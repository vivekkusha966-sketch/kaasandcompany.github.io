# kaasandcompany.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Kaas and Company Accountants</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      padding: 0;
      background: linear-gradient(to right, #1abc9c, #3498db);
      color: #333;
      overflow-x: hidden;
    }
    header, footer {
      background: rgba(44, 62, 80, 0.9);
      color: white;
      padding: 20px;
      text-align: center;
    }
    nav {
      background: rgba(52, 73, 94, 0.9);
      padding: 10px;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 1000;
    }
    nav a {
      color: white;
      margin: 0 15px;
      text-decoration: none;
      font-weight: bold;
      transition: color 0.3s ease;
    }
    nav a:hover {
      color: #f1c40f;
    }
    section {
      padding: 40px 20px;
      background: rgba(255, 255, 255, 0.9);
      margin: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    ul { list-style: none; padding: 0; }
    li { margin-bottom: 10px; }
    form input, form textarea, form select {
      width: 100%;
      padding: 10px;
      margin: 5px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    form input[type="submit"], button {
      background: #2c3e50;
      color: white;
      border: none;
      cursor: pointer;
      padding: 10px 20px;
      margin-top: 10px;
      transition: background 0.3s ease;
    }
    form input[type="submit"]:hover, button:hover {
      background: #1abc9c;
    }
    iframe {
      width: 100%;
      height: 300px;
      border: none;
    }
    .stats {
      display: flex;
      justify-content: space-around;
      background: #ecf0f1;
      padding: 20px;
      font-size: 1.5em;
      border-radius: 8px;
    }
    .stat {
      text-align: center;
    }
    #submittedReviews div {
      background: #fff;
      padding: 10px;
      margin-top: 10px;
      border-left: 4px solid #2c3e50;
    }
  </style>
</head>
<body>

<header>
  <h1>Kaas and Company Accountants</h1>
  <p>Your Trusted Chartered Accountants in Madhya Pradesh</p>
</header>

<nav>
  <a href="#about">About</a>
  <a href="#services">Services</a>
  <a href="#stats">Stats</a>
  <a href="#chart">Chart</a>
  <a href="#reviews">Reviews</a>
  <a href="#resources">Resources</a>
  <a href="#contact">Contact</a>
  <a href="#location">Location</a>
</nav>

<section id="about">
  <h2>About Us</h2>
  <p>Kaas and Company is a professional Chartered Accountant firm based in Madhya Pradesh, India. With over 15 years of experience, we specialize in tax consultancy, auditing, financial planning, and business registration services.</p>
</section>

<section id="stats" class="stats">
  <div class="stat"><span id="clients">0</span><br>Clients Served</div>
  <div class="stat"><span id="years">0</span><br>Years of Experience</div>
  <div class="stat"><span id="projects">0</span><br>Projects Completed</div>
</section>

<section id="updateCounters">
  <h2>Update Firm Stats</h2>
  <form id="counterForm">
    <label>Clients Served:</label>
    <input type="number" id="clientsInput" value="250"><br>
    <label>Years of Experience:</label>
    <input type="number" id="yearsInput" value="15"><br>
    <label>Projects Completed:</label>
    <input type="number" id="projectsInput" value="120"><br>
    <button type="submit">Update Counters</button>
  </form>
</section>

<section id="chart">
  <h2>Service Demand Overview</h2>
  <canvas id="financeChart" width="400" height="200"></canvas>
  <form id="chartForm">
    <label>Tax:</label>
    <input type="number" id="taxInput" value="65"><br>
    <label>Audit:</label>
    <input type="number" id="auditInput" value="59"><br>
    <label>GST:</label>
    <input type="number" id="gstInput" value="80"><br>
    <label>Startup:</label>
    <input type="number" id="startupInput" value="81"><br>
    <button type="submit">Update Chart</button>
  </form>
</section>

<section id="reviews">
  <h2>Rate & Review Us</h2>
  <form id="reviewForm">
    <label for="rating">Your Rating:</label>
    <select id="rating" required>
      <option value="">Select</option>
      <option value="5">★★★★★</option>
      <option value="4">★★★★☆</option>
      <option value="3">★★★☆☆</option>
      <option value="2">★★☆☆☆</option>
      <option value="1">★☆☆☆☆</option>
    </select><br>
    <label for="reviewText">Your Review:</label>
    <textarea id="reviewText" rows="4" required></textarea><br>
    <button type="submit">Submit Review</button>
  </form>
  <div id="submittedReviews">
    <h3>What People Are Saying:</h3>
  </div>
</section>

<section id="services">
  <h2>Our Services</h2>
  <ul>
    <li><i class="fas fa-file-invoice-dollar"></i> Income Tax Filing & Planning</li>
    <li><i class="fas fa-receipt"></i> GST Registration & Returns</li>
    <li><i class="fas fa-search-dollar"></i> Audit & Assurance Services</li>
    <li><i class="fas fa-building"></i> Company Incorporation & ROC Filings</li>
    <li><i class="fas fa-book"></i> Bookkeeping & Accounting</li>
    <li><i class="fas fa-chart-line"></i> Financial Advisory & Investment Planning</li>
  </ul>
</section>

<section id="resources">
  <h2>Downloadable Resources</h2>
  <ul>
    <li><a href="#">Tax Filing Checklist (PDF)</a></li>
    <li><a href="#">GST Registration Guide (PDF)</a></li>
    <li><a href="#">Company Incorporation Steps (PDF)</a></li>
  </ul>
</section>

<section id="contact">
  <h2>Contact Us</h2>
  <form action="mailto:contact@kaasaccountants.in" method="post" enctype="text/plain">
    <label>Name:</label>
    <input type="text" name="name" required>
    <label>Email:</label>
    <input type="email" name="email" required>
    <label>Message:</label>
    <textarea name="message" rows="5" required></textarea>
    <input type="submit" value="Send Message">
  </form>
</section>

<section id="location">
  <h2>Our Location</h2>
  <p>Kaas and Company Accountants<br>
     2nd Floor, Shree Business Tower,<br>
     Near Sanwer Road, Indore, Madhya Pradesh – 452010</p>
  <iframe src="https://www.google.com/maps/embed?pb=!1m18!..." allowfullscreen="" loading="lazy"></iframe>
</section>

<footer>
  <p>&copy; 2025 Kaas and Company Accountants. All rights reserved.</p>
</footer>

<!-- Scripts -->
<script>
  // Scroll animation
  const sections = document.querySelectorAll("section");
 

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Kaas and Company Accountants</title>

  <!-- Animate.css for quick keyframe effects -->
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
  />

  <!-- AOS for scroll animations -->
  <link
    rel="stylesheet"
    href="https://unpkg.com/aos@next/dist/aos.css"
  />

  <!-- Font Awesome -->
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css"
  />

  <style>
    /* Theme variables */
    :root {
      --primary: #1abc9c;
      --secondary: #3498db;
      --accent1: #9b59b6;
      --accent2: #e67e22;
      --dark: #2c3e50;
      --light: #ecf0f1;
    }

    /* Global reset & smooth scroll */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Segoe UI', Tahoma, sans-serif;
      background: var(--light);
      color: var(--dark);
      overflow-x: hidden;
    }

    a {
      text-decoration: none;
      color: inherit;
    }

    button {
      cursor: pointer;
      border: none;
      background: var(--primary);
      color: #fff;
      padding: 0.6em 1.2em;
      border-radius: 4px;
      transition: background 0.3s;
    }
    button:hover {
      background: var(--accent2);
    }

    /* Preloader */
    #preloader {
      position: fixed;
      inset: 0;
      background: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 9999;
    }
    #preloader .loader {
      width: 40px;
      height: 40px;
      border: 4px solid var(--primary);
      border-top: 4px solid var(--secondary);
      border-radius: 50%;
      animation: spin 1s linear infinite;
    }
    @keyframes spin {
      to { transform: rotate(360deg); }
    }

    /* Sticky glass nav */
    nav {
      position: sticky;
      top: 0;
      width: 100%;
      background: rgba(255,255,255,0.8);
      backdrop-filter: blur(6px);
      padding: 0.8em 1.5em;
      z-index: 100;
      display: flex;
      justify-content: center;
      gap: 1.5em;
    }
    nav a {
      position: relative;
      font-weight: 500;
      padding: 0.5em;
      transition: color 0.3s;
    }
    nav a:hover {
      color: var(--accent2);
    }
    nav a::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 50%;
      width: 0;
      height: 2px;
      background: var(--accent2);
      transition: width 0.3s, left 0.3s;
    }
    nav a:hover::after {
      width: 100%;
      left: 0;
    }

    /* Header with parallax overlay */
    header {
      position: relative;
      min-height: 80vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      color: #fff;
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      overflow: hidden;
    }
    header::before {
      content: '';
      position: absolute;
      inset: 0;
      background: url('https://images.pexels.com/photos/29585/pexels-photo.jpg') center/cover no-repeat;
      opacity: 0.2;
      transform: translateY(-20%);
      animation: parallax 20s linear infinite alternate;
    }
    @keyframes parallax {
      to { transform: translateY(20%); }
    }
    header h1 {
      font-size: 3rem;
      margin-bottom: 0.5rem;
      animation: pulse 2s infinite;
    }
    header p {
      font-size: 1.2rem;
      margin-bottom: 1.5rem;
    }
    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50%     { transform: scale(1.05); }
    }

    /* Section styling */
    section {
      padding: 4em 1.5em;
      max-width: 1000px;
      margin: auto;
    }
    section h2 {
      text-align: center;
      margin-bottom: 1em;
      font-size: 2rem;
      color: var(--dark);
    }
    section p {
      line-height: 1.6;
      margin-bottom: 1.2em;
    }

    /* Stats grid */
    .stats {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px,1fr));
      gap: 2em;
      text-align: center;
    }
    .stat {
      background: #fff;
      padding: 2em 1em;
      border-radius: 8px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.05);
      transition: transform 0.3s;
    }
    .stat:hover {
      transform: translateY(-5px);
    }
    .stat span {
      font-size: 2.5rem;
      display: block;
      color: var(--accent1);
      margin-bottom: 0.5em;
    }

    /* Form styling inside stats/chart */
    form {
      margin-top: 1.5em;
      background: #fff;
      padding: 1.5em;
      border-radius: 8px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.05);
    }
    form label {
      display: block;
      margin-top: 0.8em;
    }
    form input, form select, form textarea {
      width: 100%;
      padding: 0.6em;
      margin-top: 0.3em;
      border: 1px solid #ccc;
      border-radius: 4px;
    }

    /* Chart canvas */
    #financeChart {
      max-width: 100%;
      margin: auto;
    }

    /* Review list */
    .review {
      background: #fff;
      padding: 1em;
      margin-top: 0.8em;
      border-left: 5px solid var(--primary);
      border-radius: 4px;
    }

    /* Footer */
    footer {
      text-align: center;
      padding: 2em 1em;
      background: var(--dark);
      color: #fff;
      margin-top: 2em;
    }

    /* Scroll-to-top button */
    #scrollTopButton {
      position: fixed;
      bottom: 30px;
      right: 30px;
      background: var(--accent2);
      color: #fff;
      padding: 0.8em;
      border-radius: 50%;
      font-size: 1.2rem;
      display: none;
      z-index: 200;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
      transition: background 0.3s;
    }
    #scrollTopButton:hover {
      background: var(--accent1);
    }
  </style>
</head>
<body>

  <!-- Preloader -->
  <div id="preloader">
    <div class="loader"></div>
  </div>

  <!-- Header -->
  <header data-aos="fade-down">
    <h1>Kaas and Company Accountants</h1>
    <p>Your Trusted Chartered Accountants in Madhya Pradesh</p>
  </header>

  <!-- Navigation -->
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

  <!-- About -->
  <section id="about" data-aos="fade-up">
    <h2>About Us</h2>
    <p>Kaas and Company is a professional Chartered Accountant firm based in Madhya Pradesh, India. With over 15 years of experience, we specialize in tax consultancy, auditing, financial planning, and business registration services.</p>
  </section>

  <!-- Services -->
  <section id="services" data-aos="fade-up">
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

  <!-- Stats -->
  <section id="stats" class="stats" data-aos="fade-up">
    <div class="stat" data-tilt>
      <span id="clients">0</span>
      Clients Served
    </div>
    <div class="stat" data-tilt>
      <span id="years">0</span>
      Years of Experience
    </div>
    <div class="stat" data-tilt>
      <span id="projects">0</span>
      Projects Completed
    </div>

    <form id="counterForm">
      <label>Clients Served:</label>
      <input type="number" id="clientsInput" value="250" placeholder="Enter new clients served" />

      <label>Years of Experience:</label>
      <input type="number" id="yearsInput" value="15" placeholder="Enter new years of experience" />

      <label>Projects Completed:</label>
      <input type="number" id="projectsInput" value="120" placeholder="Enter new projects completed" />

      <button type="submit">Update Counters</button>
    </form>
  </section>

  <!-- Chart -->
  <section id="chart" data-aos="fade-left">
    <h2>Service Demand Overview</h2>
    <canvas id="financeChart" width="400" height="200"></canvas>

    <form id="chartForm">
      <label>Tax:</label>
      <input type="number" id="taxInput" value="65" placeholder="Enter new tax service demand" />

      <label>Audit:</label>
      <input type="number" id="auditInput" value="59" placeholder="Enter new audit service demand" />

      <label>GST:</label>
      <input type="number" id="gstInput" value="80" placeholder="Enter new GST service demand" />

      <label>Startup:</label>
      <input type="number" id="startupInput" value="81" placeholder="Enter new startup service demand" />

      <button type="submit">Update Chart</button>
    </form>
  </section>

  <!-- Reviews -->
  <section id="reviews" data-aos="fade-up">
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
      </select>

      <label for="reviewText">Your Review:</label>
      <textarea id="reviewText" rows="4" required placeholder="Share your experience with us"></textarea>

      <button type="submit">Submit Review</button>
    </form>

    <h3>What People Are Saying:</h3>
    <div id="submittedReviews"></div>
  </section>

  <!-- Resources -->
  <section id="resources" data-aos="fade-up">
    <h2>Useful Resources</h2>
    <ul>
      <li><a href="#">Tax Filing Checklist (PDF)</a></li>
      <li><a href="#">GST Registration Guide (PDF)</a></li>
      <li><a href="#">Company Incorporation Steps (PDF)</a></li>
    </ul>
  </section>

  <!-- Contact -->
  <section id="contact" data-aos="fade-down">
    <h2>Contact Us</h2>
    <form action="mailto:contact@kaasaccountants.in" method="post" enctype="text/plain">
      <label>Name:</label>
      <input type="text" name="name" required />

      <label>Email:</label>
      <input type="email" name="email" required />

      <label>Message:</label>
      <textarea name="message" rows="5" required></textarea>

      <input type="submit" value="Send Message" />
    </form>
  </section>

  <!-- Location -->
  <section id="location" data-aos="fade-up">
    <h2>Find Us</h2>
    <p>
      Kaas and Company Accountants<br />
      2nd Floor, Shree Business Tower,<br />
      Near Sanwer Road, Indore, Madhya Pradesh – 452010
    </p>
    <iframe
      src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3956.684025610352!2d75.88934893591082!3d22.720408543010496!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x398f0f0f0f0f0f0f%3A0xccfccfccfccfccfcc!2sShree%20Business%20Tower%2C%20Sanwer%20Road%2C%20Indore%2C%20Madhya%20Pradesh%20452010!5e0!3m2!1sen!2sin!4v1684030156335!5m2!1sen!2sin"
      width="100%"
      height="300"
      style="border:0;"
      allowfullscreen=""
      loading="lazy"
    ></iframe>
  </section>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025 Kaas and Company Accountants. All rights reserved.</p>
  </footer>

  <!-- Scroll to Top -->
  <a id="scrollTopButton" href="#"><i class="fas fa-angle-up"></i></a>

  <!-- Libraries -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js"></script>
  <script src="https://unpkg.com/vanilla-tilt@1.7.0/dist/vanilla-tilt.min.js"></script>
  <script src="https://unpkg.com/aos@next/dist/aos.js"></script>

  <!-- Core JS -->
  <script>
    // Hide preloader
    window.addEventListener('load', () => {
      document.getElementById('preloader').style.display = 'none';
    });

    // Init AOS
    AOS.init({ duration: 1000, once: true });

    // Scroll-to-top
    const scrollBtn = document.getElementById('scrollTopButton');
    window.addEventListener('scroll', () => {
      if (window.scrollY > 300) scrollBtn.style.display = 'block';
      else scrollBtn.style.display = 'none';
    });
    scrollBtn.addEventListener('click', (e) => {
      e.preventDefault();
      window.scrollTo({ top: 0, behavior: 'smooth' });
    });

    // Scroll fade in
    const sections = document.querySelectorAll('section');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting)
          entry.target.classList.add('animate__animated', 'animate__fadeInUp');
      });
    }, { threshold: 0.1 });
    sections.forEach((sec) => observer.observe(sec));

    // Counter Animation
    function animateCounter(id, endValue) {
      const el = document.getElementById(id);
      let value = 0,
          increment = endValue / 60;
      const interval = setInterval(() => {
        value += increment;
        el.textContent = Math.floor(value);
        if (value >= endValue) {
          clearInterval(interval);
          el.textContent = endValue;
        }
      }, 30);
    }
    animateCounter('clients', 250);
    animateCounter('years', 15);
    animateCounter('projects', 120);

    // Chart.js Animation
    const ctx = document.getElementById('financeChart').getContext('2d');
    let financeChart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: ['Tax', 'Audit', 'GST', 'Startup'],
        datasets: [{
          label: 'Service Demand',
          data: [65, 59, 80, 81],
          backgroundColor: [
            varStyle('--primary'),
            varStyle('--secondary'),
            varStyle('--accent1'),
            varStyle('--accent2')
          ]
        }]
      },
      options: {
        animation: {
          duration: 1200,
          easing: 'easeOutBounce'
        },
        scales: {
          y: { beginAtZero: true }
        }
      }
    });

    // Helper to read CSS variables
    function varStyle(name) {
      return getComputedStyle(document.documentElement).getPropertyValue(name);
    }

    // Update counters from form
    document.getElementById('counterForm').addEventListener('submit', (e) => {
      e.preventDefault();
      animateCounter(
        'clients',
        parseInt(document.getElementById('clientsInput').value, 10)
      );
      animateCounter(
        'years',
        parseInt(document.getElementById('yearsInput').value, 10)
      );
      animateCounter(
        'projects',
        parseInt(document.getElementById('projectsInput').value, 10)
      );
    });

    // Update chart from form
    document.getElementById('chartForm').addEventListener('submit', (e) => {
      e.preventDefault();
      financeChart.data.datasets[0].data = [
        parseInt(document.getElementById('taxInput').value, 10),
        parseInt(document.getElementById('auditInput').value, 10),
        parseInt(document.getElementById('gstInput').value, 10),
        parseInt(document.getElementById('startupInput').value, 10)
      ];
      financeChart.update();
    });

    // Tilt effect
    VanillaTilt.init(document.querySelectorAll('.stat'), {
      max: 10,
      speed: 400,
      glare: true,
      'max-glare': 0.2
    });

    // Reviews
    document.getElementById('reviewForm').addEventListener('submit', (e) => {
      e.preventDefault();
      const reviewText = document.getElementById('reviewText').value;
      const reviewRating = document.getElementById('rating').value;
      const div = document.createElement('div');
      div.className = 'review animate__animated animate__fadeIn';
      const color = {
        '5': '#f1c40f',
        '4': '#f39c12',
        '3': '#f1c40f',
        '2': '#e67e22',
        '1': '#e74c3c'
      }[reviewRating] || '#333';
      div.innerHTML = `<strong style="color:${color}">${'★'.repeat(reviewRating)}</strong> – ${reviewText}`;
      document.getElementById('submittedReviews').append(div);
      document.getElementById('reviewForm').reset();
    });
  </script>

</body>
</html>

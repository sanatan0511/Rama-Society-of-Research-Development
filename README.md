<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ramanujan Society of Research</title>
  <style>
    /* Reset CSS */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Arial', sans-serif;
      color: #333;
      scroll-behavior: smooth;
    }

    /* Full-Screen Hero Section with Logo and Background Image */
    .hero-section {
      height: 100vh; /* Full viewport height */
      background: url('https://exoplanets.nasa.gov/internal_resources/698/') no-repeat center center/cover;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      text-align: center;
      color: #fff;
      position: relative;
    }

    .hero-section img {
      max-width: 80%;
      max-height: 80%;
      height: auto;
      width: auto;
    }

    .hero-section h1 {
      font-size: 3rem; /* Bigger title font */
      margin-top: 20px;
      background: rgba(0, 0, 0, 0.6); /* Add a translucent background for better readability */
      padding: 10px 20px;
      border-radius: 5px;
    }

    .hero-section .scroll-down {
      position: absolute;
      bottom: 20px;
      font-size: 1.5rem; /* Larger scroll-down text */
      color: #fff;
      cursor: pointer;
      animation: bounce 2s infinite;
    }

    @keyframes bounce {
      0%, 100% {
        transform: translateY(0);
      }
      50% {
        transform: translateY(10px);
      }
    }

    /* Navigation Bar */
    nav {
      background-color: rgba(123, 29, 29, 0.9); /* Semi-transparent maroon */
      color: #fff;
      padding: 10px 20px;
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    nav .logo {
      display: flex;
      align-items: center;
    }

    nav .logo img {
      max-height: 50px;
      width: auto;
    }

    nav ul {
      list-style: none;
      display: flex;
    }

    nav ul li {
      margin: 0 15px;
    }

    nav ul li a {
      text-decoration: none;
      color: #fff;
      font-weight: bold;
      transition: color 0.3s ease;
    }

    nav ul li a:hover {
      color: #ffd700; /* Gold */
    }

    /* Second Page Section (Admin Login Option) */
    .second-page {
      background: #f5f5f5;
      padding: 100px 20px; /* Larger padding to give more space */
      text-align: center;
    }

    .second-page h2 {
      font-size: 3rem; /* Larger header */
      color: #7b1d1d;
      margin-bottom: 30px;
    }

    .second-page p {
      line-height: 1.8;
      font-size: 1.2rem; /* Larger text for better readability */
      margin-bottom: 30px;
      max-width: 900px;
      margin: auto;
    }

    .second-page img {
      max-width: 90%;
      height: auto;
      margin-top: 20px;
    }

    /* Account Link */
    .admin-link {
      display: block;
      margin-top: 30px;
      font-size: 1.2rem;
      color: #7b1d1d;
      text-decoration: none;
    }

    .admin-link:hover {
      color: #ffd700;
    }

    /* Footer */
    footer {
      background-color: #7b1d1d;
      color: #fff;
      text-align: center;
      padding: 10px;
    }

    footer a {
      color: #ffd700;
      text-decoration: none;
    }

  </style>
</head>
<body>
  <!-- Full-Screen Hero Section -->
  <div class="hero-section">
    <img src="https://i.ibb.co/dmZZ961/Subheading-2.png" alt="Rama Society of Research & Development(RSRD)">
    <h1>Rama Society of Research & Development(RSRD)</h1>
    <a href="#menu" class="scroll-down">Scroll Down ↓</a>
  </div>

  <!-- Navigation Bar -->
  <nav id="menu">
    <div class="logo">
      <img src="logo.png" alt="Rama Society of Research & Development(RSRD)">
      <span>Rama Society of Research & Development(RSRD)</span>
    </div>
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">Blog</a></li>
      <li><a href="#">Research Summit</a></li>
      <li><a href="#">Events</a></li>
      <li><a href="admin_login.html">Admin Login</a></li> <!-- Updated to link to a separate login page -->
      <li><a href="#">Contact Us</a></li>
    </ul>
  </nav>

  <!-- Second Page Section (Admin Login Option) -->
  <section class="second-page">
    <h2>Explore Our Research</h2>
    <p>
      Our society is dedicated to advancing research in science and mathematics. Through collaborations and mentorships, we aim to cultivate a research-oriented mindset in students. Join us in our journey of discovery and innovation.
    </p>
    <img src="https://im.indiatimes.in/content/2019/Jul/isro_history_1563885126.jpg?w=640&h=427&cc=1&webp=1&q=75" alt="Research Image">
    <a href="admin_login.html" class="admin-link">Click here to log in as Admin</a>
  </section>

  <!-- Footer -->
  <footer>
    <p>&copy; 2024 Rama Society of Research & Development(RSRD). All rights reserved.</p>
  </footer>
</body>
</html>

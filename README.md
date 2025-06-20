
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Admin Login - Ramanujan Society of Research</title>
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
      background-color: #f5f5f5;
    }

    /* Admin Login Page */
    .login-page {
      padding: 60px 20px;
      text-align: center;
      background-color: #f5f5f5;
    }

    .welcome-message {
      font-size: 1.5rem;
      margin-bottom: 20px;
      color: #7b1d1d;
    }

    .welcome-message span {
      font-weight: bold;
      color: #333;
    }

    .login-page h2 {
      font-size: 2rem;
      margin-bottom: 30px;
      color: #7b1d1d;
    }

    .login-page form {
      display: flex;
      flex-direction: column;
      align-items: center;
      max-width: 400px;
      margin: 0 auto;
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
    }

    .login-page input {
      padding: 12px;
      margin: 12px 0;
      width: 100%;
      max-width: 300px;
      font-size: 1rem;
      border-radius: 8px;
      border: 1px solid #ccc;
      transition: all 0.3s ease;
    }

    .login-page input:focus {
      border-color: #7b1d1d;
      outline: none;
    }

    .login-page button {
      padding: 12px 20px;
      font-size: 1.2rem;
      background-color: #7b1d1d;
      color: #fff;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .login-page button:hover {
      background-color: #ffd700;
    }

    .datetime {
      font-size: 1.2rem;
      color: #333;
      margin-top: 20px;
      font-style: italic;
    }
  </style>

  <!-- Include Google reCAPTCHA Script -->
  <script src="https://www.google.com/recaptcha/api.js" async defer></script>
</head>
<body>
  <!-- Admin Login Form -->
  <div class="login-page">
    <div class="welcome-message">
      <p>Welcome <span>Admin</span>!</p>
      <p id="datetime"></p> <!-- This will display the current date and time -->
    </div>
    <h2>Admin Login</h2>
    <form id="loginForm" onsubmit="return false;"> <!-- Prevent form submission to handle via JS -->
      <input type="text" id="username" placeholder="Enter Username" required>
      <input type="password" id="password" placeholder="Enter Password" required>

      <!-- reCAPTCHA Widget -->
      <div class="g-recaptcha" data-sitekey="6LdAVZcqAAAAAHoKIcFfs9RgZHrfx0K5_tbdGJ3U"></div>

      <button type="button" onclick="validateLogin()">Login</button> <!-- Use type="button" to prevent form submission -->
    </form>
  </div>

  <script>
    // JavaScript to validate login credentials securely
    let failedAttempts = 0;

    function validateLogin() {
      // Prevent login after 3 failed attempts
      if (failedAttempts >= 3) {
        alert("Too many failed attempts. Please try again later.");
        return;
      }

      // Predefined credentials (Normally, this data would be fetched from a server)
      const correctUsername = 'SiyaRam';
      const correctPassword = 'Lab123@';  // Correct password for validation

      // Get the input values
      const enteredUsername = document.getElementById('username').value;
      const enteredPassword = document.getElementById('password').value;

      // Get the reCAPTCHA response token
      const recaptchaResponse = grecaptcha.getResponse();

      // Check if reCAPTCHA is filled
      if (recaptchaResponse.length === 0) {
        alert('Please verify that you are not a robot.');
        return;
      }

      // Check if entered credentials match predefined ones
      if (enteredUsername === correctUsername && enteredPassword === correctPassword) {
        // If login is successful, redirect to first-page.html
        console.log("Login successful. Redirecting...");

        // Optional: Store login status in sessionStorage
        sessionStorage.setItem("loggedIn", true);

        // Redirect to first-page.html
        window.location.href = 'first-page.html';
      } else {
        // If login fails, show an error message and increase failed attempts counter
        failedAttempts++;
        alert('Invalid username or password');
        console.log("Login failed. Attempt number: " + failedAttempts);
      }
    }

    // JavaScript to show current date and time
    function updateDateTime() {
      const dateTimeElement = document.getElementById('datetime');
      const now = new Date();
      const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric', hour: '2-digit', minute: '2-digit', second: '2-digit' };
      const formattedDate = now.toLocaleDateString('en-US', options);
      dateTimeElement.textContent = `Current Date and Time: ${formattedDate}`;
    }

    // Call the function to update date and time every second
    setInterval(updateDateTime, 1000);
  </script>
</body>
</html>

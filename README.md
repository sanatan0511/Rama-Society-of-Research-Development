<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Secure Login - SiyaRam AI Lab</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary-color: #4a6fa5;
      --secondary-color: #166088;
      --accent-color: #4fc3f7;
      --error-color: #e53935;
      --success-color: #43a047;
      --dark-color: #0a192f;
      --light-color: #f8f9fa;
      --gradient-start: #1e3c72;
      --gradient-end: #2a5298;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
      color: var(--light-color);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .container {
      width: 100%;
      max-width: 1200px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 30px;
      background-color: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
    }

    .hero-section {
      padding: 40px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      background: url('https://images.unsplash.com/photo-1620712943543-bcc4688e7485?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80') no-repeat center center;
      background-size: cover;
      position: relative;
    }

    .hero-section::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(to right, rgba(26, 32, 44, 0.8), rgba(26, 32, 44, 0.5));
    }

    .hero-content {
      position: relative;
      z-index: 1;
    }

    .logo {
      display: flex;
      align-items: center;
      margin-bottom: 30px;
    }

    .logo img {
      width: 50px;
      height: 50px;
      margin-right: 15px;
    }

    .logo-text {
      font-size: 24px;
      font-weight: 700;
      color: var(--light-color);
    }

    .hero-title {
      font-size: 2.5rem;
      font-weight: 700;
      margin-bottom: 20px;
      line-height: 1.2;
    }

    .hero-subtitle {
      font-size: 1.1rem;
      margin-bottom: 30px;
      opacity: 0.9;
    }

    .features {
      margin-top: 40px;
    }

    .feature-item {
      display: flex;
      align-items: center;
      margin-bottom: 15px;
    }

    .feature-icon {
      width: 40px;
      height: 40px;
      background-color: var(--accent-color);
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 15px;
      color: var(--dark-color);
    }

    .login-section {
      padding: 50px;
      background-color: rgba(255, 255, 255, 0.95);
      color: var(--dark-color);
    }

    .login-header {
      text-align: center;
      margin-bottom: 40px;
    }

    .login-title {
      font-size: 2rem;
      font-weight: 700;
      color: var(--primary-color);
      margin-bottom: 10px;
    }

    .login-subtitle {
      color: #666;
      font-size: 0.9rem;
    }

    .login-form {
      display: flex;
      flex-direction: column;
    }

    .form-group {
      margin-bottom: 20px;
      position: relative;
    }

    .form-label {
      display: block;
      margin-bottom: 8px;
      font-weight: 500;
      color: #555;
    }

    .form-input {
      width: 100%;
      padding: 15px 15px 15px 45px;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 1rem;
      transition: all 0.3s;
      background-color: #f9f9f9;
    }

    .form-input:focus {
      border-color: var(--accent-color);
      box-shadow: 0 0 0 3px rgba(79, 195, 247, 0.2);
      outline: none;
      background-color: #fff;
    }

    .input-icon {
      position: absolute;
      left: 15px;
      top: 40px;
      color: #777;
    }

    .password-toggle {
      position: absolute;
      right: 15px;
      top: 40px;
      cursor: pointer;
      color: #777;
    }

    .remember-forgot {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .remember-me {
      display: flex;
      align-items: center;
    }

    .remember-me input {
      margin-right: 8px;
    }

    .forgot-password {
      color: var(--primary-color);
      text-decoration: none;
      font-size: 0.9rem;
      cursor: pointer;
    }

    .forgot-password:hover {
      text-decoration: underline;
    }

    .login-btn {
      background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
      color: white;
      border: none;
      padding: 15px;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.3s;
      margin-bottom: 20px;
    }

    .login-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }

    .divider {
      display: flex;
      align-items: center;
      margin: 20px 0;
    }

    .divider::before, .divider::after {
      content: "";
      flex: 1;
      border-bottom: 1px solid #ddd;
    }

    .divider-text {
      padding: 0 15px;
      color: #777;
      font-size: 0.9rem;
    }

    .social-login {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-bottom: 25px;
    }

    .social-btn {
      width: 45px;
      height: 45px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #f5f5f5;
      color: #555;
      border: none;
      cursor: pointer;
      transition: all 0.3s;
    }

    .social-btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }

    .register-link {
      text-align: center;
      font-size: 0.9rem;
      color: #666;
    }

    .register-link a {
      color: var(--primary-color);
      text-decoration: none;
      font-weight: 500;
    }

    .register-link a:hover {
      text-decoration: underline;
    }

    .security-info {
      margin-top: 30px;
      padding: 15px;
      background-color: #f0f7ff;
      border-radius: 8px;
      font-size: 0.8rem;
      color: #555;
      display: flex;
      align-items: center;
    }

    .security-info i {
      margin-right: 10px;
      color: var(--primary-color);
    }

    /* Modal styles */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.7);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }

    .modal-content {
      background-color: white;
      padding: 30px;
      border-radius: 10px;
      width: 90%;
      max-width: 500px;
      box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
      position: relative;
      animation: modalFadeIn 0.3s;
    }

    @keyframes modalFadeIn {
      from {
        opacity: 0;
        transform: translateY(-20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .close-modal {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: 1.5rem;
      cursor: pointer;
      color: #777;
    }

    .modal-title {
      font-size: 1.5rem;
      margin-bottom: 20px;
      color: var(--primary-color);
    }

    .reset-steps {
      margin-bottom: 20px;
      font-size: 0.9rem;
      color: #555;
    }

    .step {
      display: none;
    }

    .step.active {
      display: block;
    }

    .step-title {
      font-weight: 600;
      margin-bottom: 15px;
      color: var(--secondary-color);
    }

    .next-btn, .submit-btn {
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: 6px;
      cursor: pointer;
      margin-top: 15px;
      font-weight: 500;
      transition: all 0.3s;
    }

    .next-btn:hover, .submit-btn:hover {
      background-color: var(--secondary-color);
    }

    /* 2FA styles */
    .two-factor-auth {
      margin-top: 20px;
      padding: 20px;
      background-color: #f5f5f5;
      border-radius: 8px;
      display: none;
    }

    .auth-code-inputs {
      display: flex;
      justify-content: space-between;
      margin: 20px 0;
    }

    .auth-code-inputs input {
      width: 50px;
      height: 50px;
      text-align: center;
      font-size: 1.5rem;
      border: 1px solid #ddd;
      border-radius: 5px;
    }

    /* Responsive styles */
    @media (max-width: 992px) {
      .container {
        grid-template-columns: 1fr;
      }
      
      .hero-section {
        display: none;
      }
    }

    @media (max-width: 576px) {
      .login-section {
        padding: 30px 20px;
      }
      
      .login-title {
        font-size: 1.5rem;
      }
    }

    /* Animation */
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      10%, 30%, 50%, 70%, 90% { transform: translateX(-5px); }
      20%, 40%, 60%, 80% { transform: translateX(5px); }
    }

    .shake {
      animation: shake 0.5s;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="hero-section">
      <div class="hero-content">
        <div class="logo">
          <i class="fas fa-flask" style="font-size: 2rem; color: var(--accent-color); margin-right: 10px;"></i>
          <div class="logo-text">SiyaRam AI Lab</div>
        </div>
        <h1 class="hero-title">Advanced Research Laboratory Portal</h1>
        <p class="hero-subtitle">Secure access to our cutting-edge AI research platform and laboratory management system.</p>
        
        <div class="features">
          <div class="feature-item">
            <div class="feature-icon">
              <i class="fas fa-shield-alt"></i>
            </div>
            <div>Multi-layer security with 2FA and biometric options</div>
          </div>
          <div class="feature-item">
            <div class="feature-icon">
              <i class="fas fa-brain"></i>
            </div>
            <div>Access to advanced AI research tools</div>
          </div>
          <div class="feature-item">
            <div class="feature-icon">
              <i class="fas fa-chart-line"></i>
            </div>
            <div>Real-time laboratory data analytics</div>
          </div>
        </div>
      </div>
    </div>

    <div class="login-section">
      <div class="login-header">
        <h2 class="login-title">Secure Login</h2>
        <p class="login-subtitle">Enter your credentials to access the SiyaRam Lab portal</p>
      </div>

      <form id="loginForm" class="login-form">
        <div class="form-group">
          <label for="username" class="form-label">Username</label>
          <i class="fas fa-user input-icon"></i>
          <input type="text" id="username" class="form-input" placeholder="Enter your username" required>
        </div>

        <div class="form-group">
          <label for="password" class="form-label">Password</label>
          <i class="fas fa-lock input-icon"></i>
          <input type="password" id="password" class="form-input" placeholder="Enter your password" required>
          <i class="fas fa-eye password-toggle" id="togglePassword"></i>
        </div>

        <div class="remember-forgot">
          <div class="remember-me">
            <input type="checkbox" id="remember">
            <label for="remember">Remember me</label>
          </div>
          <a class="forgot-password" id="forgotPassword">Forgot password?</a>
        </div>

        <button type="submit" class="login-btn">Login</button>

        <div class="divider">
          <span class="divider-text">OR</span>
        </div>

        <div class="social-login">
          <button type="button" class="social-btn">
            <i class="fab fa-google"></i>
          </button>
          <button type="button" class="social-btn">
            <i class="fab fa-microsoft"></i>
          </button>
          <button type="button" class="social-btn">
            <i class="fab fa-apple"></i>
          </button>
        </div>

        <div class="register-link">
          New to SiyaRam Lab? <a href="#" id="registerLink">Request access</a>
        </div>

        <div class="security-info">
          <i class="fas fa-lock"></i>
          <span>Your credentials are encrypted and protected with advanced security measures.</span>
        </div>
      </form>

      <!-- 2FA Section (hidden by default) -->
      <div id="twoFactorAuth" class="two-factor-auth">
        <h3>Two-Factor Authentication</h3>
        <p>Enter the 6-digit code sent to your registered email</p>
        <div class="auth-code-inputs">
          <input type="text" maxlength="1" pattern="[0-9]">
          <input type="text" maxlength="1" pattern="[0-9]">
          <input type="text" maxlength="1" pattern="[0-9]">
          <input type="text" maxlength="1" pattern="[0-9]">
          <input type="text" maxlength="1" pattern="[0-9]">
          <input type="text" maxlength="1" pattern="[0-9]">
        </div>
        <button id="verify2FA" class="submit-btn">Verify</button>
      </div>
    </div>
  </div>

  <!-- Forgot Password Modal -->
  <div id="forgotPasswordModal" class="modal">
    <div class="modal-content">
      <span class="close-modal">&times;</span>
      <h3 class="modal-title">Reset Your Password</h3>
      
      <div class="reset-steps">
        <div id="step1" class="step active">
          <p class="step-title">Step 1: Verify Your Identity</p>
          <p>Enter your username and the security code provided by your administrator.</p>
          <div class="form-group">
            <label for="resetUsername">Username</label>
            <input type="text" id="resetUsername" class="form-input" placeholder="Your username">
          </div>
          <div class="form-group">
            <label for="securityCode">Security Code</label>
            <input type="text" id="securityCode" class="form-input" placeholder="Enter security code">
          </div>
          <button id="nextStep1" class="next-btn">Next</button>
        </div>
        
        <div id="step2" class="step">
          <p class="step-title">Step 2: Set New Password</p>
          <p>Create a strong new password with at least 8 characters, including numbers and special characters.</p>
          <div class="form-group">
            <label for="newPassword">New Password</label>
            <input type="password" id="newPassword" class="form-input" placeholder="New password">
          </div>
          <div class="form-group">
            <label for="confirmPassword">Confirm Password</label>
            <input type="password" id="confirmPassword" class="form-input" placeholder="Confirm password">
          </div>
          <button id="submitReset" class="submit-btn">Reset Password</button>
        </div>
        
        <div id="step3" class="step">
          <p class="step-title">Password Reset Successful!</p>
          <p>Your password has been successfully updated. You can now login with your new credentials.</p>
          <button id="closeModal" class="submit-btn">Close</button>
        </div>
      </div>
    </div>
  </div>

  <script>
    // DOM Elements
    const loginForm = document.getElementById('loginForm');
    const usernameInput = document.getElementById('username');
    const passwordInput = document.getElementById('password');
    const togglePassword = document.getElementById('togglePassword');
    const forgotPasswordBtn = document.getElementById('forgotPassword');
    const registerLink = document.getElementById('registerLink');
    const modal = document.getElementById('forgotPasswordModal');
    const closeModal = document.querySelector('.close-modal');
    const nextStep1 = document.getElementById('nextStep1');
    const submitReset = document.getElementById('submitReset');
    const closeModalBtn = document.getElementById('closeModal');
    const steps = document.querySelectorAll('.step');
    const twoFactorAuth = document.getElementById('twoFactorAuth');
    const verify2FA = document.getElementById('verify2FA');
    
    // Correct credentials
    const CORRECT_USERNAME = 'SiyaRam4811';
    const CORRECT_PASSWORD = 'Lab123@';
    const RESET_CODE = '4811';
    
    // Password toggle
    togglePassword.addEventListener('click', function() {
      const type = passwordInput.getAttribute('type') === 'password' ? 'text' : 'password';
      passwordInput.setAttribute('type', type);
      this.classList.toggle('fa-eye-slash');
    });
    
    // Forgot password modal
    forgotPasswordBtn.addEventListener('click', function() {
      modal.style.display = 'flex';
    });
    
    closeModal.addEventListener('click', function() {
      modal.style.display = 'none';
    });
    
    closeModalBtn.addEventListener('click', function() {
      modal.style.display = 'none';
      resetSteps();
    });
    
    // Next step in password reset
    nextStep1.addEventListener('click', function() {
      const username = document.getElementById('resetUsername').value;
      const code = document.getElementById('securityCode').value;
      
      if (username === CORRECT_USERNAME && code === RESET_CODE) {
        document.getElementById('step1').classList.remove('active');
        document.getElementById('step2').classList.add('active');
      } else {
        alert('Invalid username or security code. Please try again.');
      }
    });
    
    // Submit password reset
    submitReset.addEventListener('click', function() {
      const newPassword = document.getElementById('newPassword').value;
      const confirmPassword = document.getElementById('confirmPassword').value;
      
      if (newPassword !== confirmPassword) {
        alert('Passwords do not match!');
        return;
      }
      
      if (newPassword.length < 8) {
        alert('Password must be at least 8 characters long!');
        return;
      }
      
      // In a real app, you would send this to your server to update the password
      console.log('Password reset to:', newPassword);
      
      document.getElementById('step2').classList.remove('active');
      document.getElementById('step3').classList.add('active');
    });
    
    // Reset steps when modal closes
    function resetSteps() {
      steps.forEach(step => {
        step.classList.remove('active');
      });
      document.getElementById('step1').classList.add('active');
      document.getElementById('resetUsername').value = '';
      document.getElementById('securityCode').value = '';
      document.getElementById('newPassword').value = '';
      document.getElementById('confirmPassword').value = '';
    }
    
    // Form submission
    loginForm.addEventListener('submit', function(e) {
      e.preventDefault();
      
      const username = usernameInput.value;
      const password = passwordInput.value;
      
      if (username === CORRECT_USERNAME && password === CORRECT_PASSWORD) {
        // Simulate 2FA (in real app, you would send a code to user's email/phone)
        twoFactorAuth.style.display = 'block';
        loginForm.style.display = 'none';
        
        // Auto-fill a demo code (in real app, user would enter the code they receive)
        const inputs = document.querySelectorAll('.auth-code-inputs input');
        inputs[0].value = '1';
        inputs[1].value = '2';
        inputs[2].value = '3';
        inputs[3].value = '4';
        inputs[4].value = '5';
        inputs[5].value = '6';
      } else {
        // Shake animation for wrong credentials
        loginForm.classList.add('shake');
        setTimeout(() => {
          loginForm.classList.remove('shake');
        }, 500);
        
        alert('Invalid username or password. Please try again.');
      }
    });
    
    // Verify 2FA code
    verify2FA.addEventListener('click', function() {
      // In a real app, you would verify the code with your server
      alert('Login successful! Redirecting to dashboard...');
      window.location.href = 'first-page.html';
    });
    
    // Register link
    registerLink.addEventListener('click', function(e) {
      e.preventDefault();
      alert('Please contact your lab administrator to request access.');
    });
    
    // Close modal when clicking outside
    window.addEventListener('click', function(e) {
      if (e.target === modal) {
        modal.style.display = 'none';
        resetSteps();
      }
    });
  </script>
</body>
</html>

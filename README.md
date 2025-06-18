<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SiyaRam AI Lab - Secure Portal</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <script src="https://www.google.com/recaptcha/enterprise.js?render=6LdAVZcqAAAAAHoKIcFfs9RgZHrfx0K5_tbdGJ3U"></script>
  <style>
    :root {
      --primary: #2563eb;
      --primary-dark: #1e40af;
      --secondary: #10b981;
      --danger: #ef4444;
      --warning: #f59e0b;
      --light: #f8fafc;
      --dark: #0f172a;
      --gray: #64748b;
      --gray-light: #e2e8f0;
      --border-radius: 10px;
      --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
      --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
      --transition: all 0.3s ease;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background-color: #f1f5f9;
      color: var(--dark);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      background-image: 
        radial-gradient(at 80% 0%, hsla(189, 100%, 56%, 0.1) 0px, transparent 50%),
        radial-gradient(at 0% 50%, hsla(355, 100%, 93%, 0.1) 0px, transparent 50%);
    }

    .login-container {
      width: 100%;
      max-width: 400px;
      background-color: white;
      border-radius: var(--border-radius);
      box-shadow: var(--shadow-lg);
      overflow: hidden;
    }

    .login-header {
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      color: white;
      padding: 30px;
      text-align: center;
    }

    .logo {
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 15px;
    }

    .logo-icon {
      font-size: 2rem;
      margin-right: 10px;
      color: white;
    }

    .logo-text {
      font-size: 1.8rem;
      font-weight: 700;
    }

    .login-title {
      font-size: 1.5rem;
      margin-bottom: 5px;
    }

    .login-subtitle {
      font-size: 0.9rem;
      opacity: 0.9;
    }

    .login-body {
      padding: 30px;
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
      font-size: 0.9rem;
    }

    .form-input {
      width: 100%;
      padding: 12px 12px 12px 40px;
      border: 1px solid var(--gray-light);
      border-radius: var(--border-radius);
      font-size: 1rem;
      transition: var(--transition);
    }

    .form-input:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.2);
      outline: none;
    }

    .input-icon {
      position: absolute;
      left: 12px;
      top: 40px;
      color: var(--gray);
    }

    .password-toggle {
      position: absolute;
      right: 12px;
      top: 40px;
      cursor: pointer;
      color: var(--gray);
    }

    .remember-forgot {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      font-size: 0.9rem;
    }

    .remember-me {
      display: flex;
      align-items: center;
    }

    .remember-me input {
      margin-right: 8px;
      accent-color: var(--primary);
    }

    .forgot-password {
      color: var(--primary);
      text-decoration: none;
      font-weight: 500;
    }

    .forgot-password:hover {
      text-decoration: underline;
    }

    .recaptcha-container {
      margin: 20px 0;
      display: flex;
      justify-content: center;
    }

    .login-btn {
      background: linear-gradient(to right, var(--primary), var(--primary-dark));
      color: white;
      border: none;
      padding: 12px;
      border-radius: var(--border-radius);
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      margin-bottom: 20px;
      box-shadow: var(--shadow);
    }

    .login-btn:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow-lg);
    }

    .login-footer {
      text-align: center;
      font-size: 0.9rem;
      color: var(--gray);
    }

    .login-footer a {
      color: var(--primary);
      text-decoration: none;
      font-weight: 500;
    }

    .login-footer a:hover {
      text-decoration: underline;
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
      border-radius: var(--border-radius);
      width: 90%;
      max-width: 400px;
      box-shadow: var(--shadow-lg);
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
      color: var(--gray);
    }

    .modal-title {
      font-size: 1.3rem;
      margin-bottom: 15px;
      color: var(--primary-dark);
    }

    .modal-text {
      margin-bottom: 20px;
      color: var(--gray);
      font-size: 0.9rem;
    }

    .code-inputs {
      display: flex;
      justify-content: space-between;
      margin: 20px 0;
    }

    .code-input {
      width: 50px;
      height: 50px;
      text-align: center;
      font-size: 1.2rem;
      border: 1px solid var(--gray-light);
      border-radius: 5px;
    }

    .code-input:focus {
      border-color: var(--primary);
      outline: none;
    }

    .modal-btn {
      width: 100%;
      padding: 12px;
      border-radius: var(--border-radius);
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      margin-top: 10px;
      border: none;
    }

    .btn-primary {
      background-color: var(--primary);
      color: white;
    }

    .btn-primary:hover {
      background-color: var(--primary-dark);
    }

    .btn-secondary {
      background-color: transparent;
      color: var(--primary);
      border: 1px solid var(--primary);
    }

    .btn-secondary:hover {
      background-color: rgba(37, 99, 235, 0.1);
    }

    .resend-code {
      text-align: center;
      margin-top: 15px;
      font-size: 0.9rem;
    }

    .resend-code a {
      color: var(--primary);
      text-decoration: none;
      font-weight: 500;
    }

    .resend-code a:hover {
      text-decoration: underline;
    }

    /* Error message */
    .error-message {
      color: var(--danger);
      font-size: 0.8rem;
      margin-top: 5px;
      display: none;
    }

    /* Loading spinner */
    .spinner {
      display: inline-block;
      width: 20px;
      height: 20px;
      border: 3px solid rgba(255, 255, 255, 0.3);
      border-radius: 50%;
      border-top-color: white;
      animation: spin 1s ease-in-out infinite;
      margin-right: 8px;
    }

    @keyframes spin {
      to { transform: rotate(360deg); }
    }

    /* Responsive styles */
    @media (max-width: 576px) {
      .login-container {
        max-width: 100%;
      }
      
      .login-header, .login-body {
        padding: 20px;
      }
      
      .code-input {
        width: 40px;
        height: 40px;
        font-size: 1rem;
      }
    }
  </style>
</head>
<body>
  <div class="login-container">
    <div class="login-header">
      <div class="logo">
        <i class="fas fa-atom logo-icon"></i>
        <div class="logo-text">SiyaRam AI Lab</div>
      </div>
      <h2 class="login-title">Secure Research Portal</h2>
      <p class="login-subtitle">Sign in to access advanced AI research tools</p>
    </div>
    
    <div class="login-body">
      <form id="loginForm" class="login-form">
        <div class="form-group">
          <label for="username" class="form-label">Username</label>
          <i class="fas fa-user input-icon"></i>
          <input type="text" id="username" class="form-input" placeholder="Enter username" required>
          <div class="error-message" id="usernameError"></div>
        </div>
        
        <div class="form-group">
          <label for="password" class="form-label">Password</label>
          <i class="fas fa-lock input-icon"></i>
          <input type="password" id="password" class="form-input" placeholder="Enter password" required>
          <i class="fas fa-eye password-toggle" id="togglePassword"></i>
          <div class="error-message" id="passwordError"></div>
        </div>
        
        <div class="remember-forgot">
          <div class="remember-me">
            <input type="checkbox" id="remember">
            <label for="remember">Remember me</label>
          </div>
          <a href="#" class="forgot-password" id="forgotPassword">Forgot password?</a>
        </div>
        
        <div class="recaptcha-container">
          <div class="g-recaptcha" data-sitekey="6LdAVZcqAAAAAHoKIcFfs9RgZHrfx0K5_tbdGJ3U"></div>
        </div>
        
        <button type="submit" class="login-btn" id="loginBtn">
          <span id="loginBtnText">Sign In</span>
        </button>
        
        <div class="login-footer">
          Need access? <a href="#" id="requestAccess">Contact administrator</a>
        </div>
      </form>
    </div>
  </div>
  
  <!-- 2FA Verification Modal -->
  <div id="twoFactorModal" class="modal">
    <div class="modal-content">
      <span class="close-modal" id="closeTwoFactor">&times;</span>
      <h3 class="modal-title">Two-Factor Authentication</h3>
      <p class="modal-text">We've sent a 6-digit verification code to <strong>sanatansingh000001@gmail.com</strong>.</p>
      
      <div class="code-inputs">
        <input type="text" class="code-input" maxlength="1" inputmode="numeric" pattern="[0-9]">
        <input type="text" class="code-input" maxlength="1" inputmode="numeric" pattern="[0-9]">
        <input type="text" class="code-input" maxlength="1" inputmode="numeric" pattern="[0-9]">
        <input type="text" class="code-input" maxlength="1" inputmode="numeric" pattern="[0-9]">
        <input type="text" class="code-input" maxlength="1" inputmode="numeric" pattern="[0-9]">
        <input type="text" class="code-input" maxlength="1" inputmode="numeric" pattern="[0-9]">
      </div>
      
      <button class="modal-btn btn-primary" id="verifyCode">Verify</button>
      <button class="modal-btn btn-secondary" id="cancelTwoFactor">Cancel</button>
      
      <div class="resend-code">
        Didn't receive code? <a href="#" id="resendCode">Resend code</a>
      </div>
    </div>
  </div>
  
  <!-- Password Reset Modal -->
  <div id="resetModal" class="modal">
    <div class="modal-content">
      <span class="close-modal" id="closeReset">&times;</span>
      <h3 class="modal-title">Reset Password</h3>
      <p class="modal-text">Enter your username and security code to reset your password.</p>
      
      <div class="form-group">
        <label for="resetUsername" class="form-label">Username</label>
        <input type="text" id="resetUsername" class="form-input" placeholder="Enter username">
        <div class="error-message" id="resetUsernameError"></div>
      </div>
      
      <div class="form-group">
        <label for="resetCode" class="form-label">Security Code</label>
        <input type="text" id="resetCode" class="form-input" placeholder="Enter security code">
        <div class="error-message" id="resetCodeError"></div>
      </div>
      
      <div class="form-group">
        <label for="newPassword" class="form-label">New Password</label>
        <input type="password" id="newPassword" class="form-input" placeholder="Enter new password">
        <div class="error-message" id="newPasswordError"></div>
      </div>
      
      <div class="form-group">
        <label for="confirmPassword" class="form-label">Confirm Password</label>
        <input type="password" id="confirmPassword" class="form-input" placeholder="Confirm new password">
        <div class="error-message" id="confirmPasswordError"></div>
      </div>
      
      <button class="modal-btn btn-primary" id="submitReset">Reset Password</button>
      <button class="modal-btn btn-secondary" id="cancelReset">Cancel</button>
    </div>
  </div>

  <script>
    // Secure credentials (in a real app, this would be server-side)
    const SECURE_CREDENTIALS = {
      username: 'SiyaRam4811',
      password: 'Lab123@',
      resetCode: '4811',
      twoFactorEmail: 'sanatansingh000001@gmail.com'
    };

    // DOM Elements
    const loginForm = document.getElementById('loginForm');
    const usernameInput = document.getElementById('username');
    const passwordInput = document.getElementById('password');
    const togglePassword = document.getElementById('togglePassword');
    const loginBtn = document.getElementById('loginBtn');
    const loginBtnText = document.getElementById('loginBtnText');
    const forgotPasswordBtn = document.getElementById('forgotPassword');
    const requestAccessBtn = document.getElementById('requestAccess');
    
    // Modal elements
    const twoFactorModal = document.getElementById('twoFactorModal');
    const closeTwoFactorBtn = document.getElementById('closeTwoFactor');
    const verifyCodeBtn = document.getElementById('verifyCode');
    const cancelTwoFactorBtn = document.getElementById('cancelTwoFactor');
    const resendCodeBtn = document.getElementById('resendCode');
    const codeInputs = document.querySelectorAll('.code-input');
    
    const resetModal = document.getElementById('resetModal');
    const closeResetBtn = document.getElementById('closeReset');
    const submitResetBtn = document.getElementById('submitReset');
    const cancelResetBtn = document.getElementById('cancelReset');
    const resetUsername = document.getElementById('resetUsername');
    const resetCode = document.getElementById('resetCode');
    const newPassword = document.getElementById('newPassword');
    const confirmPassword = document.getElementById('confirmPassword');
    
    // Error messages
    const usernameError = document.getElementById('usernameError');
    const passwordError = document.getElementById('passwordError');
    const resetUsernameError = document.getElementById('resetUsernameError');
    const resetCodeError = document.getElementById('resetCodeError');
    const newPasswordError = document.getElementById('newPasswordError');
    const confirmPasswordError = document.getElementById('confirmPasswordError');
    
    // Security variables
    let failedAttempts = 0;
    const MAX_ATTEMPTS = 5;
    let twoFactorCode = '';
    let lastCodeSentTime = 0;
    const CODE_RESEND_DELAY = 30000; // 30 seconds
    
    // Initialize
    document.addEventListener('DOMContentLoaded', function() {
      // Password toggle
      togglePassword.addEventListener('click', function() {
        const type = passwordInput.getAttribute('type') === 'password' ? 'text' : 'password';
        passwordInput.setAttribute('type', type);
        this.classList.toggle('fa-eye');
        this.classList.toggle('fa-eye-slash');
      });
      
      // Forgot password
      forgotPasswordBtn.addEventListener('click', function(e) {
        e.preventDefault();
        resetModal.style.display = 'flex';
      });
      
      // Request access
      requestAccessBtn.addEventListener('click', function(e) {
        e.preventDefault();
        alert('Please contact the lab administrator at admin@siyaramailab.com');
      });
      
      // Close modals
      closeTwoFactorBtn.addEventListener('click', closeTwoFactorModal);
      cancelTwoFactorBtn.addEventListener('click', closeTwoFactorModal);
      closeResetBtn.addEventListener('click', closeResetModal);
      cancelResetBtn.addEventListener('click', closeResetModal);
      
      // Window click to close modals
      window.addEventListener('click', function(e) {
        if (e.target === twoFactorModal || e.target === resetModal) {
          closeTwoFactorModal();
          closeResetModal();
        }
      });
      
      // Code input handling
      codeInputs.forEach((input, index) => {
        // Allow only numbers
        input.addEventListener('input', function() {
          this.value = this.value.replace(/[^0-9]/g, '');
          
          // Auto-focus next input
          if (this.value.length === 1 && index < codeInputs.length - 1) {
            codeInputs[index + 1].focus();
          }
        });
        
        // Handle backspace
        input.addEventListener('keydown', function(e) {
          if (e.key === 'Backspace' && this.value.length === 0 && index > 0) {
            codeInputs[index - 1].focus();
          }
        });
      });
      
      // Verify 2FA code
      verifyCodeBtn.addEventListener('click', function() {
        const enteredCode = Array.from(codeInputs).map(input => input.value).join('');
        
        if (enteredCode.length !== 6) {
          alert('Please enter the full 6-digit code.');
          return;
        }
        
        if (enteredCode === twoFactorCode) {
          // Successful login - redirect to first page
          window.location.href = 'first-page.html';
        } else {
          alert('Invalid verification code. Please try again.');
          // Clear all inputs
          codeInputs.forEach(input => input.value = '');
          // Focus first input
          codeInputs[0].focus();
        }
      });
      
      // Resend 2FA code
      resendCodeBtn.addEventListener('click', function(e) {
        e.preventDefault();
        const currentTime = Date.now();
        
        if (currentTime - lastCodeSentTime < CODE_RESEND_DELAY) {
          const secondsLeft = Math.ceil((CODE_RESEND_DELAY - (currentTime - lastCodeSentTime)) / 1000);
          alert(`Please wait ${secondsLeft} seconds before requesting a new code.`);
          return;
        }
        
        twoFactorCode = generateRandomCode();
        lastCodeSentTime = currentTime;
        sendTwoFactorEmail(twoFactorCode);
        alert(`A new verification code has been sent to ${SECURE_CREDENTIALS.twoFactorEmail}`);
        
        // Clear all inputs
        codeInputs.forEach(input => input.value = '');
        // Focus first input
        codeInputs[0].focus();
      });
      
      // Submit password reset
      submitResetBtn.addEventListener('click', function() {
        let isValid = true;
        
        // Validate username
        if (resetUsername.value !== SECURE_CREDENTIALS.username) {
          resetUsernameError.textContent = 'Invalid username';
          resetUsernameError.style.display = 'block';
          isValid = false;
        } else {
          resetUsernameError.style.display = 'none';
        }
        
        // Validate security code
        if (resetCode.value !== SECURE_CREDENTIALS.resetCode) {
          resetCodeError.textContent = 'Invalid security code';
          resetCodeError.style.display = 'block';
          isValid = false;
        } else {
          resetCodeError.style.display = 'none';
        }
        
        // Validate new password
        if (newPassword.value.length < 8) {
          newPasswordError.textContent = 'Password must be at least 8 characters';
          newPasswordError.style.display = 'block';
          isValid = false;
        } else {
          newPasswordError.style.display = 'none';
        }
        
        // Validate password match
        if (newPassword.value !== confirmPassword.value) {
          confirmPasswordError.textContent = 'Passwords do not match';
          confirmPasswordError.style.display = 'block';
          isValid = false;
        } else {
          confirmPasswordError.style.display = 'none';
        }
        
        if (isValid) {
          // In a real app, you would send this to your server to update the password
          alert('Password reset successfully! You can now login with your new password.');
          closeResetModal();
        }
      });
      
      // Form submission
      loginForm.addEventListener('submit', function(e) {
        e.preventDefault();
        handleLogin();
      });
    });
    
    // Handle login
    function handleLogin() {
      // Check reCAPTCHA first
      if (grecaptcha.getResponse().length === 0) {
        alert('Please complete the reCAPTCHA verification.');
        return;
      }
      
      // Check attempt limit
      if (failedAttempts >= MAX_ATTEMPTS) {
        alert('Too many failed attempts. Your account has been temporarily locked.');
        return;
      }
      
      const username = usernameInput.value;
      const password = passwordInput.value;
      
      // Clear previous errors
      usernameError.style.display = 'none';
      passwordError.style.display = 'none';
      
      // Show loading state
      loginBtn.disabled = true;
      loginBtnText.innerHTML = '<span class="spinner"></span> Authenticating...';
      
      // Simulate network delay
      setTimeout(() => {
        if (username === SECURE_CREDENTIALS.username && password === SECURE_CREDENTIALS.password) {
          // Successful first factor auth - proceed to 2FA
          twoFactorCode = generateRandomCode();
          lastCodeSentTime = Date.now();
          sendTwoFactorEmail(twoFactorCode);
          openTwoFactorModal();
        } else {
          // Failed attempt
          failedAttempts++;
          
          if (username !== SECURE_CREDENTIALS.username) {
            usernameError.textContent = 'Invalid username';
            usernameError.style.display = 'block';
          }
          
          if (password !== SECURE_CREDENTIALS.password) {
            passwordError.textContent = 'Invalid password';
            passwordError.style.display = 'block';
          }
          
          const attemptsLeft = MAX_ATTEMPTS - failedAttempts;
          if (attemptsLeft > 0) {
            alert(`Invalid credentials. ${attemptsLeft} attempt${attemptsLeft > 1 ? 's' : ''} remaining.`);
          } else {
            alert('Account locked. Please reset your password.');
          }
          
          // Reset reCAPTCHA
          grecaptcha.reset();
        }
        
        // Reset button state
        loginBtn.disabled = false;
        loginBtnText.textContent = 'Sign In';
      }, 1500);
    }
    
    // Generate random 6-digit code
    function generateRandomCode() {
      return Math.floor(100000 + Math.random() * 900000).toString();
    }
    
    // Simulate sending 2FA email
    function sendTwoFactorEmail(code) {
      console.log(`2FA code ${code} sent to ${SECURE_CREDENTIALS.twoFactorEmail}`);
      // In a real app, you would send this to your server to email the user
    }
    
    // Open 2FA modal
    function openTwoFactorModal() {
      twoFactorModal.style.display = 'flex';
      // Focus first input
      codeInputs[0].focus();
    }
    
    // Close 2FA modal
    function closeTwoFactorModal() {
      twoFactorModal.style.display = 'none';
      // Clear all inputs
      codeInputs.forEach(input => input.value = '');
      // Reset login button
      loginBtn.disabled = false;
      loginBtnText.textContent = 'Sign In';
    }
    
    // Close reset modal
    function closeResetModal() {
      resetModal.style.display = 'none';
      // Clear all inputs
      resetUsername.value = '';
      resetCode.value = '';
      newPassword.value = '';
      confirmPassword.value = '';
      // Clear errors
      resetUsernameError.style.display = 'none';
      resetCodeError.style.display = 'none';
      newPasswordError.style.display = 'none';
      confirmPasswordError.style.display = 'none';
    }
  </script>
</body>
</html>

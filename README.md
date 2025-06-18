<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Secure Portal | SiyaRam AI Lab</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
  <script src="https://www.google.com/recaptcha/enterprise.js?render=6LdAVZcqAAAAAHoKIcFfs9RgZHrfx0K5_tbdGJ3U"></script>
  <style>
    :root {
      --primary-dark: #0f172a;
      --primary: #1e40af;
      --primary-light: #3b82f6;
      --secondary: #10b981;
      --danger: #ef4444;
      --warning: #f59e0b;
      --light: #f8fafc;
      --dark: #020617;
      --gray: #64748b;
      --gray-light: #e2e8f0;
      --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
      --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
      --border-radius: 12px;
      --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background-color: var(--primary-dark);
      color: var(--light);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      background-image: 
        radial-gradient(at 80% 0%, hsla(189, 100%, 56%, 0.1) 0px, transparent 50%),
        radial-gradient(at 0% 50%, hsla(355, 100%, 93%, 0.1) 0px, transparent 50%);
    }

    .security-container {
      width: 100%;
      max-width: 1200px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      background-color: rgba(15, 23, 42, 0.8);
      backdrop-filter: blur(10px);
      border-radius: var(--border-radius);
      overflow: hidden;
      box-shadow: var(--shadow-lg);
      border: 1px solid rgba(255, 255, 255, 0.1);
    }

    .security-hero {
      padding: 60px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      background: linear-gradient(135deg, rgba(30, 64, 175, 0.7), rgba(16, 185, 129, 0.5)), 
                  url('https://images.unsplash.com/photo-1620712943543-bcc4688e7485?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80') no-repeat center center;
      background-size: cover;
      position: relative;
    }

    .security-brand {
      display: flex;
      align-items: center;
      margin-bottom: 40px;
    }

    .security-brand-icon {
      width: 50px;
      height: 50px;
      background-color: var(--light);
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 15px;
      color: var(--primary);
      font-size: 1.5rem;
    }

    .security-brand-text {
      font-size: 1.8rem;
      font-weight: 700;
      background: linear-gradient(to right, var(--light), var(--gray-light));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .security-hero-title {
      font-size: 2.5rem;
      font-weight: 700;
      margin-bottom: 20px;
      line-height: 1.2;
    }

    .security-hero-subtitle {
      font-size: 1.1rem;
      margin-bottom: 30px;
      opacity: 0.9;
      line-height: 1.6;
    }

    .security-features {
      margin-top: 40px;
    }

    .security-feature {
      display: flex;
      align-items: flex-start;
      margin-bottom: 20px;
    }

    .security-feature-icon {
      width: 24px;
      height: 24px;
      background-color: var(--secondary);
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 15px;
      color: var(--light);
      font-size: 0.8rem;
      flex-shrink: 0;
      margin-top: 2px;
    }

    .security-feature-text {
      font-size: 0.95rem;
    }

    .security-login {
      padding: 60px;
      background-color: var(--light);
      color: var(--dark);
      position: relative;
    }

    .security-login-header {
      margin-bottom: 40px;
    }

    .security-login-title {
      font-size: 2rem;
      font-weight: 700;
      color: var(--primary-dark);
      margin-bottom: 10px;
    }

    .security-login-subtitle {
      color: var(--gray);
      font-size: 0.95rem;
    }

    .security-form {
      display: flex;
      flex-direction: column;
    }

    .security-form-group {
      margin-bottom: 20px;
      position: relative;
    }

    .security-form-label {
      display: block;
      margin-bottom: 8px;
      font-weight: 500;
      color: var(--dark);
      font-size: 0.9rem;
    }

    .security-form-input {
      width: 100%;
      padding: 14px 14px 14px 45px;
      border: 1px solid var(--gray-light);
      border-radius: 8px;
      font-size: 1rem;
      transition: var(--transition);
      background-color: white;
      font-family: 'Inter', sans-serif;
    }

    .security-form-input:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.2);
      outline: none;
    }

    .security-input-icon {
      position: absolute;
      left: 15px;
      top: 42px;
      color: var(--gray);
      font-size: 1.1rem;
    }

    .security-password-toggle {
      position: absolute;
      right: 15px;
      top: 42px;
      cursor: pointer;
      color: var(--gray);
      font-size: 1.1rem;
    }

    .security-remember-forgot {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      font-size: 0.9rem;
    }

    .security-remember-me {
      display: flex;
      align-items: center;
    }

    .security-remember-me input {
      margin-right: 8px;
      accent-color: var(--primary);
    }

    .security-forgot-password {
      color: var(--primary);
      text-decoration: none;
      font-weight: 500;
      cursor: pointer;
      transition: var(--transition);
    }

    .security-forgot-password:hover {
      color: var(--primary-dark);
      text-decoration: underline;
    }

    .security-recaptcha {
      margin: 20px 0;
      display: flex;
      justify-content: center;
    }

    .security-submit-btn {
      background: linear-gradient(to right, var(--primary), var(--primary-light));
      color: white;
      border: none;
      padding: 14px;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      margin-bottom: 20px;
      font-family: 'Inter', sans-serif;
      box-shadow: var(--shadow);
    }

    .security-submit-btn:hover {
      background: linear-gradient(to right, var(--primary-dark), var(--primary));
      transform: translateY(-2px);
    }

    .security-divider {
      display: flex;
      align-items: center;
      margin: 20px 0;
      color: var(--gray);
      font-size: 0.9rem;
    }

    .security-divider::before, .security-divider::after {
      content: "";
      flex: 1;
      border-bottom: 1px solid var(--gray-light);
    }

    .security-divider-text {
      padding: 0 15px;
    }

    .security-social-login {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-bottom: 25px;
    }

    .security-social-btn {
      width: 45px;
      height: 45px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: white;
      color: var(--dark);
      border: 1px solid var(--gray-light);
      cursor: pointer;
      transition: var(--transition);
      box-shadow: var(--shadow);
    }

    .security-social-btn:hover {
      transform: translateY(-3px);
      box-shadow: var(--shadow-lg);
    }

    .security-footer {
      text-align: center;
      font-size: 0.9rem;
      color: var(--gray);
    }

    .security-footer a {
      color: var(--primary);
      text-decoration: none;
      font-weight: 500;
    }

    .security-footer a:hover {
      text-decoration: underline;
    }

    .security-info {
      margin-top: 30px;
      padding: 15px;
      background-color: #f0f7ff;
      border-radius: 8px;
      font-size: 0.8rem;
      color: var(--primary-dark);
      display: flex;
      align-items: center;
      border-left: 4px solid var(--primary);
    }

    .security-info i {
      margin-right: 10px;
      color: var(--primary);
    }

    /* 2FA Modal */
    .security-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.8);
      z-index: 1000;
      justify-content: center;
      align-items: center;
      backdrop-filter: blur(5px);
    }

    .security-modal-content {
      background-color: white;
      padding: 40px;
      border-radius: var(--border-radius);
      width: 90%;
      max-width: 500px;
      box-shadow: var(--shadow-lg);
      position: relative;
      animation: modalFadeIn 0.3s;
      border: 1px solid rgba(0, 0, 0, 0.1);
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

    .security-close-modal {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: 1.5rem;
      cursor: pointer;
      color: var(--gray);
      transition: var(--transition);
    }

    .security-close-modal:hover {
      color: var(--dark);
    }

    .security-modal-title {
      font-size: 1.5rem;
      margin-bottom: 20px;
      color: var(--primary-dark);
    }

    .security-modal-subtitle {
      margin-bottom: 20px;
      color: var(--gray);
      font-size: 0.95rem;
      line-height: 1.6;
    }

    .security-code-inputs {
      display: flex;
      justify-content: space-between;
      margin: 30px 0;
    }

    .security-code-input {
      width: 50px;
      height: 60px;
      text-align: center;
      font-size: 1.5rem;
      border: 1px solid var(--gray-light);
      border-radius: 8px;
      font-family: 'JetBrains Mono', monospace;
      transition: var(--transition);
    }

    .security-code-input:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.2);
      outline: none;
    }

    .security-modal-btn {
      width: 100%;
      padding: 14px;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      margin-top: 15px;
      border: none;
    }

    .security-modal-primary {
      background-color: var(--primary);
      color: white;
    }

    .security-modal-primary:hover {
      background-color: var(--primary-dark);
    }

    .security-modal-secondary {
      background-color: transparent;
      color: var(--primary);
      border: 1px solid var(--primary);
    }

    .security-modal-secondary:hover {
      background-color: rgba(59, 130, 246, 0.1);
    }

    .security-resend-code {
      text-align: center;
      margin-top: 20px;
      font-size: 0.9rem;
      color: var(--gray);
    }

    .security-resend-code a {
      color: var(--primary);
      text-decoration: none;
      font-weight: 500;
      cursor: pointer;
    }

    .security-resend-code a:hover {
      text-decoration: underline;
    }

    /* Password Reset Modal */
    .security-reset-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.8);
      z-index: 1000;
      justify-content: center;
      align-items: center;
      backdrop-filter: blur(5px);
    }

    .security-reset-content {
      background-color: white;
      padding: 40px;
      border-radius: var(--border-radius);
      width: 90%;
      max-width: 500px;
      box-shadow: var(--shadow-lg);
      position: relative;
      animation: modalFadeIn 0.3s;
    }

    .security-reset-title {
      font-size: 1.5rem;
      margin-bottom: 20px;
      color: var(--primary-dark);
    }

    .security-reset-steps {
      margin-bottom: 20px;
    }

    .security-reset-step {
      display: none;
    }

    .security-reset-step.active {
      display: block;
    }

    .security-reset-step-title {
      font-weight: 600;
      margin-bottom: 15px;
      color: var(--primary-dark);
    }

    .security-reset-step-text {
      margin-bottom: 20px;
      color: var(--gray);
      font-size: 0.95rem;
      line-height: 1.6;
    }

    .security-reset-btns {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }

    /* Activity Monitor */
    .security-activity {
      position: absolute;
      bottom: 20px;
      right: 20px;
      display: flex;
      align-items: center;
      font-size: 0.8rem;
      color: var(--gray);
    }

    .security-activity-dot {
      width: 8px;
      height: 8px;
      background-color: var(--secondary);
      border-radius: 50%;
      margin-right: 8px;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0% {
        opacity: 1;
      }
      50% {
        opacity: 0.5;
      }
      100% {
        opacity: 1;
      }
    }

    /* Responsive styles */
    @media (max-width: 992px) {
      .security-container {
        grid-template-columns: 1fr;
      }
      
      .security-hero {
        display: none;
      }

      .security-login {
        padding: 40px;
      }
    }

    @media (max-width: 576px) {
      .security-login {
        padding: 30px 20px;
      }
      
      .security-login-title {
        font-size: 1.5rem;
      }

      .security-modal-content, .security-reset-content {
        padding: 30px 20px;
      }

      .security-code-input {
        width: 40px;
        height: 50px;
        font-size: 1.2rem;
      }
    }

    /* Animations */
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      10%, 30%, 50%, 70%, 90% { transform: translateX(-5px); }
      20%, 40%, 60%, 80% { transform: translateX(5px); }
    }

    .security-shake {
      animation: shake 0.5s;
    }

    /* Password strength meter */
    .security-password-strength {
      height: 4px;
      background-color: var(--gray-light);
      border-radius: 2px;
      margin-top: 8px;
      overflow: hidden;
    }

    .security-password-strength-bar {
      height: 100%;
      width: 0;
      transition: var(--transition);
    }

    .security-password-rules {
      margin-top: 10px;
      font-size: 0.8rem;
      color: var(--gray);
    }

    .security-password-rule {
      display: flex;
      align-items: center;
      margin-bottom: 5px;
    }

    .security-password-rule i {
      margin-right: 5px;
      font-size: 0.7rem;
    }

    .security-password-rule.valid {
      color: var(--secondary);
    }

    .security-password-rule.invalid {
      color: var(--gray);
    }
  </style>
</head>
<body>
  <div class="security-container">
    <div class="security-hero">
      <div class="security-brand">
        <div class="security-brand-icon">
          <i class="fas fa-atom"></i>
        </div>
        <div class="security-brand-text">SiyaRam AI Lab</div>
      </div>
      <h1 class="security-hero-title">Secure Research Portal</h1>
      <p class="security-hero-subtitle">
        Access cutting-edge AI research tools and laboratory management systems 
        with enterprise-grade security protocols and multi-factor authentication.
      </p>
      
      <div class="security-features">
        <div class="security-feature">
          <div class="security-feature-icon">
            <i class="fas fa-shield-alt"></i>
          </div>
          <div class="security-feature-text">
            Military-grade encryption with 256-bit SSL and multi-factor authentication
          </div>
        </div>
        <div class="security-feature">
          <div class="security-feature-icon">
            <i class="fas fa-fingerprint"></i>
          </div>
          <div class="security-feature-text">
            Biometric authentication support for enhanced security
          </div>
        </div>
        <div class="security-feature">
          <div class="security-feature-icon">
            <i class="fas fa-clock"></i>
          </div>
          <div class="security-feature-text">
            Session timeout after 15 minutes of inactivity
          </div>
        </div>
      </div>
    </div>

    <div class="security-login">
      <div class="security-login-header">
        <h2 class="security-login-title">Secure Authentication</h2>
        <p class="security-login-subtitle">Enter your credentials to access the SiyaRam AI Lab portal</p>
      </div>

      <form id="securityLoginForm" class="security-form">
        <div class="security-form-group">
          <label for="securityUsername" class="security-form-label">Username</label>
          <i class="fas fa-user security-input-icon"></i>
          <input type="text" id="securityUsername" class="security-form-input" placeholder="Enter your username" required autocomplete="username">
        </div>

        <div class="security-form-group">
          <label for="securityPassword" class="security-form-label">Password</label>
          <i class="fas fa-lock security-input-icon"></i>
          <input type="password" id="securityPassword" class="security-form-input" placeholder="Enter your password" required autocomplete="current-password">
          <i class="fas fa-eye security-password-toggle" id="securityTogglePassword"></i>
        </div>

        <div class="security-remember-forgot">
          <div class="security-remember-me">
            <input type="checkbox" id="securityRemember">
            <label for="securityRemember">Remember this device</label>
          </div>
          <a class="security-forgot-password" id="securityForgotPassword">Forgot password?</a>
        </div>

        <div class="security-recaptcha">
          <div class="g-recaptcha" data-sitekey="6LdAVZcqAAAAAHoKIcFfs9RgZHrfx0K5_tbdGJ3U"></div>
        </div>

        <button type="submit" class="security-submit-btn" id="securityLoginBtn">
          <span id="securityLoginBtnText">Authenticate</span>
          <i class="fas fa-lock" id="securityLoginBtnIcon" style="margin-left: 8px;"></i>
        </button>

        <div class="security-divider">
          <span class="security-divider-text">OR CONTINUE WITH</span>
        </div>

        <div class="security-social-login">
          <button type="button" class="security-social-btn">
            <i class="fab fa-google"></i>
          </button>
          <button type="button" class="security-social-btn">
            <i class="fab fa-microsoft"></i>
          </button>
          <button type="button" class="security-social-btn">
            <i class="fab fa-apple"></i>
          </button>
        </div>

        <div class="security-footer">
          Don't have access? <a href="#" id="securityRequestAccess">Request credentials</a>
        </div>

        <div class="security-info">
          <i class="fas fa-info-circle"></i>
          <span>This system is monitored for security purposes. Unauthorized access is prohibited.</span>
        </div>
      </form>

      <div class="security-activity">
        <div class="security-activity-dot"></div>
        <span>Secure connection established</span>
      </div>
    </div>
  </div>

  <!-- 2FA Verification Modal -->
  <div id="securityTwoFactorModal" class="security-modal">
    <div class="security-modal-content">
      <span class="security-close-modal" id="securityCloseTwoFactor">&times;</span>
      <h3 class="security-modal-title">Two-Factor Authentication</h3>
      <p class="security-modal-subtitle">
        We've sent a 6-digit verification code to <strong>sanatansingh000001@gmail.com</strong>. 
        Please enter it below to complete your login.
      </p>
      
      <div class="security-code-inputs">
        <input type="text" class="security-code-input" maxlength="1" pattern="[0-9]" inputmode="numeric">
        <input type="text" class="security-code-input" maxlength="1" pattern="[0-9]" inputmode="numeric">
        <input type="text" class="security-code-input" maxlength="1" pattern="[0-9]" inputmode="numeric">
        <input type="text" class="security-code-input" maxlength="1" pattern="[0-9]" inputmode="numeric">
        <input type="text" class="security-code-input" maxlength="1" pattern="[0-9]" inputmode="numeric">
        <input type="text" class="security-code-input" maxlength="1" pattern="[0-9]" inputmode="numeric">
      </div>
      
      <button type="button" class="security-modal-btn security-modal-primary" id="securityVerify2FA">Verify Code</button>
      <button type="button" class="security-modal-btn security-modal-secondary" id="securityCancel2FA">Cancel</button>
      
      <div class="security-resend-code">
        Didn't receive a code? <a href="#" id="securityResendCode">Resend code</a>
      </div>
    </div>
  </div>

  <!-- Password Reset Modal -->
  <div id="securityResetModal" class="security-reset-modal">
    <div class="security-reset-content">
      <span class="security-close-modal" id="securityCloseReset">&times;</span>
      <h3 class="security-reset-title">Reset Your Password</h3>
      
      <div class="security-reset-steps">
        <div id="securityResetStep1" class="security-reset-step active">
          <h4 class="security-reset-step-title">Step 1: Verify Your Identity</h4>
          <p class="security-reset-step-text">
            Enter your username and the security code provided by your administrator to verify your identity.
          </p>
          <div class="security-form-group">
            <label for="securityResetUsername" class="security-form-label">Username</label>
            <input type="text" id="securityResetUsername" class="security-form-input" placeholder="Your username">
          </div>
          <div class="security-form-group">
            <label for="securityResetCode" class="security-form-label">Security Code</label>
            <input type="text" id="securityResetCode" class="security-form-input" placeholder="Enter security code">
          </div>
          <div class="security-reset-btns">
            <button id="securityResetNext" class="security-modal-btn security-modal-primary">Next</button>
          </div>
        </div>
        
        <div id="securityResetStep2" class="security-reset-step">
          <h4 class="security-reset-step-title">Step 2: Set New Credentials</h4>
          <p class="security-reset-step-text">
            Create a strong new password following our security requirements. Your password must:
          </p>
          <div class="security-password-rules">
            <div class="security-password-rule invalid" id="securityRuleLength">
              <i class="fas fa-circle"></i>
              <span>Be at least 12 characters long</span>
            </div>
            <div class="security-password-rule invalid" id="securityRuleUpper">
              <i class="fas fa-circle"></i>
              <span>Contain uppercase letters</span>
            </div>
            <div class="security-password-rule invalid" id="securityRuleLower">
              <i class="fas fa-circle"></i>
              <span>Contain lowercase letters</span>
            </div>
            <div class="security-password-rule invalid" id="securityRuleNumber">
              <i class="fas fa-circle"></i>
              <span>Contain numbers</span>
            </div>
            <div class="security-password-rule invalid" id="securityRuleSpecial">
              <i class="fas fa-circle"></i>
              <span>Contain special characters</span>
            </div>
          </div>
          <div class="security-form-group">
            <label for="securityNewPassword" class="security-form-label">New Password</label>
            <input type="password" id="securityNewPassword" class="security-form-input" placeholder="New password">
            <div class="security-password-strength">
              <div class="security-password-strength-bar" id="securityPasswordStrength"></div>
            </div>
          </div>
          <div class="security-form-group">
            <label for="securityConfirmPassword" class="security-form-label">Confirm Password</label>
            <input type="password" id="securityConfirmPassword" class="security-form-input" placeholder="Confirm password">
          </div>
          <div class="security-reset-btns">
            <button id="securityResetBack" class="security-modal-btn security-modal-secondary">Back</button>
            <button id="securityResetSubmit" class="security-modal-btn security-modal-primary">Reset Password</button>
          </div>
        </div>
        
        <div id="securityResetStep3" class="security-reset-step">
          <h4 class="security-reset-step-title">Credentials Updated Successfully!</h4>
          <p class="security-reset-step-text">
            Your password has been successfully updated. You can now login with your new credentials.
          </p>
          <div class="security-reset-btns">
            <button id="securityResetClose" class="security-modal-btn security-modal-primary">Close</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Secure credential validation (in a real app, this would be server-side)
    const SECURE_CREDENTIALS = {
      username: 'SiyaRam4811',
      password: 'Lab123@',
      resetCode: '4811',
      twoFactorEmail: 'sanatansingh000001@gmail.com'
    };

    // DOM Elements
    const loginForm = document.getElementById('securityLoginForm');
    const usernameInput = document.getElementById('securityUsername');
    const passwordInput = document.getElementById('securityPassword');
    const togglePassword = document.getElementById('securityTogglePassword');
    const forgotPasswordBtn = document.getElementById('securityForgotPassword');
    const requestAccessBtn = document.getElementById('securityRequestAccess');
    const loginBtn = document.getElementById('securityLoginBtn');
    const loginBtnText = document.getElementById('securityLoginBtnText');
    const loginBtnIcon = document.getElementById('securityLoginBtnIcon');
    
    // Modal elements
    const twoFactorModal = document.getElementById('securityTwoFactorModal');
    const closeTwoFactorBtn = document.getElementById('securityCloseTwoFactor');
    const verify2FABtn = document.getElementById('securityVerify2FA');
    const cancel2FABtn = document.getElementById('securityCancel2FA');
    const resendCodeBtn = document.getElementById('securityResendCode');
    const codeInputs = document.querySelectorAll('.security-code-input');
    
    const resetModal = document.getElementById('securityResetModal');
    const closeResetBtn = document.getElementById('securityCloseReset');
    const resetNextBtn = document.getElementById('securityResetNext');
    const resetBackBtn = document.getElementById('securityResetBack');
    const resetSubmitBtn = document.getElementById('securityResetSubmit');
    const resetCloseBtn = document.getElementById('securityResetClose');
    const resetUsername = document.getElementById('securityResetUsername');
    const resetCode = document.getElementById('securityResetCode');
    const newPassword = document.getElementById('securityNewPassword');
    const confirmPassword = document.getElementById('securityConfirmPassword');
    const passwordStrength = document.getElementById('securityPasswordStrength');
    const passwordRules = {
      length: document.getElementById('securityRuleLength'),
      upper: document.getElementById('securityRuleUpper'),
      lower: document.getElementById('securityRuleLower'),
      number: document.getElementById('securityRuleNumber'),
      special: document.getElementById('securityRuleSpecial')
    };
    
    // Security variables
    let failedAttempts = 0;
    const MAX_ATTEMPTS = 5;
    let twoFactorCode = generateRandomCode();
    let lastCodeSentTime = 0;
    const CODE_RESEND_DELAY = 30000; // 30 seconds
    
    // Initialize the app
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
        alert('Please contact the lab administrator at admin@siyaramailab.com to request access credentials.');
      });
      
      // Close modals
      closeTwoFactorBtn.addEventListener('click', closeTwoFactorModal);
      cancel2FABtn.addEventListener('click', closeTwoFactorModal);
      closeResetBtn.addEventListener('click', closeResetModal);
      resetCloseBtn.addEventListener('click', closeResetModal);
      
      // Window click to close modals
      window.addEventListener('click', function(e) {
        if (e.target === twoFactorModal) {
          closeTwoFactorModal();
        }
        if (e.target === resetModal) {
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
      verify2FABtn.addEventListener('click', function() {
        const enteredCode = Array.from(codeInputs).map(input => input.value).join('');
        
        if (enteredCode.length !== 6) {
          alert('Please enter the full 6-digit code.');
          return;
        }
        
        if (enteredCode === twoFactorCode) {
          // Successful login - redirect to first page
          alert('Authentication successful! Redirecting to dashboard...');
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
      
      // Password reset steps
      resetNextBtn.addEventListener('click', function() {
        if (resetUsername.value !== SECURE_CREDENTIALS.username) {
          alert('Invalid username. Please try again.');
          return;
        }
        
        if (resetCode.value !== SECURE_CREDENTIALS.resetCode) {
          alert('Invalid security code. Please try again.');
          return;
        }
        
        // Move to step 2
        document.getElementById('securityResetStep1').classList.remove('active');
        document.getElementById('securityResetStep2').classList.add('active');
      });
      
      resetBackBtn.addEventListener('click', function() {
        // Back to step 1
        document.getElementById('securityResetStep2').classList.remove('active');
        document.getElementById('securityResetStep1').classList.add('active');
      });
      
      // Password strength checker
      newPassword.addEventListener('input', checkPasswordStrength);
      
      // Submit new password
      resetSubmitBtn.addEventListener('click', function() {
        if (newPassword.value !== confirmPassword.value) {
          alert('Passwords do not match!');
          return;
        }
        
        if (!isPasswordStrong(newPassword.value)) {
          alert('Please make sure your password meets all the requirements.');
          return;
        }
        
        // In a real app, you would send this to your server to update the password
        console.log('Password reset to:', newPassword.value);
        
        // Move to success step
        document.getElementById('securityResetStep2').classList.remove('active');
        document.getElementById('securityResetStep3').classList.add('active');
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
        alert('Too many failed attempts. Your account has been temporarily locked. Please try again later or reset your password.');
        return;
      }
      
      const username = usernameInput.value;
      const password = passwordInput.value;
      
      // Show loading state
      loginBtnText.textContent = 'Authenticating...';
      loginBtnIcon.className = 'fas fa-spinner fa-spin';
      loginBtn.disabled = true;
      
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
          loginForm.classList.add('security-shake');
          setTimeout(() => {
            loginForm.classList.remove('security-shake');
          }, 500);
          
          const attemptsLeft = MAX_ATTEMPTS - failedAttempts;
          alert(`Invalid credentials. ${attemptsLeft > 0 ? `${attemptsLeft} attempt${attemptsLeft > 1 ? 's' : ''} remaining.` : 'No attempts remaining.'}`);
          
          // Reset reCAPTCHA
          grecaptcha.reset();
        }
        
        // Reset button state
        loginBtnText.textContent = 'Authenticate';
        loginBtnIcon.className = 'fas fa-lock';
        loginBtn.disabled = false;
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
    }
    
    // Close reset modal
    function closeResetModal() {
      resetModal.style.display = 'none';
      // Reset all steps
      document.querySelectorAll('.security-reset-step').forEach(step => {
        step.classList.remove('active');
      });
      document.getElementById('securityResetStep1').classList.add('active');
      // Clear all inputs
      resetUsername.value = '';
      resetCode.value = '';
      newPassword.value = '';
      confirmPassword.value = '';
      // Reset password strength
      passwordStrength.style.width = '0%';
      passwordStrength.style.backgroundColor = '';
      // Reset rules
      Object.values(passwordRules).forEach(rule => {
        rule.classList.remove('valid');
        rule.classList.add('invalid');
      });
    }
    
    // Check password strength
    function checkPasswordStrength() {
      const password = newPassword.value;
      let strength = 0;
      
      // Length check (12+ characters)
      const hasLength = password.length >= 12;
      passwordRules.length.classList.toggle('valid', hasLength);
      passwordRules.length.classList.toggle('invalid', !hasLength);
      if (hasLength) strength += 20;
      
      // Uppercase check
      const hasUpper = /[A-Z]/.test(password);
      passwordRules.upper.classList.toggle('valid', hasUpper);
      passwordRules.upper.classList.toggle('invalid', !hasUpper);
      if (hasUpper) strength += 20;
      
      // Lowercase check
      const hasLower = /[a-z]/.test(password);
      passwordRules.lower.classList.toggle('valid', hasLower);
      passwordRules.lower.classList.toggle('invalid', !hasLower);
      if (hasLower) strength += 20;
      
      // Number check
      const hasNumber = /[0-9]/.test(password);
      passwordRules.number.classList.toggle('valid', hasNumber);
      passwordRules.number.classList.toggle('invalid', !hasNumber);
      if (hasNumber) strength += 20;
      
      // Special char check
      const hasSpecial = /[!@#$%^&*(),.?":{}|<>]/.test(password);
      passwordRules.special.classList.toggle('valid', hasSpecial);
      passwordRules.special.classList.toggle('invalid', !hasSpecial);
      if (hasSpecial) strength += 20;
      
      // Update strength bar
      passwordStrength.style.width = `${strength}%`;
      
      // Set color based on strength
      if (strength < 60) {
        passwordStrength.style.backgroundColor = var(--danger);
      } else if (strength < 80) {
        passwordStrength.style.backgroundColor = var(--warning);
      } else {
        passwordStrength.style.backgroundColor = var(--secondary);
      }
    }
    
    // Check if password meets all requirements
    function isPasswordStrong(password) {
      return password.length >= 12 &&
             /[A-Z]/.test(password) &&
             /[a-z]/.test(password) &&
             /[0-9]/.test(password) &&
             /[!@#$%^&*(),.?":{}|<>]/.test(password);
    }
  </script>
</body>
</html>

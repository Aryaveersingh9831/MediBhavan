<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MediBhavan - Secure Medical Records</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    :root {
      --primary: #4F46E5;
      --primary-light: #6366F1;
      --secondary: #10B981;
      --dark: #1F2937;
      --light: #F9FAFB;
      --gray: #6B7280;
      --danger: #EF4444;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      font-family: 'Poppins', sans-serif;
      background-color: #F3F4F6;
      color: var(--dark);
    }
    
    .app {
      min-height: 100vh;
    }
    
    /* Auth Page Styling */
    .auth-container {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background: linear-gradient(135deg, #f5f7fa 0%, #e4e8f0 100%);
      position: relative;
      overflow: hidden;
    }
    
    .auth-container::before {
      content: '';
      position: absolute;
      top: -50%;
      right: -50%;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle, var(--primary-light) 0%, transparent 70%);
      opacity: 0.1;
      z-index: 0;
    }
    
    .auth-card {
      background: white;
      padding: 2.5rem;
      border-radius: 16px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
      width: 100%;
      max-width: 450px;
      position: relative;
      z-index: 1;
      border: 1px solid rgba(255, 255, 255, 0.3);
      backdrop-filter: blur(10px);
    }
    
    .auth-card h1 {
      text-align: center;
      color: var(--primary);
      margin-bottom: 1.5rem;
      font-weight: 600;
      font-size: 1.8rem;
    }
    
    .auth-logo {
      text-align: center;
      margin-bottom: 1.5rem;
    }
    
    .auth-logo img {
      height: 60px;
      margin-bottom: 1rem;
    }
    
    .auth-toggle {
      text-align: center;
      margin-top: 1.5rem;
      color: var(--gray);
      font-size: 0.9rem;
    }
    
    .auth-toggle span {
      color: var(--primary);
      cursor: pointer;
      font-weight: 500;
      transition: all 0.3s ease;
    }
    
    .auth-toggle span:hover {
      text-decoration: underline;
    }
    
    /* Form Styling */
    .auth-form {
      display: flex;
      flex-direction: column;
    }
    
    .form-group {
      margin-bottom: 1.25rem;
      position: relative;
    }
    
    .form-group label {
      display: block;
      margin-bottom: 0.5rem;
      color: var(--dark);
      font-weight: 500;
      font-size: 0.9rem;
    }
    
    .form-group input {
      width: 100%;
      padding: 0.85rem 1rem;
      border: 1px solid #E5E7EB;
      border-radius: 8px;
      font-size: 0.95rem;
      transition: all 0.3s ease;
      background-color: var(--light);
    }
    
    .form-group input:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.2);
    }
    
    .form-group .input-icon {
      position: absolute;
      right: 1rem;
      top: 50%;
      transform: translateY(-50%);
      color: var(--gray);
    }
    
    .role-selection {
      margin: 1.5rem 0;
      display: flex;
      gap: 1rem;
    }
    
    .role-option {
      flex: 1;
      border: 1px solid #E5E7EB;
      border-radius: 8px;
      padding: 1rem;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s ease;
      background-color: white;
    }
    
    .role-option:hover {
      border-color: var(--primary);
    }
    
    .role-option.selected {
      border-color: var(--primary);
      background-color: rgba(79, 70, 229, 0.05);
    }
    
    .role-option i {
      font-size: 1.5rem;
      margin-bottom: 0.5rem;
      color: var(--primary);
    }
    
    .role-option .role-name {
      font-weight: 500;
      margin-bottom: 0.25rem;
    }
    
    .role-option .role-desc {
      font-size: 0.8rem;
      color: var(--gray);
    }
    
    .auth-button {
      background-color: var(--primary);
      color: white;
      border: none;
      padding: 1rem;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: 500;
      cursor: pointer;
      margin-top: 0.5rem;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }
    
    .auth-button:hover {
      background-color: var(--primary-light);
      transform: translateY(-2px);
      box-shadow: 0 4px 12px rgba(79, 70, 229, 0.2);
    }
    
    .social-auth {
      margin-top: 1.5rem;
      display: flex;
      flex-direction: column;
      gap: 0.75rem;
    }
    
    .social-button {
      padding: 0.85rem;
      border-radius: 8px;
      font-size: 0.95rem;
      font-weight: 500;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.75rem;
      border: 1px solid #E5E7EB;
      background: white;
      transition: all 0.3s ease;
    }
    
    .social-button:hover {
      background-color: #F9FAFB;
    }
    
    .social-button.google {
      color: #DB4437;
    }
    
    .social-button.facebook {
      color: #4267B2;
    }
    
    .divider {
      display: flex;
      align-items: center;
      margin: 1.5rem 0;
      color: var(--gray);
      font-size: 0.8rem;
    }
    
    .divider::before, .divider::after {
      content: '';
      flex: 1;
      height: 1px;
      background: #E5E7EB;
      margin: 0 0.5rem;
    }
    
    .recaptcha-notice {
      font-size: 0.7rem;
      color: var(--gray);
      text-align: center;
      margin-top: 1.5rem;
      line-height: 1.4;
    }
    
    .error {
      color: var(--danger);
      font-size: 0.8rem;
      margin-top: 0.25rem;
    }
    
    /* Dashboard Styling */
    .dashboard {
      display: flex;
      min-height: 100vh;
    }
    
    .sidebar {
      width: 280px;
      background: white;
      border-right: 1px solid #E5E7EB;
      padding: 1.5rem;
      display: flex;
      flex-direction: column;
    }
    
    .sidebar-header {
      display: flex;
      align-items: center;
      margin-bottom: 2rem;
      padding-bottom: 1.5rem;
      border-bottom: 1px solid #E5E7EB;
    }
    
    .sidebar-header img {
      height: 40px;
      margin-right: 0.75rem;
    }
    
    .sidebar-header h2 {
      font-size: 1.2rem;
      font-weight: 600;
      color: var(--primary);
    }
    
    .nav-item {
      display: flex;
      align-items: center;
      padding: 0.75rem 1rem;
      border-radius: 8px;
      margin-bottom: 0.5rem;
      color: var(--dark);
      text-decoration: none;
      transition: all 0.3s ease;
    }
    
    .nav-item:hover {
      background-color: #F3F4F6;
    }
    
    .nav-item.active {
      background-color: rgba(79, 70, 229, 0.1);
      color: var(--primary);
      font-weight: 500;
    }
    
    .nav-item i {
      margin-right: 0.75rem;
      width: 20px;
      text-align: center;
    }
    
    .user-profile {
      margin-top: auto;
      padding-top: 1.5rem;
      border-top: 1px solid #E5E7EB;
      display: flex;
      align-items: center;
    }
    
    .user-avatar {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background-color: var(--primary);
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 0.75rem;
      font-weight: 500;
    }
    
    .user-info h4 {
      font-size: 0.9rem;
      font-weight: 500;
      margin-bottom: 0.1rem;
    }
    
    .user-info p {
      font-size: 0.75rem;
      color: var(--gray);
    }
    
    .main-content {
      flex: 1;
      padding: 2rem;
      background-color: #F9FAFB;
    }
    
    .header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 2rem;
    }
    
    .header h2 {
      font-size: 1.5rem;
      font-weight: 600;
      color: var(--dark);
    }
    
    .search-bar {
      display: flex;
      align-items: center;
      background: white;
      border-radius: 8px;
      padding: 0.5rem 1rem;
      width: 300px;
      box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
    }
    
    .search-bar input {
      border: none;
      outline: none;
      flex: 1;
      padding: 0.5rem;
      background: transparent;
    }
    
    .search-bar i {
      color: var(--gray);
    }
    
    .card {
      background: white;
      border-radius: 12px;
      padding: 1.5rem;
      margin-bottom: 1.5rem;
      box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
    }
    
    .card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1.5rem;
    }
    
    .card-header h3 {
      font-size: 1.2rem;
      font-weight: 600;
    }
    
    .btn {
      padding: 0.75rem 1.25rem;
      border-radius: 8px;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.3s ease;
      border: none;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
    }
    
    .btn-primary {
      background-color: var(--primary);
      color: white;
    }
    
    .btn-primary:hover {
      background-color: var(--primary-light);
      transform: translateY(-2px);
      box-shadow: 0 4px 12px rgba(79, 70, 229, 0.2);
    }
    
    .btn-outline {
      background: transparent;
      border: 1px solid #E5E7EB;
      color: var(--dark);
    }
    
    .btn-outline:hover {
      background-color: #F9FAFB;
    }
    
    .patient-info {
      display: flex;
      align-items: center;
      margin-bottom: 1.5rem;
    }
    
    .patient-avatar {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background-color: var(--secondary);
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 1rem;
      font-size: 1.5rem;
      font-weight: 500;
    }
    
    .patient-details h3 {
      font-size: 1.2rem;
      font-weight: 600;
      margin-bottom: 0.25rem;
    }
    
    .patient-details p {
      color: var(--gray);
      font-size: 0.9rem;
    }
    
    .file-upload-area {
      border: 2px dashed #E5E7EB;
      border-radius: 12px;
      padding: 2rem;
      text-align: center;
      margin-bottom: 1.5rem;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .file-upload-area:hover {
      border-color: var(--primary);
      background-color: rgba(79, 70, 229, 0.02);
    }
    
    .file-upload-area i {
      font-size: 2rem;
      color: var(--primary);
      margin-bottom: 1rem;
    }
    
    .file-upload-area p {
      color: var(--gray);
      margin-bottom: 0.5rem;
    }
    
    .file-upload-area .btn {
      margin-top: 1rem;
    }
    
    .file-list {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 1rem;
    }
    
    .file-item {
      background: white;
      border-radius: 8px;
      padding: 1rem;
      border: 1px solid #E5E7EB;
      transition: all 0.3s ease;
    }
    
    .file-item:hover {
      transform: translateY(-2px);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
    }
    
    .file-icon {
      width: 40px;
      height: 40px;
      border-radius: 8px;
      background-color: rgba(79, 70, 229, 0.1);
      color: var(--primary);
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 0.75rem;
    }
    
    .file-name {
      font-weight: 500;
      margin-bottom: 0.25rem;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    
    .file-meta {
      display: flex;
      justify-content: space-between;
      color: var(--gray);
      font-size: 0.8rem;
    }
    
    .file-actions {
      display: flex;
      gap: 0.5rem;
      margin-top: 0.75rem;
    }
    
    .file-actions .btn {
      padding: 0.5rem;
      font-size: 0.8rem;
    }
    
    /* Responsive */
    @media (max-width: 768px) {
      .dashboard {
        flex-direction: column;
      }
      
      .sidebar {
        width: 100%;
        padding: 1rem;
      }
      
      .main-content {
        padding: 1.5rem;
      }
      
      .header {
        flex-direction: column;
        align-items: flex-start;
        gap: 1rem;
      }
      
      .search-bar {
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <div id="root"></div>

  <!-- Load React and Babel -->
  <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js" crossorigin></script>
  <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
  
  <!-- Medical Icons SVG -->
  <svg xmlns="http://www.w3.org/2000/svg" style="display: none;">
    <symbol id="icon-medical" viewBox="0 0 24 24">
      <path fill="currentColor" d="M19 3H5c-1.1 0-1.99.9-1.99 2L3 19c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-1 11h-4v4h-4v-4H6v-4h4V6h4v4h4v4z"/>
    </symbol>
    <symbol id="icon-doctor" viewBox="0 0 24 24">
      <path fill="currentColor" d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 3c1.66 0 3 1.34 3 3s-1.34 3-3 3-3-1.34-3-3 1.34-3 3-3zm0 14.2c-2.5 0-4.71-1.28-6-3.22.03-1.99 4-3.08 6-3.08 1.99 0 5.97 1.09 6 3.08-1.29 1.94-3.5 3.22-6 3.22z"/>
    </symbol>
    <symbol id="icon-patient" viewBox="0 0 24 24">
      <path fill="currentColor" d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
    </symbol>
  </svg>

  <script type="text/babel" data-presets="react">
    // Backend Simulation
    const fakeDatabase = {
      users: [
        {
          email: "doctor@example.com",
          password: "password123",
          role: "doctor",
          name: "Dr. Sarah Johnson",
          userId: "Dr_7a3b9c",
          _id: "doc1"
        },
        {
          email: "patient@example.com",
          password: "password123",
          role: "patient",
          name: "John Smith",
          userId: "P_4d5e6f",
          _id: "pat1"
        }
      ],
      files: [],
      auditLogs: []
    };
    
    class User {
      constructor(email, password, role, name) {
        this.email = email;
        this.password = password;
        this.role = role;
        this.name = name;
        this.userId = this.generateUserId(role);
        this._id = Math.random().toString(36).substr(2, 9);
      }
      
      generateUserId(role) {
        const prefix = role === 'doctor' ? 'Dr_' : 'P_';
        return prefix + Math.random().toString(36).substr(2, 6);
      }
    }
    
    // Frontend Components
    function LoginForm({ setUser, onSwitch }) {
      const [email, setEmail] = React.useState('');
      const [password, setPassword] = React.useState('');
      const [error, setError] = React.useState('');
      const [loading, setLoading] = React.useState(false);
      
      const handleSubmit = (e) => {
        e.preventDefault();
        setLoading(true);
        setError('');
        
        // Simulate API call
        setTimeout(() => {
          const user = fakeDatabase.users.find(u => u.email === email && u.password === password);
          if (user) {
            setUser(user);
          } else {
            setError('Invalid email or password');
          }
          setLoading(false);
        }, 800);
      };
      
      return (
        <form onSubmit={handleSubmit} className="auth-form">
          <h2>Log In</h2>
          {error && <div className="error">{error}</div>}
          <div className="form-group">
            <label>Email</label>
            <input 
              type="email" 
              value={email} 
              onChange={(e) => setEmail(e.target.value)} 
              required 
              placeholder="Enter your email"
            />
            <i className="fas fa-envelope input-icon"></i>
          </div>
          <div className="form-group">
            <label>Password</label>
            <input 
              type="password" 
              value={password} 
              onChange={(e) => setPassword(e.target.value)} 
              required 
              placeholder="Enter your password"
            />
            <i className="fas fa-lock input-icon"></i>
          </div>
          <button type="submit" className="auth-button" disabled={loading}>
            {loading ? 'Logging in...' : 'Log In'}
            {loading ? <i className="fas fa-spinner fa-spin"></i> : <i className="fas fa-sign-in-alt"></i>}
          </button>
          
          <div className="divider">or continue with</div>
          
          <div className="social-auth">
            <button type="button" className="social-button google">
              <i className="fab fa-google"></i> Google
            </button>
            <button type="button" className="social-button facebook">
              <i className="fab fa-facebook-f"></i> Facebook
            </button>
          </div>
        </form>
      );
    }
    
    function SignupForm({ setUser, onSwitch }) {
      const [formData, setFormData] = React.useState({
        email: '',
        confirmEmail: '',
        password: '',
        role: '',
        name: ''
      });
      const [errors, setErrors] = React.useState({});
      const [loading, setLoading] = React.useState(false);
      
      const handleChange = (e) => {
        const { name, value } = e.target;
        setFormData(prev => ({ ...prev, [name]: value }));
      };
      
      const selectRole = (role) => {
        setFormData(prev => ({ ...prev, role }));
      };
      
      const handleSubmit = (e) => {
        e.preventDefault();
        setLoading(true);
        const newErrors = {};
        
        if (formData.email !== formData.confirmEmail) {
          newErrors.email = "Emails don't match";
        }
        if (formData.password.length < 8) {
          newErrors.password = "Password must be at least 8 characters";
        }
        if (!formData.role) {
          newErrors.role = "Please select a role";
        }
        
        if (Object.keys(newErrors).length > 0) {
          setErrors(newErrors);
          setLoading(false);
          return;
        }
        
        // Simulate API call
        setTimeout(() => {
          const newUser = new User(
            formData.email,
            formData.password,
            formData.role,
            formData.name
          );
          
          fakeDatabase.users.push(newUser);
          setUser(newUser);
          setLoading(false);
        }, 1000);
      };
      
      return (
        <form onSubmit={handleSubmit} className="auth-form">
          <h2>Create Account</h2>
          
          <div className="form-group">
            <label>Email</label>
            <input
              type="email"
              name="email"
              value={formData.email}
              onChange={handleChange}
              required
              placeholder="Enter your email"
            />
            <i className="fas fa-envelope input-icon"></i>
            {errors.email && <span className="error">{errors.email}</span>}
          </div>
          
          <div className="form-group">
            <label>Confirm Email</label>
            <input
              type="email"
              name="confirmEmail"
              value={formData.confirmEmail}
              onChange={handleChange}
              required
              placeholder="Confirm your email"
            />
            <i className="fas fa-envelope input-icon"></i>
          </div>
          
          <div className="form-group">
            <label>Full Name</label>
            <input
              type="text"
              name="name"
              value={formData.name}
              onChange={handleChange}
              required
              placeholder="Enter your full name"
            />
            <i className="fas fa-user input-icon"></i>
          </div>
          
          <div className="form-group">
            <label>Password</label>
            <input
              type="password"
              name="password"
              value={formData.password}
              onChange={handleChange}
              required
              placeholder="Create a password"
            />
            <i className="fas fa-lock input-icon"></i>
            {errors.password && <span className="error">{errors.password}</span>}
          </div>
          
          <div style={{ marginBottom: '1.5rem' }}>
            <label style={{ display: 'block', marginBottom: '0.5rem', fontWeight: '500' }}>I am a:</label>
            <div className="role-selection">
              <div 
                className={`role-option ${formData.role === 'patient' ? 'selected' : ''}`}
                onClick={() => selectRole('patient')}
              >
                <svg width="24" height="24" fill="currentColor">
                  <use xlinkHref="#icon-patient" />
                </svg>
                <div className="role-name">Patient</div>
                <div className="role-desc">I need medical care</div>
              </div>
              <div 
                className={`role-option ${formData.role === 'doctor' ? 'selected' : ''}`}
                onClick={() => selectRole('doctor')}
              >
                <svg width="24" height="24" fill="currentColor">
                  <use xlinkHref="#icon-doctor" />
                </svg>
                <div className="role-name">Doctor</div>
                <div className="role-desc">I provide medical care</div>
              </div>
            </div>
            {errors.role && <span className="error" style={{ display: 'block', marginTop: '0.5rem' }}>{errors.role}</span>}
          </div>
          
          <button type="submit" className="auth-button" disabled={loading}>
            {loading ? 'Creating account...' : 'Sign Up'}
            {loading ? <i className="fas fa-spinner fa-spin"></i> : <i className="fas fa-user-plus"></i>}
          </button>
          
          <div className="recaptcha-notice">
            This site is protected by reCAPTCHA Enterprise. Goodies Privacy Policy and Terms of Service apply
          </div>
        </form>
      );
    }
    
    function AuthPage({ setUser }) {
      const [isLogin, setIsLogin] = React.useState(true);
      
      return (
        <div className="auth-container">
          <div className="auth-card">
            <div className="auth-logo">
              <svg width="60" height="60" fill="#4F46E5">
                <use xlinkHref="#icon-medical" />
              </svg>
              <h1>MediBhavan</h1>
            </div>
            {isLogin ? (
              <>
                <LoginForm setUser={setUser} />
                <p className="auth-toggle">
                  Don't have an account?{' '}
                  <span onClick={() => setIsLogin(false)}>Sign Up</span>
                </p>
              </>
            ) : (
              <>
                <SignupForm setUser={setUser} />
                <p className="auth-toggle">
                  Already have an account?{' '}
                  <span onClick={() => setIsLogin(true)}>Log In</span>
                </p>
              </>
            )}
          </div>
        </div>
      );
    }
    
    function DoctorDashboard({ user }) {
      const [patientId, setPatientId] = React.useState('');
      const [currentPatient, setCurrentPatient] = React.useState(null);
      const [files, setFiles] = React.useState([]);
      const [message, setMessage] = React.useState('');
      const [activeTab, setActiveTab] = React.useState('files');
      
      const connectToPatient = () => {
        const patient = fakeDatabase.users.find(u => u.userId === patientId && u.role === 'patient');
        if (patient) {
          setCurrentPatient(patient);
          
          // Load patient files (simulated)
          setTimeout(() => {
            setFiles([
              {
                id: '1',
                name: 'Blood Test Results.pdf',
                type: 'report',
                date: '2023-05-15',
                size: '2.4 MB'
              },
              {
                id: '2',
                name: 'Prescription_0423.pdf',
                type: 'prescription',
                date: '2023-04-23',
                size: '1.1 MB'
              }
            ]);
          }, 500);
        } else {
          alert('Patient not found');
        }
      };
      
      const uploadFile = () => {
        const newFile = {
          id: Math.random().toString(36).substr(2, 9),
          name: 'New_Prescription.pdf',
          type: 'prescription',
          date: new Date().toISOString().split('T')[0],
          size: '1.5 MB'
        };
        setFiles([...files, newFile]);
        alert('File uploaded successfully!');
      };
      
      const sendMessage = () => {
        if (message.trim()) {
          alert(`Message sent to ${currentPatient.name}: ${message}`);
          setMessage('');
        }
      };
      
      return (
        <div className="dashboard">
          <div className="sidebar">
            <div className="sidebar-header">
              <svg width="40" height="40" fill="#4F46E5">
                <use xlinkHref="#icon-medical" />
              </svg>
              <h2>MediBhavan</h2>
            </div>
            
            <a href="#" className="nav-item active">
              <i className="fas fa-home"></i> Dashboard
            </a>
            <a href="#" className="nav-item">
              <i className="fas fa-calendar-alt"></i> Appointments
            </a>
            <a href="#" className="nav-item">
              <i className="fas fa-file-medical"></i> Records
            </a>
            <a href="#" className="nav-item">
              <i className="fas fa-users"></i> Patients
            </a>
            <a href="#" className="nav-item">
              <i className="fas fa-cog"></i> Settings
            </a>
            
            <div className="user-profile">
              <div className="user-avatar">
                {user.name.split(' ').map(n => n[0]).join('')}
              </div>
              <div className="user-info">
                <h4>{user.name}</h4>
                <p>{user.userId}</p>
              </div>
            </div>
          </div>
          
          <div className="main-content">
            <div className="header">
              <h2>Welcome back, Dr. {user.name.split(' ')[1]}</h2>
              <div className="search-bar">
                <i className="fas fa-search"></i>
                <input type="text" placeholder="Search..." />
              </div>
            </div>
            
            <div className="card">
              <div className="patient-connect" style={{ display: 'flex', gap: '1rem' }}>
                <input
                  type="text"
                  placeholder="Enter Patient ID (P_...)"
                  value={patientId}
                  onChange={(e) => setPatientId(e.target.value)}
                  style={{ flex: 1, padding: '0.85rem 1rem', borderRadius: '8px', border: '1px solid #E5E7EB' }}
                />
                <button 
                  className="btn btn-primary"
                  onClick={connectToPatient}
                  style={{ padding: '0.85rem 1.5rem' }}
                >
                  <i className="fas fa-link"></i> Connect
                </button>
              </div>
            </div>
            
            {currentPatient && (
              <>
                <div className="card">
                  <div className="patient-info">
                    <div className="patient-avatar">
                      {currentPatient.name.split(' ').map(n => n[0]).join('')}
                    </div>
                    <div className="patient-details">
                      <h3>{currentPatient.name}</h3>
                      <p>Patient ID: {currentPatient.userId}</p>
                    </div>
                  </div>
                  
                  <div className="tabs" style={{ display: 'flex', borderBottom: '1px solid #E5E7EB', marginBottom: '1.5rem' }}>
                    <button 
                      className={`tab-btn ${activeTab === 'files' ? 'active' : ''}`}
                      onClick={() => setActiveTab('files')}
                      style={{
                        padding: '0.75rem 1.5rem',
                        background: 'none',
                        border: 'none',
                        borderBottom: activeTab === 'files' ? '2px solid var(--primary)' : 'none',
                        color: activeTab === 'files' ? 'var(--primary)' : 'var(--gray)',
                        fontWeight: activeTab === 'files' ? '600' : '400',
                        cursor: 'pointer'
                      }}
                    >
                      <i className="fas fa-file-medical"></i> Medical Files
                    </button>
                    <button 
                      className={`tab-btn ${activeTab === 'chat' ? 'active' : ''}`}
                      onClick={() => setActiveTab('chat')}
                      style={{
                        padding: '0.75rem 1.5rem',
                        background: 'none',
                        border: 'none',
                        borderBottom: activeTab === 'chat' ? '2px solid var(--primary)' : 'none',
                        color: activeTab === 'chat' ? 'var(--primary)' : 'var(--gray)',
                        fontWeight: activeTab === 'chat' ? '600' : '400',
                        cursor: 'pointer'
                      }}
                    >
                      <i className="fas fa-comments"></i> Secure Chat
                    </button>
                  </div>
                  
                  {activeTab === 'files' ? (
                    <>
                      <div className="file-upload-area" onClick={() => document.getElementById('file-upload').click()}>
                        <i className="fas fa-cloud-upload-alt"></i>
                        <h4>Upload Medical Files</h4>
                        <p>Drag & drop files here or click to browse</p>
                        <p style={{ fontSize: '0.8rem' }}>Supports: PDF, JPG, PNG (Max 25MB)</p>
                        <input type="file" id="file-upload" style={{ display: 'none' }} />
                        <button className="btn btn-outline" style={{ marginTop: '1rem' }}>
                          <i className="fas fa-upload"></i> Select Files
                        </button>
                      </div>
                      
                      <div className="card-header">
                        <h3>Shared Files</h3>
                        <div style={{ display: 'flex', gap: '0.5rem' }}>
                          <select style={{ padding: '0.5rem', borderRadius: '6px', border: '1px solid #E5E7EB' }}>
                            <option>Prescriptions</option>
                            <option>Test Results</option>
                            <option>All Files</option>
                          </select>
                          <button className="btn btn-primary" onClick={uploadFile}>
                            <i className="fas fa-plus"></i> New Prescription
                          </button>
                        </div>
                      </div>
                      
                      <div className="file-list">
                        {files.map(file => (
                          <div key={file.id} className="file-item">
                            <div className="file-icon">
                              <i className="fas fa-file-pdf"></i>
                            </div>
                            <div className="file-name">{file.name}</div>
                            <div className="file-meta">
                              <span>{file.date}</span>
                              <span>{file.size}</span>
                            </div>
                            <div className="file-actions">
                              <button className="btn btn-outline">
                                <i className="fas fa-eye"></i> View
                              </button>
                              <button className="btn btn-outline">
                                <i className="fas fa-download"></i> Download
                              </button>
                            </div>
                          </div>
                        ))}
                      </div>
                    </>
                  ) : (
                    <div className="chat-container" style={{ height: '400px', display: 'flex', flexDirection: 'column' }}>
                      <div className="chat-messages" style={{ flex: 1, overflowY: 'auto', padding: '1rem', background: '#F9FAFB', borderRadius: '8px', marginBottom: '1rem' }}>
                        <div style={{ display: 'flex', justifyContent: 'flex-end', marginBottom: '1rem' }}>
                          <div style={{ background: 'var(--primary)', color: 'white', padding: '0.75rem 1rem', borderRadius: '12px 12px 0 12px', maxWidth: '70%' }}>
                            Hello {currentPatient.name.split(' ')[0]}, how are you feeling today?
                          </div>
                        </div>
                        <div style={{ display: 'flex', justifyContent: 'flex-start', marginBottom: '1rem' }}>
                          <div style={{ background: 'white', padding: '0.75rem 1rem', borderRadius: '12px 12px 12px 0', maxWidth: '70%', boxShadow: '0 1px 3px rgba(0,0,0,0.1)' }}>
                            Much better after taking the medication, thank you Doctor!
                          </div>
                        </div>
                      </div>
                      <div className="chat-input" style={{ display: 'flex', gap: '0.5rem' }}>
                        <input
                          type="text"
                          value={message}
                          onChange={(e) => setMessage(e.target.value)}
                          placeholder="Type your message..."
                          style={{ flex: 1, padding: '0.85rem 1rem', borderRadius: '8px', border: '1px solid #E5E7EB' }}
                        />
                        <button 
                          className="btn btn-primary"
                          onClick={sendMessage}
                          style={{ padding: '0 1.5rem' }}
                        >
                          <i className="fas fa-paper-plane"></i>
                        </button>
                      </div>
                    </div>
                  )}
                </div>
              </>
            )}
          </div>
        </div>
      );
    }
    
    function PatientDashboard({ user }) {
      const [doctorId, setDoctorId] = React.useState('');
      const [currentDoctor, setCurrentDoctor] = React.useState(null);
      const [files, setFiles] = React.useState([]);
      const [activeTab, setActiveTab] = React.useState('files');
      
      React.useEffect(() => {
        // Simulate loading doctor and files
        setTimeout(() => {
          const doctor = fakeDatabase.users.find(u => u.role === 'doctor');
          if (doctor) {
            setCurrentDoctor(doctor);
            setFiles([
              {
                id: '1',
                name: 'Prescription_June2023.pdf',
                type: 'prescription',
                date: '2023-06-10',
                size: '1.2 MB',
                doctor: doctor.name
              },
              {
                id: '2',
                name: 'Blood_Test_Requirements.pdf',
                type: 'test',
                date: '2023-06-10',
                size: '0.8 MB',
                doctor: doctor.name
              }
            ]);
          }
        }, 500);
      }, []);
      
      const uploadFile = () => {
        const newFile = {
          id: Math.random().toString(36).substr(2, 9),
          name: 'My_Test_Results.pdf',
          type: 'report',
          date: new Date().toISOString().split('T')[0],
          size: '3.2 MB',
          doctor: currentDoctor.name
        };
        setFiles([...files, newFile]);
        alert('File uploaded successfully!');
      };
      
      return (
        <div className="dashboard">
          <div className="sidebar">
            <div className="sidebar-header">
              <svg width="40" height="40" fill="#4F46E5">
                <use xlinkHref="#icon-medical" />
              </svg>
              <h2>MediBhavan</h2>
            </div>
            
            <a href="#" className="nav-item active">
              <i className="fas fa-home"></i> Dashboard
            </a>
            <a href="#" className="nav-item">
              <i className="fas fa-file-medical"></i> My Records
            </a>
            <a href="#" className="nav-item">
              <i className="fas fa-calendar-alt"></i> Appointments
            </a>
            <a href="#" className="nav-item">
              <i className="fas fa-user-md"></i> Doctors
            </a>
            <a href="#" className="nav-item">
              <i className="fas fa-cog"></i> Settings
            </a>
            
            <div className="user-profile">
              <div className="user-avatar">
                {user.name.split(' ').map(n => n[0]).join('')}
              </div>
              <div className="user-info">
                <h4>{user.name}</h4>
                <p>{user.userId}</p>
              </div>
            </div>
          </div>
          
          <div className="main-content">
            <div className="header">
              <h2>Welcome, {user.name.split(' ')[0]}</h2>
              <div className="search-bar">
                <i className="fas fa-search"></i>
                <input type="text" placeholder="Search..." />
              </div>
            </div>
            
            {currentDoctor ? (
              <div className="card">
                <div className="patient-info">
                  <div className="patient-avatar" style={{ backgroundColor: '#4F46E5' }}>
                    {currentDoctor.name.split(' ').map(n => n[0]).join('')}
                  </div>
                  <div className="patient-details">
                    <h3>{currentDoctor.name}</h3>
                    <p>Your Primary Care Physician</p>
                  </div>
                </div>
                
                <div className="tabs" style={{ display: 'flex', borderBottom: '1px solid #E5E7EB', marginBottom: '1.5rem' }}>
                  <button 
                    className={`tab-btn ${activeTab === 'files' ? 'active' : ''}`}
                    onClick={() => setActiveTab('files')}
                    style={{
                      padding: '0.75rem 1.5rem',
                      background: 'none',
                      border: 'none',
                      borderBottom: activeTab === 'files' ? '2px solid var(--primary)' : 'none',
                      color: activeTab === 'files' ? 'var(--primary)' : 'var(--gray)',
                      fontWeight: activeTab === 'files' ? '600' : '400',
                      cursor: 'pointer'
                    }}
                  >
                    <i className="fas fa-file-medical"></i> My Medical Files
                  </button>
                  <button 
                    className={`tab-btn ${activeTab === 'chat' ? 'active' : ''}`}
                    onClick={() => setActiveTab('chat')}
                    style={{
                      padding: '0.75rem 1.5rem',
                      background: 'none',
                      border: 'none',
                      borderBottom: activeTab === 'chat' ? '2px solid var(--primary)' : 'none',
                      color: activeTab === 'chat' ? 'var(--primary)' : 'var(--gray)',
                      fontWeight: activeTab === 'chat' ? '600' : '400',
                      cursor: 'pointer'
                    }}
                  >
                    <i className="fas fa-comments"></i> Messages
                  </button>
                </div>
                
                {activeTab === 'files' ? (
                  <>
                    <div className="file-upload-area" onClick={() => document.getElementById('patient-file-upload').click()}>
                      <i className="fas fa-cloud-upload-alt"></i>
                      <h4>Upload Medical Reports</h4>
                      <p>Drag & drop files here or click to browse</p>
                      <p style={{ fontSize: '0.8rem' }}>Supports: PDF, JPG, PNG (Max 25MB)</p>
                      <input type="file" id="patient-file-upload" style={{ display: 'none' }} />
                      <button className="btn btn-outline" style={{ marginTop: '1rem' }} onClick={uploadFile}>
                        <i className="fas fa-upload"></i> Upload Reports
                      </button>
                    </div>
                    
                    <div className="file-list">
                      {files.map(file => (
                        <div key={file.id} className="file-item">
                          <div className="file-icon" style={{ 
                            backgroundColor: file.type === 'prescription' ? 'rgba(16, 185, 129, 0.1)' : 
                                          file.type === 'test' ? 'rgba(239, 68, 68, 0.1)' : 'rgba(99, 102, 241, 0.1)',
                            color: file.type === 'prescription' ? '#10B981' : 
                                  file.type === 'test' ? '#EF4444' : '#6366F1'
                          }}>
                            <i className={`fas ${
                              file.type === 'prescription' ? 'fa-prescription-bottle-alt' : 
                              file.type === 'test' ? 'fa-flask' : 'fa-file-medical'
                            }`}></i>
                          </div>
                          <div className="file-name">{file.name}</div>
                          <div className="file-meta">
                            <span>{file.date}</span>
                            <span>{file.size}</span>
                          </div>
                          <div className="file-actions">
                            <button className="btn btn-outline">
                              <i className="fas fa-eye"></i> View
                            </button>
                            <button className="btn btn-outline">
                              <i className="fas fa-download"></i> Download
                            </button>
                          </div>
                          {file.doctor && (
                            <div style={{ fontSize: '0.8rem', color: 'var(--gray)', marginTop: '0.5rem' }}>
                              From: {file.doctor}
                            </div>
                          )}
                        </div>
                      ))}
                    </div>
                  </>
                ) : (
                  <div className="chat-container" style={{ height: '400px', display: 'flex', flexDirection: 'column' }}>
                    <div className="chat-messages" style={{ flex: 1, overflowY: 'auto', padding: '1rem', background: '#F9FAFB', borderRadius: '8px', marginBottom: '1rem' }}>
                      <div style={{ display: 'flex', justifyContent: 'flex-start', marginBottom: '1rem' }}>
                        <div style={{ background: 'white', padding: '0.75rem 1rem', borderRadius: '12px 12px 12px 0', maxWidth: '70%', boxShadow: '0 1px 3px rgba(0,0,0,0.1)' }}>
                          Hello {user.name.split(' ')[0]}, how are you feeling today?
                        </div>
                      </div>
                      <div style={{ display: 'flex', justifyContent: 'flex-end', marginBottom: '1rem' }}>
                        <div style={{ background: 'var(--primary)', color: 'white', padding: '0.75rem 1rem', borderRadius: '12px 12px 0 12px', maxWidth: '70%' }}>
                          Much better after taking the medication, thank you Doctor!
                        </div>
                      </div>
                    </div>
                    <div className="chat-input" style={{ display: 'flex', gap: '0.5rem' }}>
                      <input
                        type="text"
                        placeholder="Type your message..."
                        style={{ flex: 1, padding: '0.85rem 1rem', borderRadius: '8px', border: '1px solid #E5E7EB' }}
                      />
                      <button 
                        className="btn btn-primary"
                        style={{ padding: '0 1.5rem' }}
                      >
                        <i className="fas fa-paper-plane"></i>
                      </button>
                    </div>
                  </div>
                )}
              </div>
            ) : (
              <div className="card" style={{ textAlign: 'center', padding: '2rem' }}>
                <i className="fas fa-user-md" style={{ fontSize: '3rem', color: 'var(--primary)', marginBottom: '1rem' }}></i>
                <h3>No Doctor Assigned</h3>
                <p style={{ marginBottom: '1.5rem' }}>Please enter your doctor's ID to connect</p>
                <div style={{ display: 'flex', gap: '0.5rem', maxWidth: '500px', margin: '0 auto' }}>
                  <input
                    type="text"
                    placeholder="Enter Doctor ID (Dr_...)"
                    value={doctorId}
                    onChange={(e) => setDoctorId(e.target.value)}
                    style={{ flex: 1, padding: '0.85rem 1rem', borderRadius: '8px', border: '1px solid #E5E7EB' }}
                  />
                  <button className="btn btn-primary">
                    <i className="fas fa-link"></i> Connect
                  </button>
                </div>
              </div>
            )}
          </div>
        </div>
      );
    }
    
    function App() {
      const [user, setUser] = React.useState(null);
      
      // Check if user is logged in (in a real app, this would check localStorage/session)
      React.useEffect(() => {
        // For demo purposes, auto-login as doctor or patient
        // Remove this in production
        const demoUser = fakeDatabase.users[0]; // Try changing index to 1 for patient view
        // setUser(demoUser);
      }, []);
      
      if (!user) {
        return <AuthPage setUser={setUser} />;
      }
      
      return user.role === 'doctor' 
        ? <DoctorDashboard user={user} /> 
        : <PatientDashboard user={user} />;
    }
    
    // Render the app
    ReactDOM.render(<App />, document.getElementById('root'));
  </script>
</body>
</html>

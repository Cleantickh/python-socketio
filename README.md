<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CleanTickPanel - Create Your Own SMM Panel</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }
        
        :root {
            --primary: #6c5ce7;
            --primary-dark: #5d4aec;
            --secondary: #00cec9;
            --dark: #2d3436;
            --light: #f7f7f7;
            --success: #00b894;
            --danger: #d63031;
            --warning: #fdcb6e;
        }
        
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #e4edf5 100%);
            color: var(--dark);
            min-height: 100vh;
            position: relative;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header Styles */
        header {
            background: white;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
        }
        
        .logo i {
            color: var(--secondary);
        }
        
        .nav-links {
            display: flex;
            gap: 30px;
        }
        
        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
            transition: all 0.3s ease;
        }
        
        .nav-links a:hover {
            color: var(--primary);
        }
        
        .nav-buttons {
            display: flex;
            gap: 15px;
        }
        
        .btn {
            padding: 10px 25px;
            border-radius: 50px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            border: none;
            font-size: 16px;
        }
        
        .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }
        
        .btn-outline:hover {
            background: var(--primary);
            color: white;
        }
        
        .btn-primary {
            background: var(--primary);
            color: white;
            box-shadow: 0 4px 15px rgba(108, 92, 231, 0.3);
        }
        
        .btn-primary:hover {
            background: var(--primary-dark);
            transform: translateY(-2px);
        }
        
        /* Hero Section */
        .hero {
            padding: 80px 0;
            display: flex;
            align-items: center;
            gap: 50px;
        }
        
        .hero-content {
            flex: 1;
        }
        
        .hero h1 {
            font-size: 3.5rem;
            line-height: 1.2;
            margin-bottom: 20px;
            color: var(--dark);
        }
        
        .hero h1 span {
            color: var(--primary);
        }
        
        .hero p {
            font-size: 1.2rem;
            color: #555;
            margin-bottom: 30px;
            max-width: 600px;
        }
        
        .hero-image {
            flex: 1;
            display: flex;
            justify-content: center;
        }
        
        .hero-image img {
            max-width: 100%;
            border-radius: 20px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
        }
        
        /* Features Section */
        .section-title {
            text-align: center;
            margin-bottom: 60px;
        }
        
        .section-title h2 {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: var(--dark);
        }
        
        .section-title p {
            color: #666;
            font-size: 1.1rem;
            max-width: 700px;
            margin: 0 auto;
        }
        
        .features {
            padding: 80px 0;
            background: white;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .feature-card {
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
        }
        
        .feature-icon {
            width: 70px;
            height: 70px;
            background: rgba(108, 92, 231, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }
        
        .feature-icon i {
            font-size: 30px;
            color: var(--primary);
        }
        
        .feature-card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: var(--dark);
        }
        
        .feature-card p {
            color: #666;
            line-height: 1.6;
        }
        
        /* How It Works */
        .how-it-works {
            padding: 80px 0;
        }
        
        .steps {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 20px;
            position: relative;
        }
        
        .steps::before {
            content: "";
            position: absolute;
            top: 50px;
            left: 10%;
            right: 10%;
            height: 4px;
            background: var(--secondary);
            z-index: 1;
        }
        
        .step {
            background: white;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            width: calc(25% - 20px);
            position: relative;
            z-index: 2;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
        }
        
        .step-number {
            width: 50px;
            height: 50px;
            background: var(--primary);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            font-weight: 700;
            margin: 0 auto 20px;
        }
        
        .step h3 {
            font-size: 1.3rem;
            margin-bottom: 15px;
            color: var(--dark);
        }
        
        .step p {
            color: #666;
        }
        
        /* Pricing Section */
        .pricing {
            padding: 80px 0;
            background: white;
        }
        
        .pricing-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .pricing-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
            position: relative;
        }
        
        .pricing-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
        }
        
        .pricing-header {
            background: var(--primary);
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        .pricing-header h3 {
            font-size: 1.5rem;
            margin-bottom: 10px;
        }
        
        .pricing-header .price {
            font-size: 3rem;
            font-weight: 700;
        }
        
        .pricing-header .price span {
            font-size: 1rem;
            font-weight: 400;
        }
        
        .pricing-body {
            padding: 30px;
        }
        
        .pricing-features {
            list-style: none;
            margin-bottom: 30px;
        }
        
        .pricing-features li {
            padding: 10px 0;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .pricing-features li i {
            color: var(--success);
        }
        
        .popular-badge {
            position: absolute;
            top: 20px;
            right: -30px;
            background: var(--warning);
            color: var(--dark);
            padding: 5px 30px;
            transform: rotate(45deg);
            font-weight: 700;
            font-size: 14px;
        }
        
        /* Registration Form */
        .registration {
            padding: 80px 0;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
        }
        
        .registration .section-title h2 {
            color: white;
        }
        
        .registration .section-title p {
            color: rgba(255, 255, 255, 0.8);
        }
        
        .form-container {
            background: white;
            border-radius: 20px;
            padding: 40px;
            max-width: 800px;
            margin: 0 auto;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
        }
        
        .form-row {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .form-group {
            flex: 1;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--dark);
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 15px;
            border: 2px solid #eee;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .form-control:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(108, 92, 231, 0.2);
        }
        
        .subdomain-group {
            display: flex;
            align-items: center;
        }
        
        .subdomain-group .form-control {
            border-radius: 10px 0 0 10px;
        }
        
        .subdomain-text {
            background: #f5f7fa;
            padding: 0 15px;
            height: 100%;
            display: flex;
            align-items: center;
            border-radius: 0 10px 10px 0;
            border: 2px solid #eee;
            border-left: none;
            color: #666;
        }
        
        .form-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 30px;
        }
        
        .terms {
            color: #666;
            font-size: 14px;
        }
        
        .terms a {
            color: var(--primary);
            text-decoration: none;
        }
        
        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            padding: 60px 0 30px;
        }
        
        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }
        
        .footer-col h3 {
            font-size: 1.3rem;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }
        
        .footer-col h3::after {
            content: "";
            position: absolute;
            bottom: 0;
            left: 0;
            width: 50px;
            height: 3px;
            background: var(--primary);
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 10px;
        }
        
        .footer-links a {
            color: #bbb;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .footer-links a:hover {
            color: var(--secondary);
            padding-left: 5px;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        
        .social-links a {
            width: 40px;
            height: 40px;
            background: #333;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .social-links a:hover {
            background: var(--primary);
            transform: translateY(-5px);
        }
        
        .copyright {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid #333;
            color: #999;
            font-size: 14px;
        }
        
        /* Responsive Design */
        @media (max-width: 992px) {
            .hero {
                flex-direction: column;
                text-align: center;
            }
            
            .hero p {
                margin: 0 auto 30px;
            }
            
            .steps::before {
                display: none;
            }
            
            .step {
                width: calc(50% - 20px);
                margin-bottom: 30px;
            }
        }
        
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .form-row {
                flex-direction: column;
                gap: 0;
            }
            
            .step {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <nav class="navbar">
                <div class="logo">
                    <i class="fas fa-crown"></i>
                    <span>CleanTickPanel</span>
                </div>
                <div class="nav-links">
                    <a href="#">Home</a>
                    <a href="#">Features</a>
                    <a href="#">Pricing</a>
                    <a href="#">How It Works</a>
                    <a href="#">Contact</a>
                </div>
                <div class="nav-buttons">
                    <button class="btn btn-outline">Login</button>
                    <button class="btn btn-primary">Register</button>
                </div>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Create Your Own <span>SMM Panel</span> in Minutes</h1>
                <p>CleanTickPanel is the ultimate platform to launch and manage your own social media marketing panel. Start your reselling business today with our powerful tools.</p>
                <div class="hero-buttons">
                    <button class="btn btn-primary">Get Started Now</button>
                    <button class="btn btn-outline">View Demo</button>
                </div>
            </div>
            <div class="hero-image">
                <img src="https://images.unsplash.com/photo-1551434678-e076c223a692?auto=format&fit=crop&w=600&h=400&q=80" alt="Dashboard Preview">
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section class="features">
        <div class="container">
            <div class="section-title">
                <h2>Powerful Features</h2>
                <p>Everything you need to start and grow your SMM reselling business</p>
            </div>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-layer-group"></i>
                    </div>
                    <h3>Multi-Tenant Architecture</h3>
                    <p>Host multiple SMM panels under a single system with complete data isolation and security.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-credit-card"></i>
                    </div>
                    <h3>Integrated Payments</h3>
                    <p>Accept payments seamlessly with Stripe, PayPal, and cryptocurrency support.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-chart-line"></i>
                    </div>
                    <h3>Analytics Dashboard</h3>
                    <p>Track your sales, revenue, and customer growth with beautiful, real-time dashboards.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-shield-alt"></i>
                    </div>
                    <h3>Enterprise Security</h3>
                    <p>Military-grade encryption, DDoS protection, and regular security audits.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-plug"></i>
                    </div>
                    <h3>API Integrations</h3>
                    <p>Connect with popular SMM services and automate your order processing.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-mobile-alt"></i>
                    </div>
                    <h3>Mobile Responsive</h3>
                    <p>Fully responsive design that works perfectly on all devices and screen sizes.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- How It Works -->
    <section class="how-it-works">
        <div class="container">
            <div class="section-title">
                <h2>How It Works</h2>
                <p>Launch your own SMM panel in just 4 simple steps</p>
            </div>
            <div class="steps">
                <div class="step">
                    <div class="step-number">1</div>
                    <h3>Create Account</h3>
                    <p>Register as a panel owner and set up your account.</p>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <h3>Customize Panel</h3>
                    <p>Personalize your panel with branding and services.</p>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <h3>Add Services</h3>
                    <p>Integrate SMM services or add your own offerings.</p>
                </div>
                <div class="step">
                    <div class="step-number">4</div>
                    <h3>Start Selling</h3>
                    <p>Launch your panel and start accepting orders.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Pricing Section -->
    <section class="pricing">
        <div class="container">
            <div class="section-title">
                <h2>Simple, Transparent Pricing</h2>
                <p>Choose the plan that works best for your business</p>
            </div>
            <div class="pricing-grid">
                <div class="pricing-card">
                    <div class="pricing-header">
                        <h3>Starter</h3>
                        <div class="price">$49<span>/month</span></div>
                    </div>
                    <div class="pricing-body">
                        <ul class="pricing-features">
                            <li><i class="fas fa-check"></i> 1 Panel</li>
                            <li><i class="fas fa-check"></i> 100 Monthly Orders</li>
                            <li><i class="fas fa-check"></i> Basic Support</li>
                            <li><i class="fas fa-times"></i> API Access</li>
                            <li><i class="fas fa-times"></i> White Label</li>
                        </ul>
                        <button class="btn btn-outline" style="width:100%">Get Started</button>
                    </div>
                </div>
                <div class="pricing-card">
                    <div class="popular-badge">POPULAR</div>
                    <div class="pricing-header" style="background: var(--secondary);">
                        <h3>Professional</h3>
                        <div class="price">$99<span>/month</span></div>
                    </div>
                    <div class="pricing-body">
                        <ul class="pricing-features">
                            <li><i class="fas fa-check"></i> 3 Panels</li>
                            <li><i class="fas fa-check"></i> 500 Monthly Orders</li>
                            <li><i class="fas fa-check"></i> Priority Support</li>
                            <li><i class="fas fa-check"></i> API Access</li>
                            <li><i class="fas fa-times"></i> White Label</li>
                        </ul>
                        <button class="btn btn-primary" style="width:100%">Get Started</button>
                    </div>
                </div>
                <div class="pricing-card">
                    <div class="pricing-header">
                        <h3>Enterprise</h3>
                        <div class="price">$199<span>/month</span></div>
                    </div>
                    <div class="pricing-body">
                        <ul class="pricing-features">
                            <li><i class="fas fa-check"></i> Unlimited Panels</li>
                            <li><i class="fas fa-check"></i> Unlimited Orders</li>
                            <li><i class="fas fa-check"></i> 24/7 Support</li>
                            <li><i class="fas fa-check"></i> API Access</li>
                            <li><i class="fas fa-check"></i> White Label</li>
                        </ul>
                        <button class="btn btn-outline" style="width:100%">Get Started</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Registration Section -->
    <section class="registration">
        <div class="container">
            <div class="section-title">
                <h2>Create Your Panel Today</h2>
                <p>Join thousands of successful SMM businesses using our platform</p>
            </div>
            <div class="form-container">
                <form id="registrationForm">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="panelName">Panel Name</label>
                            <input type="text" id="panelName" class="form-control" placeholder="Enter your panel name" required>
                        </div>
                        <div class="form-group">
                            <label for="adminName">Admin Name</label>
                            <input type="text" id="adminName" class="form-control" placeholder="Your full name" required>
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label for="email">Email Address</label>
                            <input type="email" id="email" class="form-control" placeholder="your@email.com" required>
                        </div>
                        <div class="form-group">
                            <label for="password">Password</label>
                            <input type="password" id="password" class="form-control" placeholder="Create a strong password" required>
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label for="subdomain">Subdomain</label>
                            <div class="subdomain-group">
                                <input type="text" id="subdomain" class="form-control" placeholder="yourname" required>
                                <div class="subdomain-text">.cleantickpanel.com</div>
                            </div>
                        </div>
                        <div class="form-group">
                            <label for="plan">Select Plan</label>
                            <select id="plan" class="form-control" required>
                                <option value="">Choose a plan</option>
                                <option value="starter">Starter - $49/month</option>
                                <option value="professional">Professional - $99/month</option>
                                <option value="enterprise">Enterprise - $199/month</option>
                            </select>
                        </div>
                    </div>
                    <div class="form-footer">
                        <div class="terms">
                            <input type="checkbox" id="terms" required>
                            <label for="terms">I agree to the <a href="#">Terms of Service</a> and <a href="#">Privacy Policy</a></label>
                        </div>
                        <button type="submit" class="btn btn-primary">Create My Panel</button>
                    </div>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-grid">
                <div class="footer-col">
                    <h3>CleanTickPanel</h3>
                    <p>The all-in-one platform to launch and manage your own SMM panel business. Trusted by thousands of resellers worldwide.</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-facebook-f"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-linkedin-in"></i></a>
                    </div>
                </div>
                <div class="footer-col">
                    <h3>Quick Links</h3>
                    <ul class="footer-links">
                        <li><a href="#">Home</a></li>
                        <li><a href="#">Features</a></li>
                        <li><a href="#">Pricing</a></li>
                        <li><a href="#">How It Works</a></li>
                        <li><a href="#">Contact Us</a></li>
                    </ul>
                </div>
                <div class="footer-col">
                    <h3>Resources</h3>
                    <ul class="footer-links">
                        <li><a href="#">Documentation</a></li>
                        <li><a href="#">API Reference</a></li>
                        <li><a href="#">Blog</a></li>
                        <li><a href="#">FAQs</a></li>
                        <li><a href="#">Support Center</a></li>
                    </ul>
                </div>
                <div class="footer-col">
                    <h3>Contact Us</h3>
                    <ul class="footer-links">
                        <li><i class="fas fa-envelope"></i> support@cleantickpanel.com</li>
                        <li><i class="fas fa-phone"></i> +1 (555) 123-4567</li>
                        <li><i class="fas fa-map-marker-alt"></i> 123 Business Ave, Suite 100<br>New York, NY 10001</li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                &copy; 2023 CleanTickPanel. All rights reserved.
            </div>
        </div>
    </footer>

    <script>
        // Form submission handling
        document.getElementById('registrationForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form values
            const panelName = document.getElementById('panelName').value;
            const subdomain = document.getElementById('subdomain').value;
            const adminName = document.getElementById('adminName').value;
            const email = document.getElementById('email').value;
            const plan = document.getElementById('plan').value;
            
            // Show success message
            alert(`Your panel "${panelName}" has been created successfully!\n\nAdmin URL: https://${subdomain}.cleantickpanel.com\n\nWe've sent setup instructions to ${email}.`);
            
            // Reset form
            this.reset();
        });
        
        // Animate elements on scroll
        document.addEventListener('DOMContentLoaded', function() {
            const animateOnScroll = function() {
                const elements = document.querySelectorAll('.feature-card, .step, .pricing-card');
                
                elements.forEach(element => {
                    const position = element.getBoundingClientRect();
                    
                    // If element is in viewport
                    if(position.top < window.innerHeight * 0.75) {
                        element.style.opacity = "1";
                        element.style.transform = "translateY(0)";
                    }
                });
            };
            
            // Initial check
            animateOnScroll();
            
            // Check on scroll
            window.addEventListener('scroll', animateOnScroll);
            
            // Set initial styles for animation
            document.querySelectorAll('.feature-card, .step, .pricing-card').forEach(element => {
                element.style.opacity = "0";
                element.style.transform = "translateY(20px)";
                element.style.transition = "all 0.5s ease";
            });
        });
    </script>
</body>
</html>
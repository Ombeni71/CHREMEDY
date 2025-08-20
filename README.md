<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Freedom Mark International - Access More. Waste Less.</title>
    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
    <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap" async defer></script>
    <style>
        :root {
            --primary: #1A5D1A;
            --secondary: #E8B753;
            --light: #F8F9FA;
            --dark: #212529;
            --gray: #6c757d;
            --success: #28a745;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f9f9f9;
            color: var(--dark);
            line-height: 1.6;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        header {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
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
            font-size: 32px;
        }
        
        .nav-links {
            display: flex;
            gap: 30px;
        }
        
        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .nav-links a:hover {
            color: var(--primary);
        }
        
        .auth-buttons {
            display: flex;
            gap: 15px;
        }
        
        .btn {
            padding: 10px 20px;
            border-radius: 30px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
            text-align: center;
        }
        
        .btn-outline {
            border: 2px solid var(--primary);
            color: var(--primary);
            background: transparent;
        }
        
        .btn-outline:hover {
            background: var(--primary);
            color: white;
        }
        
        .btn-primary {
            background: var(--primary);
            color: white;
            border: 2px solid var(--primary);
        }
        
        .btn-primary:hover {
            background: #144a14;
            border-color: #144a14;
        }
        
        .hero {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 80px 0;
            text-align: center;
        }
        
        .hero h1 {
            font-size: 48px;
            color: var(--primary);
            margin-bottom: 20px;
            line-height: 1.2;
        }
        
        .hero p {
            font-size: 20px;
            color: var(--gray);
            max-width: 800px;
            margin: 0 auto 40px;
        }
        
        .hero-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 50px;
        }
        
        .app-preview {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            margin: 50px 0;
        }
        
        .phone-frame {
            width: 280px;
            height: 580px;
            background: var(--dark);
            border-radius: 40px;
            padding: 20px;
            position: relative;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }
        
        .phone-notch {
            width: 120px;
            height: 20px;
            background: #111;
            border-radius: 10px;
            margin: 0 auto 20px;
        }
        
        .phone-screen {
            width: 100%;
            height: 100%;
            background: white;
            border-radius: 20px;
            overflow: hidden;
            position: relative;
        }
        
        .phone-screen img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .mission {
            background: white;
            padding: 80px 0;
            text-align: center;
        }
        
        .section-title {
            font-size: 36px;
            color: var(--primary);
            margin-bottom: 20px;
        }
        
        .section-subtitle {
            font-size: 18px;
            color: var(--gray);
            max-width: 800px;
            margin: 0 auto 50px;
        }
        
        .steps {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            margin: 50px 0;
        }
        
        .step {
            background: white;
            border-radius: 15px;
            padding: 30px;
            width: 300px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            text-align: center;
            transition: transform 0.3s;
        }
        
        .step:hover {
            transform: translateY(-10px);
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
            font-size: 24px;
            font-weight: 700;
            margin: 0 auto 20px;
        }
        
        .step h3 {
            font-size: 24px;
            margin-bottom: 15px;
            color: var(--primary);
        }
        
        .step p {
            color: var(--gray);
        }
        
        .step-image {
            width: 100%;
            height: 200px;
            border-radius: 10px;
            margin: 20px 0;
            overflow: hidden;
        }
        
        .step-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .deals-section {
            background: linear-gradient(135deg, var(--primary) 0%, #2d8a2d 100%);
            color: white;
            padding: 80px 0;
            text-align: center;
        }
        
        .deals-section .section-title {
            color: white;
        }
        
        .deals-section .section-subtitle {
            color: rgba(255,255,255,0.9);
        }
        
        .deals-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 50px 0;
        }
        
        .deal-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: transform 0.3s;
        }
        
        .deal-card:hover {
            transform: translateY(-10px);
        }
        
        .deal-image {
            height: 180px;
            overflow: hidden;
        }
        
        .deal-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .deal-content {
            padding: 20px;
            text-align: left;
        }
        
        .deal-title {
            font-size: 18px;
            font-weight: 600;
            color: var(--dark);
            margin-bottom: 10px;
        }
        
        .deal-price {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 15px;
        }
        
        .current-price {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
        }
        
        .original-price {
            font-size: 18px;
            color: var(--gray);
            text-decoration: line-through;
        }
        
        .discount {
            background: var(--secondary);
            color: var(--dark);
            padding: 3px 8px;
            border-radius: 5px;
            font-size: 14px;
            font-weight: 600;
        }
        
        .location {
            display: flex;
            align-items: center;
            gap: 5px;
            color: var(--gray);
            font-size: 14px;
            margin-bottom: 15px;
        }
        
        .btn-deal {
            width: 100%;
            padding: 12px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .btn-deal:hover {
            background: #144a14;
        }
        
        .map-section {
            padding: 80px 0;
            text-align: center;
        }
        
        .map-container {
            height: 500px;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            margin: 50px 0;
        }
        
        #map {
            height: 100%;
            width: 100%;
        }
        
        .impact {
            background: white;
            padding: 80px 0;
            text-align: center;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin: 50px 0;
        }
        
        .stat-card {
            padding: 30px;
            border-radius: 15px;
            background: var(--light);
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
        }
        
        .stat-number {
            font-size: 48px;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 10px;
        }
        
        .stat-label {
            font-size: 18px;
            color: var(--gray);
        }
        
        .vendors-section {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 80px 0;
            text-align: center;
        }
        
        .vendor-portal {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            padding: 40px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }
        
        .login-form {
            max-width: 400px;
            margin: 30px auto;
            text-align: left;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--dark);
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        footer {
            background: var(--dark);
            color: white;
            padding: 60px 0 30px;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }
        
        .footer-column h3 {
            font-size: 18px;
            margin-bottom: 20px;
            color: var(--secondary);
        }
        
        .footer-column ul {
            list-style: none;
        }
        
        .footer-column ul li {
            margin-bottom: 10px;
        }
        
        .footer-column ul li a {
            color: #ddd;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-column ul li a:hover {
            color: var(--secondary);
        }
        
        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .contact-info div {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .copyright {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid #444;
            color: #aaa;
            font-size: 14px;
        }
        
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 36px;
            }
            
            .hero p {
                font-size: 18px;
            }
            
            .app-preview {
                flex-direction: column;
                align-items: center;
            }
            
            .steps {
                flex-direction: column;
                align-items: center;
            }
            
            .step {
                width: 100%;
                max-width: 350px;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <nav class="navbar">
                <div class="logo">
                    <i class="fas fa-globe"></i>
                    <span>Freedom Mark International</span>
                </div>
                <div class="nav-links">
                    <a href="#how-it-works">How It Works</a>
                    <a href="#deals">Deals</a>
                    <a href="#map">Locations</a>
                    <a href="#impact">Impact</a>
                </div>
                <div class="auth-buttons">
                    <a href="#vendor-login" class="btn btn-outline">Vendor Login</a>
                    <a href="#download" class="btn btn-primary">Download App</a>
                </div>
            </nav>
        </div>
    </header>

    <section class="hero">
        <div class="container">
            <h1>The app for life's best kept deals</h1>
            <p>Fresh produce, essential goods, and more at up to 70% off. With the Freedom Mark International app, find deals at your local stores and enjoy more for less.</p>
            <div class="hero-buttons">
                <a href="#download" class="btn btn-primary">Download the App</a>
                <a href="#vendor-login" class="btn btn-outline">Become a Vendor</a>
            </div>
            <div class="app-preview">
                <div class="phone-frame">
                    <div class="phone-notch"></div>
                    <div class="phone-screen">
                        <img src="https://cdn.sanity.io/images/7topkt8d/production/9bf1239359b3e375ed431176a1ad38ac0b3d6232-424x810.png?auto=format&fit=max&w=640" alt="Freedom Mark App Download">
                    </div>
                </div>
                <div class="phone-frame">
                    <div class="phone-notch"></div>
                    <div class="phone-screen">
                        <img src="https://cdn.sanity.io/images/7topkt8d/production/fe989648f3efa9e318fc2e6c781eb33031d32ab8-531x627.png?auto=format&fit=max&w=640" alt="Freedom Mark App Deals">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="mission">
        <div class="container">
            <h2 class="section-title">On a mission to empower communities not landfills</h2>
            <p class="section-subtitle">Join Freedom Mark shoppers saving thousands of dollars a year on essential goods, while also saving quality items from going to waste.</p>
            
            <div class="steps">
                <div class="step">
                    <div class="step-number">1</div>
                    <h3>Download the App</h3>
                    <p>Get the Freedom Mark International app for iOS or Android</p>
                    <div class="step-image">
                        <img src="https://cdn.sanity.io/images/7topkt8d/production/c5b9a02646a2b561fd4e96c60878a53515b0cc0f-531x627.png?auto=format&fit=max&w=640" alt="App Store">
                    </div>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <h3>Browse for Deals</h3>
                    <p>Find local deals for up to 70% off and check out in the app</p>
                    <div class="step-image">
                        <img src="https://cdn.sanity.io/images/7topkt8d/production/fe989648f3efa9e318fc2e6c781eb33031d32ab8-531x627.png?auto=format&fit=max&w=640" alt="Browse Deals">
                    </div>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <h3>Pick Up or Deliver</h3>
                    <p>Pick up your haul from your local store or choose delivery</p>
                    <div class="step-image">
                        <img src="https://cdn.sanity.io/images/7topkt8d/production/184c685bf26e3ac0990994d824c23dd2938f005e-750x821.png?auto=format&fit=max&w=640" alt="Pick Up">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="deals-section" id="deals">
        <div class="container">
            <h2 class="section-title">Today's Best Deals</h2>
            <p class="section-subtitle">Discover amazing discounts on fresh produce, household essentials, personal care items, and more</p>
            
            <div class="deals-grid">
                <div class="deal-card">
                    <div class="deal-image">
                        <img src="https://placehold.co/300x200/FF9900/FFFFFF?text=Organic+Oranges" alt="Organic Oranges">
                    </div>
                    <div class="deal-content">
                        <h3 class="deal-title">Organic Navel Oranges</h3>
                        <div class="deal-price">
                            <span class="current-price">$2.99</span>
                            <span class="original-price">$5.99</span>
                            <span class="discount">50% OFF</span>
                        </div>
                        <div class="location">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>Whole Foods Market - Downtown</span>
                        </div>
                        <button class="btn-deal">Add to Cart</button>
                    </div>
                </div>
                
                <div class="deal-card">
                    <div class="deal-image">
                        <img src="https://placehold.co/300x200/4CAF50/FFFFFF?text=Fresh+Salmon" alt="Fresh Salmon">
                    </div>
                    <div class="deal-content">
                        <h3 class="deal-title">Wild Caught Salmon Fillet</h3>
                        <div class="deal-price">
                            <span class="current-price">$8.99</span>
                            <span class="original-price">$17.99</span>
                            <span class="discount">50% OFF</span>
                        </div>
                        <div class="location">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>Trader Joe's - Midtown</span>
                        </div>
                        <button class="btn-deal">Add to Cart</button>
                    </div>
                </div>
                
                <div class="deal-card">
                    <div class="deal-image">
                        <img src="https://placehold.co/300x200/9C27B0/FFFFFF?text=Toilet+Paper" alt="Toilet Paper">
                    </div>
                    <div class="deal-content">
                        <h3 class="deal-title">Premium Toilet Paper (12-pack)</h3>
                        <div class="deal-price">
                            <span class="current-price">$6.99</span>
                            <span class="original-price">$15.99</span>
                            <span class="discount">56% OFF</span>
                        </div>
                        <div class="location">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>Target - Northside</span>
                        </div>
                        <button class="btn-deal">Add to Cart</button>
                    </div>
                </div>
                
                <div class="deal-card">
                    <div class="deal-image">
                        <img src="https://placehold.co/300x200/FF5722/FFFFFF?text=Shampoo" alt="Shampoo">
                    </div>
                    <div class="deal-content">
                        <h3 class="deal-title">Organic Shampoo & Conditioner</h3>
                        <div class="deal-price">
                            <span class="current-price">$4.99</span>
                            <span class="original-price">$12.99</span>
                            <span class="discount">61% OFF</span>
                        </div>
                        <div class="location">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>Walgreens - East End</span>
                        </div>
                        <button class="btn-deal">Add to Cart</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="map-section" id="map">
        <div class="container">
            <h2 class="section-title">Find Us at Your Favorite Retailers</h2>
            <p class="section-subtitle">We partner with stores across the USA and around the world to bring you the best deals on quality goods</p>
            
            <div class="map-container">
                <div id="map"></div>
            </div>
        </div>
    </section>

    <section class="impact">
        <div class="container">
            <h2 class="section-title">Our Global Impact</h2>
            <p class="section-subtitle">Together, we're making a difference in communities and the environment</p>
            
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-number">5M+</div>
                    <div class="stat-label">Items Saved from Landfills</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">$25M+</div>
                    <div class="stat-label">Saved by Shoppers</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">15K+</div>
                    <div class="stat-label">Partner Stores Worldwide</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">70%</div>
                    <div class="stat-label">Average Discount</div>
                </div>
            </div>
        </div>
    </section>

    <section class="vendors-section">
        <div class="container">
            <h2 class="section-title">Vendor Sign-In Portal</h2>
            <p class="section-subtitle">Manage your surplus inventory, set discounts, and connect with customers through our vendor portal</p>
            
            <div class="vendor-portal">
                <div id="vendor-login">
                    <h3 style="color: var(--primary); margin-bottom: 20px;">Vendor Login</h3>
                    <div class="login-form">
                        <div class="form-group">
                            <label for="email">Email Address</label>
                            <input type="email" class="form-control" id="email" placeholder="Enter your email">
                        </div>
                        <div class="form-group">
                            <label for="password">Password</label>
                            <input type="password" class="form-control" id="password" placeholder="Enter your password">
                        </div>
                        <button class="btn btn-primary" style="width: 100%;">Sign In</button>
                        <p style="text-align: center; margin-top: 15px;">
                            <a href="#" style="color: var(--primary);">Forgot password?</a>
                        </p>
                    </div>
                    <div style="text-align: center; margin-top: 30px;">
                        <p>Don't have an account?</p>
                        <a href="#" class="btn btn-outline">Become a Vendor</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>Company</h3>
                    <ul>
                        <li><a href="#">About Us</a></li>
                        <li><a href="#">Our Mission</a></li>
                        <li><a href="#">Careers</a></li>
                        <li><a href="#">Press</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Support</h3>
                    <ul>
                        <li><a href="#">Help Center</a></li>
                        <li><a href="#">Contact Us</a></li>
                        <li><a href="#">Report an Issue</a></li>
                        <li><a href="#">App Feedback</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Legal</h3>
                    <ul>
                        <li><a href="#">Terms of Service</a></li>
                        <li><a href="#">Privacy Policy</a></li>
                        <li><a href="#">Refund Policy</a></li>
                        <li><a href="#">Vendor Agreement</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Contact Us</h3>
                    <div class="contact-info">
                        <div>
                            <i class="fas fa-envelope"></i>
                            <span>info@freedommarkint.com</span>
                        </div>
                        <div>
                            <i class="fas fa-globe"></i>
                            <span>www.freedommarkint.com</span>
                        </div>
                        <div>
                            <i class="fas fa-phone"></i>
                            <span>317-201-4808</span>
                        </div>
                        <div>
                            <i class="fas fa-map-marker-alt"></i>
                            <span>Indianapolis, IN, USA</span>
                        </div>
                    </div>
                </div>
            </div>
            <div class="copyright">
                &copy; 2024 Freedom Mark International. All rights reserved. | Empowering communities, reducing waste worldwide.
            </div>
        </div>
    </footer>

    <script>
        // Initialize Google Map
        function initMap() {
            const locations = [
                { name: "Whole Foods Market - Downtown", lat: 39.7684, lng: -86.1581, deals: 24 },
                { name: "Trader Joe's - Midtown", lat: 39.7814, lng: -86.1492, deals: 18 },
                { name: "Target - Northside", lat: 39.8597, lng: -86.2122, deals: 32 },
                { name: "Walgreens - East End", lat: 39.7300, lng: -86.1000, deals: 15 },
                { name: "Kroger - Southside", lat: 39.6923, lng: -86.1958, deals: 28 }
            ];
            
            const map = new google.maps.Map(document.getElementById("map"), {
                zoom: 11,
                center: { lat: 39.7684, lng: -86.1581 },
                styles: [
                    {
                        "featureType": "water",
                        "elementType": "geometry",
                        "stylers": [{ "color": "#e9e9e9" }, { "lightness": 17 }]
                    },
                    {
                        "featureType": "landscape",
                        "elementType": "geometry",
                        "stylers": [{ "color": "#f5f5f5" }, { "lightness": 20 }]
                    }
                ],
                mapTypeControl: false,
                fullscreenControl: false
            });
            
            const bounds = new google.maps.LatLngBounds();
            
            locations.forEach(location => {
                const marker = new google.maps.Marker({
                    position: { lat: location.lat, lng: location.lng },
                    map: map,
                    title: location.name
                });
                
                const infoWindow = new google.maps.InfoWindow({
                    content: `<div style="font-family: Arial, sans-serif; max-width: 200px;">
                        <strong>${location.name}</strong><br>
                        ${location.deals} active deals<br>
                        <em>Click to view deals</em>
                    </div>`
                });
                
                marker.addListener("click", () => {
                    infoWindow.open(map, marker);
                });
                
                bounds.extend(marker.position);
            });
            
            map.fitBounds(bounds);
        }
        
        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    window.scrollTo({
                        top: target.offsetTop - 100,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // Simple form interaction
        document.querySelector('.btn-deal').addEventListener('click', function() {
            alert('Item added to cart! Download the Freedom Mark International app to complete your purchase.');
        });
        
        document.querySelector('.btn-primary').addEventListener('click', function() {
            alert('Thank you for your interest! The Freedom Mark International app is available on the App Store and Google Play.');
        });
    </script>
</body>
</html>

# climtech-refrigeration-site<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Clim Tech Réfrigération - Froid Industriel Strasbourg & Alsace</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&family=Roboto:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        /* Styles généraux - Thème sombre */
        :root {
            --primary: #00b4d8;
            --secondary: #48cae4;
            --accent: #ff9e00;
            --dark: #0d1b2a;
            --darker: #070d14;
            --gray-dark: #1b263b;
            --gray: #415a77;
            --gray-light: #778da9;
            --light: #e0e1dd;
            --emergency: #ff5a5f;
            --success: #06d6a0;
            --warning: #ffd166;
            --ice-blue: #a8dadc;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            line-height: 1.6;
            color: var(--light);
            background-color: var(--dark);
            font-family: 'Roboto', sans-serif;
            position: relative;
            overflow-x: hidden;
        }
        
        /* Bâtiment sphérique en arrière-plan */
        .background-sphere {
            position: fixed;
            top: 50%;
            right: -200px;
            transform: translateY(-50%);
            width: 600px;
            height: 600px;
            z-index: -1;
            opacity: 0.15;
            pointer-events: none;
        }
        
        .sphere {
            position: absolute;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 30% 30%, var(--primary) 0%, transparent 70%),
                        radial-gradient(circle at 70% 70%, var(--secondary) 0%, transparent 70%);
            border-radius: 50%;
            animation: rotateSphere 60s infinite linear;
            box-shadow: 
                inset 0 0 100px rgba(0, 180, 216, 0.3),
                0 0 150px rgba(0, 180, 216, 0.2);
        }
        
        .sphere::before {
            content: '';
            position: absolute;
            width: 90%;
            height: 90%;
            top: 5%;
            left: 5%;
            background: radial-gradient(circle at 40% 40%, transparent 30%, rgba(0, 180, 216, 0.1) 70%);
            border-radius: 50%;
            filter: blur(20px);
        }
        
        .sphere::after {
            content: '';
            position: absolute;
            width: 80%;
            height: 80%;
            top: 10%;
            left: 10%;
            background: radial-gradient(circle at 60% 60%, transparent 40%, rgba(72, 202, 228, 0.05) 60%);
            border-radius: 50%;
            filter: blur(30px);
        }
        
        /* Éléments structuraux de la sphère */
        .sphere-structure {
            position: absolute;
            width: 100%;
            height: 100%;
            border-radius: 50%;
        }
        
        .sphere-door {
            position: absolute;
            width: 120px;
            height: 200px;
            background: linear-gradient(90deg, rgba(0, 0, 0, 0.3) 0%, rgba(168, 218, 220, 0.1) 100%);
            border-radius: 60px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(45deg);
            box-shadow: 
                inset 0 0 30px rgba(0, 0, 0, 0.5),
                0 0 40px rgba(168, 218, 220, 0.2);
        }
        
        .sphere-light {
            position: absolute;
            width: 40px;
            height: 40px;
            background: radial-gradient(circle, var(--ice-blue) 0%, transparent 70%);
            border-radius: 50%;
            top: 20%;
            left: 20%;
            animation: pulseLight 4s infinite alternate;
            box-shadow: 0 0 30px var(--ice-blue);
        }
        
        .sphere-light:nth-child(2) {
            top: 70%;
            left: 70%;
            animation-delay: 1s;
        }
        
        @keyframes rotateSphere {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }
        
        @keyframes pulseLight {
            0% {
                opacity: 0.3;
                box-shadow: 0 0 20px var(--ice-blue);
            }
            100% {
                opacity: 0.7;
                box-shadow: 0 0 40px var(--ice-blue);
            }
        }
        
        /* Logo Cube 3D */
        .logo-3d-container {
            perspective: 1000px;
            width: 60px;
            height: 60px;
            margin-right: 15px;
        }
        
        .cube-3d {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            animation: rotateCube 20s infinite linear;
            transform-origin: center center;
        }
        
        .cube-face {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border: 2px solid rgba(255, 255, 255, 0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 
                inset 0 0 20px rgba(255, 255, 255, 0.1),
                0 0 30px rgba(0, 180, 216, 0.3);
        }
        
        .cube-face::before {
            content: "❄";
            font-size: 24px;
            color: var(--dark);
            font-weight: bold;
        }
        
        .cube-front {
            transform: translateZ(30px);
            background: linear-gradient(135deg, var(--primary), #0096c7);
        }
        
        .cube-back {
            transform: translateZ(-30px) rotateY(180deg);
            background: linear-gradient(135deg, var(--secondary), #48cae4);
        }
        
        .cube-right {
            transform: rotateY(90deg) translateZ(30px);
            background: linear-gradient(135deg, #0096c7, #0077b6);
        }
        
        .cube-left {
            transform: rotateY(-90deg) translateZ(30px);
            background: linear-gradient(135deg, #0077b6, #0096c7);
        }
        
        .cube-top {
            transform: rotateX(90deg) translateZ(30px);
            background: linear-gradient(135deg, #48cae4, #0096c7);
        }
        
        .cube-bottom {
            transform: rotateX(-90deg) translateZ(30px);
            background: linear-gradient(135deg, #0096c7, #48cae4);
        }
        
        @keyframes rotateCube {
            0% {
                transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
            }
            25% {
                transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg);
            }
            50% {
                transform: rotateX(180deg) rotateY(180deg) rotateZ(90deg);
            }
            75% {
                transform: rotateX(270deg) rotateY(270deg) rotateZ(180deg);
            }
            100% {
                transform: rotateX(360deg) rotateY(360deg) rotateZ(270deg);
            }
        }
        
        h1, h2, h3, h4 {
            font-family: 'Montserrat', sans-serif;
            font-weight: 600;
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
            position: relative;
            z-index: 1;
        }
        
        section {
            padding: 80px 0;
            position: relative;
            z-index: 1;
        }
        
        .btn {
            display: inline-block;
            padding: 14px 32px;
            background-color: var(--primary);
            color: var(--dark);
            text-decoration: none;
            border-radius: 8px;
            font-weight: 600;
            font-family: 'Montserrat', sans-serif;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .btn:hover {
            background-color: #0096c7;
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 180, 216, 0.3);
        }
        
        .btn-emergency {
            background-color: var(--emergency);
            color: white;
            animation: pulse 2s infinite;
            font-size: 16px;
            padding: 16px 40px;
        }
        
        .btn-emergency:hover {
            background-color: #ff4757;
            box-shadow: 0 8px 25px rgba(255, 90, 95, 0.4);
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(255, 90, 95, 0.7); }
            70% { box-shadow: 0 0 0 12px rgba(255, 90, 95, 0); }
            100% { box-shadow: 0 0 0 0 rgba(255, 90, 95, 0); }
        }
        
        /* Header */
        header {
            background-color: rgba(7, 13, 20, 0.95);
            box-shadow: 0 4px 20px rgba(0,0,0,0.6);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            border-bottom: 3px solid var(--primary);
            backdrop-filter: blur(10px);
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }
        
        .logo-container {
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .logo-text {
            font-size: 26px;
            font-weight: 700;
            color: var(--light);
            font-family: 'Montserrat', sans-serif;
        }
        
        .logo-text span {
            color: var(--primary);
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 30px;
        }
        
        nav ul li a {
            text-decoration: none;
            color: var(--light);
            font-weight: 500;
            font-family: 'Montserrat', sans-serif;
            transition: all 0.3s;
            position: relative;
            font-size: 15px;
        }
        
        nav ul li a:hover {
            color: var(--primary);
        }
        
        nav ul li a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background: var(--primary);
            left: 0;
            bottom: -8px;
            transition: width 0.3s;
        }
        
        nav ul li a:hover::after {
            width: 100%;
        }
        
        .mobile-menu {
            display: none;
            font-size: 28px;
            cursor: pointer;
            color: var(--light);
        }
        
        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(13, 27, 42, 0.85), rgba(13, 27, 42, 0.9)), url('https://images.unsplash.com/photo-1558618666-fcd25c85cd64?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            text-align: center;
            padding: 200px 0 100px;
            margin-top: 70px;
            position: relative;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 80% 50%, rgba(0, 180, 216, 0.1) 0%, transparent 50%);
            pointer-events: none;
        }
        
        .hero h1 {
            font-size: 52px;
            margin-bottom: 25px;
            color: var(--light);
            text-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
        }
        
        .hero h1 span {
            color: var(--primary);
        }
        
        .hero p {
            font-size: 20px;
            max-width: 800px;
            margin: 0 auto 40px;
            color: var(--light);
            font-weight: 300;
        }
        
        /* Services */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 35px;
            margin-top: 50px;
        }
        
        .service-card {
            background: rgba(27, 38, 59, 0.8);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 12px 35px rgba(0,0,0,0.4);
            transition: all 0.3s;
            border: 1px solid var(--gray);
            backdrop-filter: blur(5px);
        }
        
        .service-card:hover {
            transform: translateY(-12px);
            box-shadow: 0 20px 40px rgba(0, 180, 216, 0.25);
            border-color: var(--primary);
        }
        
        .service-img {
            height: 220px;
            background-size: cover;
            background-position: center;
        }
        
        .service-content {
            padding: 25px;
        }
        
        /* Galerie - Images techniques uniquement */
        .gallery-section {
            background-color: rgba(7, 13, 20, 0.9);
            border-top: 2px solid var(--gray);
            border-bottom: 2px solid var(--gray);
            backdrop-filter: blur(5px);
        }
        
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
            margin-top: 50px;
        }
        
        .gallery-item {
            height: 220px;
            border-radius: 12px;
            overflow: hidden;
            position: relative;
            cursor: pointer;
            transition: all 0.4s;
            border: 2px solid var(--gray);
        }
        
        .gallery-item:hover {
            transform: scale(1.05);
            border-color: var(--primary);
            box-shadow: 0 15px 35px rgba(0, 180, 216, 0.3);
        }
        
        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s;
        }
        
        .gallery-item:hover img {
            transform: scale(1.15);
        }
        
        /* Zones d'intervention Strasbourg */
        .zones-section {
            background-color: rgba(27, 38, 59, 0.9);
            position: relative;
            backdrop-filter: blur(5px);
        }
        
        .zones-section::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://images.unsplash.com/photo-1594736797933-d0f9593a283d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            opacity: 0.1;
            z-index: 0;
        }
        
        .zones-section > .container {
            position: relative;
            z-index: 1;
        }
        
        .zones-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 35px;
            margin-top: 50px;
        }
        
        .zone-card {
            background: rgba(7, 13, 20, 0.9);
            border-radius: 12px;
            padding: 35px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
            border: 2px solid var(--gray);
            transition: all 0.3s;
            backdrop-filter: blur(5px);
        }
        
        .zone-card:hover {
            border-color: var(--primary);
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 180, 216, 0.25);
        }
        
        .zone-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }
        
        .zone-badge {
            padding: 8px 20px;
            border-radius: 25px;
            font-weight: 600;
            font-size: 14px;
            font-family: 'Montserrat', sans-serif;
        }
        
        .zone-1 .zone-badge { background: var(--success); color: var(--dark); }
        .zone-2 .zone-badge { background: var(--warning); color: var(--dark); }
        .zone-3 .zone-badge { background: var(--emergency); color: white; }
        
        .zone-features ul {
            list-style: none;
            margin-top: 20px;
        }
        
        .zone-features li {
            margin-bottom: 12px;
            display: flex;
            align-items: center;
        }
        
        .zone-features li:before {
            content: "✓";
            margin-right: 12px;
            color: var(--success);
            font-weight: bold;
            font-size: 18px;
        }
        
        /* Tableau tarifs */
        .pricing-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 40px;
            background: rgba(7, 13, 20, 0.9);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
            border: 1px solid var(--gray);
            backdrop-filter: blur(5px);
        }
        
        .pricing-table th, .pricing-table td {
            padding: 18px;
            text-align: center;
            border: 1px solid var(--gray);
        }
        
        .pricing-table th {
            background-color: var(--primary);
            color: var(--dark);
            font-weight: 700;
            font-family: 'Montserrat', sans-serif;
            font-size: 16px;
        }
        
        .pricing-table tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.05);
        }
        
        .pricing-table tr:hover {
            background-color: rgba(0, 180, 216, 0.1);
        }
        
        /* Urgence Section */
        .emergency-section {
            text-align: center;
            background: linear-gradient(135deg, rgba(7, 13, 20, 0.95) 0%, rgba(26, 26, 46, 0.95) 100%);
            border-top: 4px solid var(--emergency);
            border-bottom: 4px solid var(--emergency);
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(5px);
        }
        
        .emergency-section::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255, 90, 95, 0.15) 0%, transparent 70%);
        }
        
        .emergency-contact {
            font-size: 36px;
            margin: 25px 0;
            color: var(--emergency);
            font-weight: 700;
            font-family: 'Montserrat', sans-serif;
            text-shadow: 0 2px 10px rgba(255, 90, 95, 0.3);
        }
        
        .emergency-payment {
            background: rgba(7, 13, 20, 0.9);
            border-radius: 12px;
            padding: 30px;
            max-width: 500px;
            margin: 40px auto;
            border: 2px solid var(--emergency);
            box-shadow: 0 15px 35px rgba(255, 90, 95, 0.2);
            backdrop-filter: blur(5px);
        }
        
        /* Paiement en ligne */
        .payment-section {
            text-align: center;
            background: rgba(27, 38, 59, 0.9);
            backdrop-filter: blur(5px);
        }
        
        .payment-options {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin-top: 40px;
            flex-wrap: wrap;
        }
        
        .payment-option {
            background: rgba(7, 13, 20, 0.9);
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
            width: 220px;
            border: 1px solid var(--gray);
            transition: all 0.3s;
            backdrop-filter: blur(5px);
        }
        
        .payment-option:hover {
            transform: translateY(-8px);
            border-color: var(--primary);
            box-shadow: 0 15px 35px rgba(0, 180, 216, 0.25);
        }
        
        /* Footer */
        footer {
            background-color: rgba(7, 13, 20, 0.95);
            color: var(--light);
            padding: 60px 0 25px;
            border-top: 3px solid var(--primary);
            backdrop-filter: blur(5px);
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }
        
        .footer-column h3 {
            color: var(--light);
            margin-bottom: 25px;
            font-size: 22px;
            border-bottom: 2px solid var(--primary);
            padding-bottom: 12px;
            display: inline-block;
            font-family: 'Montserrat', sans-serif;
        }
        
        .copyright {
            text-align: center;
            padding-top: 25px;
            border-top: 1px solid var(--gray);
            color: var(--gray-light);
            font-size: 14px;
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.85);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background: rgba(27, 38, 59, 0.95);
            padding: 40px;
            border-radius: 15px;
            max-width: 550px;
            width: 90%;
            position: relative;
            border: 2px solid var(--primary);
            box-shadow: 0 25px 50px rgba(0, 180, 216, 0.25);
            backdrop-filter: blur(10px);
        }
        
        .close-modal {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 28px;
            cursor: pointer;
            color: var(--gray-light);
            transition: color 0.3s;
        }
        
        .close-modal:hover {
            color: var(--primary);
        }
        
        /* Responsive */
        @media (max-width: 992px) {
            .rdv-container {
                grid-template-columns: 1fr;
            }
            
            .hero h1 {
                font-size: 42px;
            }
            
            .background-sphere {
                right: -300px;
                width: 500px;
                height: 500px;
            }
        }
        
        @media (max-width: 768px) {
            nav ul {
                display: none;
                position: absolute;
                top: 85px;
                left: 0;
                width: 100%;
                background: rgba(7, 13, 20, 0.98);
                flex-direction: column;
                padding: 25px;
                box-shadow: 0 10px 25px rgba(0,0,0,0.5);
                border-top: 3px solid var(--primary);
                backdrop-filter: blur(10px);
            }
            
            nav ul.show {
                display: flex;
            }
            
            nav ul li {
                margin: 15px 0;
            }
            
            .mobile-menu {
                display: block;
            }
            
            .hero {
                padding: 160px 0 80px;
            }
            
            section {
                padding: 60px 0;
            }
            
            .logo-text {
                font-size: 22px;
            }
            
            .emergency-contact {
                font-size: 28px;
            }
            
            .background-sphere {
                right: -350px;
                width: 450px;
                height: 450px;
                opacity: 0.1;
            }
            
            .logo-3d-container {
                width: 50px;
                height: 50px;
            }
        }
        
        @media (max-width: 480px) {
            .logo-text {
                font-size: 18px;
            }
            
            .logo-container {
                gap: 10px;
            }
            
            .hero h1 {
                font-size: 32px;
            }
            
            .btn {
                padding: 12px 25px;
                font-size: 14px;
            }
            
            .background-sphere {
                right: -400px;
                width: 400px;
                height: 400px;
            }
            
            .logo-3d-container {
                width: 40px;
                height: 40px;
            }
        }
    </style>
</head>
<body>
    <!-- Bâtiment sphérique en arrière-plan -->
    <div class="background-sphere">
        <div class="sphere"></div>
        <div class="sphere-structure">
            <div class="sphere-door"></div>
            <div class="sphere-light"></div>
            <div class="sphere-light"></div>
        </div>
    </div>

    <!-- Header -->
    <header>
        <div class="container header-container">
            <div class="logo-container">
                <div class="logo-3d-container">
                    <div class="cube-3d">
                        <div class="cube-face cube-front"></div>
                        <div class="cube-face cube-back"></div>
                        <div class="cube-face cube-right"></div>
                        <div class="cube-face cube-left"></div>
                        <div class="cube-face cube-top"></div>
                        <div class="cube-face cube-bottom"></div>
                    </div>
                </div>
                <div class="logo-text">CLIM<span>TECH</span> RÉFRIGÉRATION</div>
            </div>
            <div class="mobile-menu">☰</div>
            <nav>
                <ul>
                    <li><a href="#accueil">Accueil</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#galerie">Réalisations</a></li>
                    <li><a href="#zones">Zone Strasbourg</a></li>
                    <li><a href="#urgence">Urgence 24/7</a></li>
                    <li><a href="#rdv">RDV & Devis</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="accueil">
        <div class="container">
            <h1>Spécialiste en <span>froid industriel</span> Strasbourg & Alsace</h1>
            <p>Clim Tech Réfrigération assure l'installation, la maintenance et la réparation de vos équipements frigorifiques dans toute la région Grand Est.</p>
            <a href="#urgence" class="btn btn-emergency">URGENCE DÉPANNAGE 24/7</a>
            <a href="#rdv" class="btn" style="margin-left: 20px;">Devis Gratuit</a>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services">
        <div class="container">
            <h2>Nos Services</h2>
            <p>Solutions complètes pour vos installations frigorifiques professionnelles.</p>
            
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-img" style="background-image: url('https://images.unsplash.com/photo-1581094794329-c8112a89af12?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80');"></div>
                    <div class="service-content">
                        <h3>Installation Chambres Froides</h3>
                        <p>Conception et installation sur mesure de chambres froides positives/négatives pour professionnels.</p>
                    </div>
                </div>
                
                <div class="service-card">
                    <div class="service-img" style="background-image: url('https://images.unsplash.com/photo-1558618666-fcd25c85cd64?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80');"></div>
                    <div class="service-content">
                        <h3>Maintenance Préventive</h3>
                        <p>Contrats de maintenance adaptés pour optimiser la durée de vie de vos équipements.</p>
                    </div>
                </div>
                
                <div class="service-card">
                    <div class="service-img" style="background-image: url('https://images.unsplash.com/photo-1581094792964-8d1b7d6c2c3e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80');"></div>
                    <div class="service-content">
                        <h3>Dépannage Urgent</h3>
                        <p>Intervention rapide 24h/24 pour limiter les pertes de votre chaîne du froid.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Galerie Section - Images techniques uniquement -->
    <section class="gallery-section" id="galerie">
        <div class="container">
            <h2>Nos Réalisations Techniques</h2>
            <p>Découvrez nos installations de froid industriel dans la région de Strasbourg.</p>
            
            <div class="gallery-grid">
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1581094794329-c8112a89af12?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Chambre froide industrielle">
                </div>
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1558618666-fcd25c85cd64?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Système réfrigération industriel">
                </div>
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1581094794793-0d0d6f5d5b5b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Installation professionnelle chambre froide">
                </div>
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1581094794793-0d0d6f5d5b5c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Contrôle technique équipement froid">
                </div>
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1581094792964-8d1b7d6c2c3e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Maintenance préventive système froid">
                </div>
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1558618666-fcd25c85cd64?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=60" alt="Équipement frigorifique industriel">
                </div>
            </div>
        </div>
    </section>

    <!-- Zones d'intervention Strasbourg -->
    <section class="zones-section" id="zones">
        <div class="container">
            <h2>Zones d'Intervention Strasbourg & Alsace</h2>
            <p>Nos tarifs de déplacement varient selon votre localisation dans la région.</p>
            
            <table class="pricing-table">
                <thead>
                    <tr>
                        <th>Zone</th>
                        <th>Secteur géographique</th>
                        <th>Tarif déplacement</th>
                        <th>Délai d'intervention</th>
                        <th>Disponibilité</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Zone 1</strong></td>
                        <td>Strasbourg centre & Eurométropole</td>
                        <td>65 € HT</td>
                        <td>≤ 90 minutes</td>
                        <td>24h/24 - 7j/7</td>
                    </tr>
                    <tr>
                        <td><strong>Zone 2</strong></td>
                        <td>Bas-Rhin (hors Eurométropole)</td>
                        <td>90 € HT</td>
                        <td>≤ 3 heures</td>
                        <td>6h-23h - 7j/7</td>
                    </tr>
                    <tr>
                        <td><strong>Zone 3</strong></td>
                        <td>Grand Est (Alsace, Lorraine)</td>
                        <td>120 € HT</td>
                        <td>≤ 5 heures</td>
                        <td>8h-20h - Lun/Sam</td>
                    </tr>
                </tbody>
            </table>
            
            <div class="zones-grid">
                <div class="zone-card zone-1">
                    <div class="zone-header">
                        <h3>Zone 1 - Strasbourg Centre</h3>
                        <span class="zone-badge">INTERVENTION EXPRESS</span>
                    </div>
                    <p><strong>Tarif déplacement : 65 € HT</strong></p>
                    <p>Communes : Strasbourg, Schiltigheim, Illkirch, Bischheim, etc.</p>
                    <div class="zone-features">
                        <ul>
                            <li>Intervention ultra-rapide (≤ 90 min)</li>
                            <li>Disponibilité 24/7 toute l'année</li>
                            <li>Équipe d'urgence dédiée</li>
                            <li>Dépannage prioritaire garanti</li>
                        </ul>
                    </div>
                </div>
                
                <div class="zone-card zone-2">
                    <div class="zone-header">
                        <h3>Zone 2 - Bas-Rhin</h3>
                        <span class="zone-badge">INTERVENTION RAPIDE</span>
                    </div>
                    <p><strong>Tarif déplacement : 90 € HT</strong></p>
                    <p>Tout le Bas-Rhin hors Eurométropole de Strasbourg.</p>
                    <div class="zone-features">
                        <ul>
                            <li>Intervention rapide (≤ 3 heures)</li>
                            <li>Disponibilité 6h-23h</li>
                            <li>Service 7j/7</li>
                            <li>Techniciens certifiés</li>
                        </ul>
                    </div>
                </div>
                
                <div class="zone-card zone-3">
                    <div class="zone-header">
                        <h3>Zone 3 - Grand Est</h3>
                        <span class="zone-badge">INTERVENTION PROGRAMMÉE</span>
                    </div>
                    <p><strong>Tarif déplacement : 120 € HT</strong></p>
                    <p>Alsace, Moselle, Vosges et départements limitrophes.</p>
                    <div class="zone-features">
                        <ul>
                            <li>Intervention sous 5 heures</li>
                            <li>Disponibilité 8h-20h</li>
                            <li>Lundi au samedi</li>
                            <li>Maintenance préventive incluse</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Urgence Section -->
    <section class="emergency-section" id="urgence">
        <div class="container">
            <h2>DÉPANNAGE URGENT 24H/24 - 7J/7</h2>
            <p>En cas de panne de votre installation frigorifique, notre équipe d'urgence intervient rapidement pour limiter les pertes.</p>
            
            <div class="emergency-contact">📞 03 88 45 67 89</div>
            <p>Appelez-nous pour une intervention d'urgence. Notre équipe est disponible 24h/24 et 7j/7.</p>
            
            <a href="tel:0388456789" class="btn btn-emergency">APPEL URGENCE IMMÉDIAT</a>
            
            <div class="emergency-payment">
                <h3>Paiement Déplacement d'Urgence</h3>
                <p style="margin: 15px 0;">Réglez le déplacement d'urgence en ligne pour une intervention prioritaire :</p>
                
                <div style="display: flex; flex-direction: column; gap: 15px; margin: 25px 0;">
                    <div style="display: flex; justify-content: space-between; background: rgba(27, 38, 59, 0.8); padding: 15px; border-radius: 8px; border: 1px solid var(--gray);">
                        <span>Zone 1 - Strasbourg Centre</span>
                        <strong style="color: var(--success);">65 € HT</strong>
                    </div>
                    <div style="display: flex; justify-content: space-between; background: rgba(27, 38, 59, 0.8); padding: 15px; border-radius: 8px; border: 1px solid var(--gray);">
                        <span>Zone 2 - Bas-Rhin</span>
                        <strong style="color: var(--warning);">90 € HT</strong>
                    </div>
                    <div style="display: flex; justify-content: space-between; background: rgba(27, 38, 59, 0.8); padding: 15px; border-radius: 8px; border: 1px solid var(--gray);">
                        <span>Zone 3 - Grand Est</span>
                        <strong style="color: var(--emergency);">120 € HT</strong>
                    </div>
                </div>
                
                <button class="btn" onclick="openPaymentModal()">PAYER DÉPLACEMENT URGENCE</button>
                <p style="margin-top: 15px; font-size: 14px; color: var(--gray-light);">Le règlement du déplacement garantit une intervention prioritaire dans les délais annoncés.</p>
            </div>
            
            <div style="margin-top: 40px;">
                <h3>Types d'urgence traitées</h3>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-top: 30px;">
                    <div style="background: rgba(255, 90, 95, 0.1); padding: 20px; border-radius: 10px; border: 1px solid var(--emergency);">
                        <strong style="color: var(--emergency);">Panne Totale</strong>
                        <p style="margin-top: 10px;">Arrêt complet de la production de froid</p>
                    </div>
                    <div style="background: rgba(255, 90, 95, 0.1); padding: 20px; border-radius: 10px; border: 1px solid var(--emergency);">
                        <strong style="color: var(--emergency);">Défaut Température</strong>
                        <p style="margin-top: 10px;">Écart de température critique détecté</p>
                    </div>
                    <div style="background: rgba(255, 90, 95, 0.1); padding: 20px; border-radius: 10px; border: 1px solid var(--emergency);">
                        <strong style="color: var(--emergency);">Fuites Réfrigérant</strong>
                        <p style="margin-top: 10px;">Fuites de fluide frigorigène</p>
                    </div>
                    <div style="background: rgba(255, 90, 95, 0.1); padding: 20px; border-radius: 10px; border: 1px solid var(--emergency);">
                        <strong style="color: var(--emergency);">Problèmes Électriques</strong>
                        <p style="margin-top: 10px;">Défauts électriques ou de sécurité</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- RDV Section -->
    <section class="rdv-section" id="rdv">
        <div class="container">
            <div style="background: rgba(7, 13, 20, 0.9); padding: 40px; border-radius: 15px; border: 2px solid var(--gray); backdrop-filter: blur(5px);">
                <h2>Demander un Devis ou Prendre RDV</h2>
                <p style="margin-bottom: 30px;">Remplissez le formulaire ci-dessous pour une intervention ou un devis gratuit.</p>
                
                <form id="appointment-form">
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 25px; margin-bottom: 25px;">
                        <div class="form-group">
                            <label for="name" style="display: block; margin-bottom: 8px; color: var(--light); font-weight: 500;">Nom complet</label>
                            <input type="text" id="name" required style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light);">
                        </div>
                        
                        <div class="form-group">
                            <label for="email" style="display: block; margin-bottom: 8px; color: var(--light); font-weight: 500;">Email</label>
                            <input type="email" id="email" required style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light);">
                        </div>
                    </div>
                    
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 25px; margin-bottom: 25px;">
                        <div class="form-group">
                            <label for="phone" style="display: block; margin-bottom: 8px; color: var(--light); font-weight: 500;">Téléphone</label>
                            <input type="tel" id="phone" required style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light);">
                        </div>
                        
                        <div class="form-group">
                            <label for="zone" style="display: block; margin-bottom: 8px; color: var(--light); font-weight: 500;">Zone d'intervention</label>
                            <select id="zone" required style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light);">
                                <option value="">Sélectionnez votre zone</option>
                                <option value="zone1">Zone 1 - Strasbourg Centre</option>
                                <option value="zone2">Zone 2 - Bas-Rhin</option>
                                <option value="zone3">Zone 3 - Grand Est</option>
                            </select>
                        </div>
                    </div>
                    
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 25px; margin-bottom: 25px;">
                        <div class="form-group">
                            <label for="service" style="display: block; margin-bottom: 8px; color: var(--light); font-weight: 500;">Type de service</label>
                            <select id="service" required style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light);">
                                <option value="">Sélectionnez un service</option>
                                <option value="installation">Installation chambre froide</option>
                                <option value="maintenance">Maintenance préventive</option>
                                <option value="repair">Dépannage urgent</option>
                                <option value="consultation">Consultation technique</option>
                            </select>
                        </div>
                        
                        <div class="form-group">
                            <label for="date" style="display: block; margin-bottom: 8px; color: var(--light); font-weight: 500;">Date souhaitée</label>
                            <input type="date" id="date" required style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light);">
                        </div>
                    </div>
                    
                    <div class="form-group" style="margin-bottom: 30px;">
                        <label for="message" style="display: block; margin-bottom: 8px; color: var(--light); font-weight: 500;">Message (optionnel)</label>
                        <textarea id="message" placeholder="Décrivez brièvement votre besoin..." style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light); height: 120px;"></textarea>
                    </div>
                    
                    <button type="submit" class="btn" style="width: 100%; padding: 16px; font-size: 18px;">Envoyer la demande</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Paiement Section -->
    <section class="payment-section" id="paiement">
        <div class="container">
            <h2>Paiement en Ligne Sécurisé</h2>
            <p>Réglez facilement vos factures en toute sécurité grâce à notre plateforme de paiement.</p>
            
            <div class="payment-options">
                <div class="payment-option">
                    <div style="font-size: 48px; margin-bottom: 20px;">💳</div>
                    <h3>Carte Bancaire</h3>
                    <p>Paiement sécurisé par carte avec cryptage SSL</p>
                </div>
                
                <div class="payment-option">
                    <div style="font-size: 48px; margin-bottom: 20px;">📱</div>
                    <h3>Virement</h3>
                    <p>Virement bancaire simple et rapide</p>
                </div>
                
                <div class="payment-option">
                    <div style="font-size: 48px; margin-bottom: 20px;">🔐</div>
                    <h3>PayPal</h3>
                    <p>Paiement sécurisé via PayPal</p>
                </div>
            </div>
            
            <a href="#" class="btn btn-secondary" id="pay-btn" style="margin-top: 40px;">Accéder au portail de paiement</a>
        </div>
    </section>

    <!-- Footer -->
    <footer id="contact">
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <div class="logo-container">
                        <div class="logo-3d-container" style="width: 45px; height: 45px;">
                            <div class="cube-3d" style="animation: rotateCube 15s infinite linear;">
                                <div class="cube-face cube-front"></div>
                                <div class="cube-face cube-back"></div>
                                <div class="cube-face cube-right"></div>
                                <div class="cube-face cube-left"></div>
                                <div class="cube-face cube-top"></div>
                                <div class="cube-face cube-bottom"></div>
                            </div>
                        </div>
                        <div class="logo-text" style="font-size: 22px;">CLIM<span>TECH</span></div>
                    </div>
                    <p style="margin-top: 20px; color: var(--gray-light);">Spécialiste en froid industriel à Strasbourg. Nous intervenons pour l'installation, la maintenance et la réparation de vos équipements frigorifiques.</p>
                </div>
                
                <div class="footer-column">
                    <h3>Contact</h3>
                    <ul>
                        <li style="margin-bottom: 12px; color: var(--gray-light);">📞 03 88 45 67 89</li>
                        <li style="margin-bottom: 12px; color: var(--gray-light);">✉️ contact@climtech-strasbourg.fr</li>
                        <li style="color: var(--gray-light);">📍 12 Rue du Froid Industriel, 67000 Strasbourg</li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Horaires</h3>
                    <ul>
                        <li style="margin-bottom: 12px; color: var(--gray-light);">Lun-Ven: 8h-18h</li>
                        <li style="margin-bottom: 12px; color: var(--gray-light);">Sam: 9h-12h</li>
                        <li style="color: var(--gray-light);">Urgences: 24h/24 - 7j/7</li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Liens Rapides</h3>
                    <ul>
                        <li style="margin-bottom: 12px;"><a href="#accueil">Accueil</a></li>
                        <li style="margin-bottom: 12px;"><a href="#services">Services</a></li>
                        <li style="margin-bottom: 12px;"><a href="#urgence">Urgence Dépannage</a></li>
                        <li><a href="#paiement">Paiement en ligne</a></li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2023 Clim Tech Réfrigération - Strasbourg. Tous droits réservés.</p>
            </div>
        </div>
    </footer>

    <!-- Modal de paiement -->
    <div class="modal" id="payment-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2>Paiement Déplacement Urgence</h2>
            <p style="margin: 20px 0;">Sélectionnez votre zone et procédez au paiement sécurisé :</p>
            
            <div style="margin: 25px 0;">
                <div class="form-group">
                    <label for="payment-zone" style="display: block; margin-bottom: 10px; color: var(--light);">Zone d'intervention</label>
                    <select id="payment-zone" style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light); margin-bottom: 20px;">
                        <option value="">Sélectionnez votre zone</option>
                        <option value="65">Zone 1 - Strasbourg Centre (65 € HT)</option>
                        <option value="90">Zone 2 - Bas-Rhin (90 € HT)</option>
                        <option value="120">Zone 3 - Grand Est (120 € HT)</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="payment-amount" style="display: block; margin-bottom: 10px; color: var(--light);">Montant à régler</label>
                    <input type="text" id="payment-amount" readonly style="width: 100%; padding: 12px; background: var(--dark); border: 1px solid var(--gray); border-radius: 8px; color: var(--light); font-weight: bold; font-size: 18px; text-align: center;" value="0 € HT">
                </div>
            </div>
            
            <div style="background: rgba(0, 180, 216, 0.1); padding: 20px; border-radius: 10px; margin: 25px 0; border: 1px solid var(--primary);">
                <p style="color: var(--light); margin-bottom: 10px;"><strong>Important :</strong></p>
                <p style="color: var(--gray-light); font-size: 14px;">Le paiement du déplacement garantit une intervention prioritaire dans les délais annoncés pour votre zone. Ce montant sera déduit de la facture totale de l'intervention.</p>
            </div>
            
            <button class="btn" style="width: 100%; padding: 16px; font-size: 18px;">PROCÉDER AU PAIEMENT SÉCURISÉ</button>
        </div>
    </div>

    <!-- Modal de confirmation -->
    <div class="modal" id="confirmation-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2>Demande envoyée avec succès !</h2>
            <div style="font-size: 60px; color: var(--success); text-align: center; margin: 20px 0;">✓</div>
            <p style="text-align: center; margin: 20px 0;">Votre demande de rendez-vous a bien été enregistrée. Notre équipe vous contactera dans les plus brefs délais pour confirmer la date et l'heure.</p>
            <button class="btn" id="modal-close-btn" style="width: 100%; padding: 16px; margin-top: 20px;">Fermer</button>
        </div>
    </div>

    <script>
        // Menu mobile
        document.querySelector('.mobile-menu').addEventListener('click', function() {
            document.querySelector('nav ul').classList.toggle('show');
        });
        
        // Formulaire de rendez-vous
        document.getElementById('appointment-form').addEventListener('submit', function(e) {
            e.preventDefault();
            document.getElementById('confirmation-modal').style.display = 'flex';
        });
        
        // Gestion du paiement d'urgence
        function openPaymentModal() {
            document.getElementById('payment-modal').style.display = 'flex';
        }
        
        document.getElementById('pay-btn').addEventListener('click', function(e) {
            e.preventDefault();
            openPaymentModal();
        });
        
        // Mise à jour du montant du paiement
        document.getElementById('payment-zone').addEventListener('change', function() {
            const amount = this.value;
            if (amount) {
                document.getElementById('payment-amount').value = amount + ' € HT';
            } else {
                document.getElementById('payment-amount').value = '0 € HT';
            }
        });
        
        // Fermer les modals
        document.querySelectorAll('.close-modal, #modal-close-btn').forEach(function(element) {
            element.addEventListener('click', function() {
                document.querySelectorAll('.modal').forEach(function(modal) {
                    modal.style.display = 'none';
                });
            });
        });
        
        // Fermer les modals en cliquant à l'extérieur
        window.addEventListener('click', function(e) {
            document.querySelectorAll('.modal').forEach(function(modal) {
                if (e.target === modal) {
                    modal.style.display = 'none';
                }
            });
        });
        
        // Fermer le menu mobile en cliquant sur un lien
        document.querySelectorAll('nav ul li a').forEach(function(link) {
            link.addEventListener('click', function() {
                document.querySelector('nav ul').classList.remove('show');
            });
        });
        
        // Date minimum pour le formulaire (aujourd'hui)
        const today = new Date().toISOString().split('T')[0];
        document.getElementById('date').min = today;
    </script>
</body>
</html>

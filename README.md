<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Apex Summit Trails | Global Leaders in Student Expeditions</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* DESIGN SYSTEM SYSTEM (As per Screenshot 2026-06-12 181615.png) */
        :root {
            --midnight-navy: #0A0E1A;
            --glacier-white: #F0F4F8;
            --summit-gold: #D4A853;
            --moss-green: #2D5016;
            --ice-blue: #7BB8D4;
            --white: #ffffff;
            --card-bg: rgba(255, 255, 255, 0.03);
            --card-border: rgba(255, 255, 255, 0.08);
            --font-display: 'Bebas Neue', sans-serif;
            --font-body: 'Inter', sans-serif;
            --transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        /* RESET & GENERAL STYLES */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--midnight-navy);
            color: var(--glacier-white);
            font-family: var(--font-body);
            overflow-x: hidden;
            line-height: 1.6;
        }

        h1, h2, h3, h4, .display-font {
            font-family: var(--font-display);
            letter-spacing: 1px;
            font-weight: 400;
        }

        a {
            text-decoration: none;
            color: inherit;
            transition: var(--transition);
        }

        ul {
            list-style: none;
        }

        img {
            max-width: 100%;
            display: block;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        /* UTILITIES & ANIMATION CLASSES */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.8rem 2rem;
            font-family: var(--font-display);
            font-size: 1.2rem;
            letter-spacing: 1px;
            border-radius: 4px;
            cursor: pointer;
            transition: var(--transition);
            border: none;
        }

        .btn-primary {
            background-color: var(--summit-gold);
            color: var(--midnight-navy);
        }

        .btn-primary:hover {
            background-color: var(--white);
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(212, 168, 83, 0.2);
        }

        .btn-outline {
            background-color: transparent;
            border: 2px solid var(--ice-blue);
            color: var(--ice-blue);
        }

        .btn-outline:hover {
            background-color: var(--ice-blue);
            color: var(--midnight-navy);
            transform: translateY(-3px);
        }

        .section-title {
            font-size: 3.5rem;
            text-align: center;
            margin-bottom: 1rem;
            color: var(--white);
        }

        .section-subtitle {
            text-align: center;
            max-width: 600px;
            margin: 0 auto 4rem auto;
            color: var(--ice-blue);
            font-size: 1.1rem;
            font-weight: 300;
        }

        /* Scroll Animation Triggers */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.8s ease, transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* TOP UTILITY BAR & NAVIGATION */
        .top-bar {
            background-color: rgba(10, 14, 26, 0.95);
            border-bottom: 1px solid var(--card-border);
            font-size: 0.85rem;
            padding: 0.5rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 101;
        }

        .top-bar .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .top-info {
            display: flex;
            gap: 1.5rem;
        }

        .top-info a:hover {
            color: var(--summit-gold);
        }

        .top-tagline {
            font-family: var(--font-display);
            letter-spacing: 1.5px;
            color: var(--summit-gold);
        }

        header {
            background-color: rgba(10, 14, 26, 0.85);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            position: fixed;
            width: 100%;
            top: 33px;
            z-index: 100;
            border-bottom: 1px solid var(--card-border);
            transition: var(--transition);
        }

        header.scrolled {
            top: 0;
            background-color: rgba(10, 14, 26, 0.98);
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 80px;
        }

        .logo {
            font-family: var(--font-display);
            font-size: 1.8rem;
            color: var(--white);
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .logo span {
            color: var(--summit-gold);
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            font-family: var(--font-display);
            font-size: 1.1rem;
            letter-spacing: 0.5px;
            font-weight: 300;
            position: relative;
            padding: 0.5rem 0;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background-color: var(--summit-gold);
            transition: var(--transition);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-links a:hover {
            color: var(--white);
        }

        .mobile-toggle {
            display: none;
            color: var(--white);
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* PARALLAX SIGNATURE HERO */
        .parallax-hero {
            position: relative;
            height: 100vh;
            width: 100%;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(to bottom, #0f172a, #1e293b);
        }

        .parallax-layer {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: bottom center;
            will-change: transform;
        }

        /* Generated multi-layered mountain graphics natively using CSS gradients and SVG shapes */
        .layer-bg {
            background: radial-gradient(circle at 50% 30%, #2a3e5c 0%, var(--midnight-navy) 80%);
            z-index: 1;
        }

        .layer-stars {
            background-image: radial-gradient(white, rgba(255,255,255,.2) 2px, transparent 40px);
            background-size: 550px 550px;
            opacity: 0.4;
            z-index: 2;
        }

        .layer-mountains-back {
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 600" fill="%23172237"><path d="M0,450 L180,300 L420,410 L680,220 L980,390 L1220,260 L1440,380 L1440,600 L0,600 Z"></path></svg>');
            z-index: 3;
            transform: translateY(10%);
        }

        .layer-mountains-mid {
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 600" fill="%2321304a"><path d="M0,500 L280,350 L600,480 L850,310 L1150,440 L1440,320 L1440,600 L0,600 Z"></path></svg>');
            z-index: 4;
            transform: translateY(5%);
        }

        .hero-content {
            position: relative;
            z-index: 5;
            text-align: center;
            max-width: 900px;
            padding: 0 2rem;
            margin-top: 60px;
        }

        .hero-content h1 {
            font-size: 6rem;
            line-height: 0.95;
            margin-bottom: 1.5rem;
            color: var(--white);
            text-shadow: 0 4px 20px rgba(0,0,0,0.6);
        }

        .hero-content h1 span {
            color: var(--summit-gold);
        }

        .hero-content p {
            font-size: 1.3rem;
            font-weight: 300;
            max-width: 650px;
            margin: 0 auto 2.5rem auto;
            color: var(--glacier-white);
            text-shadow: 0 2px 10px rgba(0,0,0,0.5);
        }

        .layer-mountains-front {
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 600" fill="%230A0E1A"><path d="M0,520 L350,420 L750,530 L1100,390 L1440,490 L1440,600 L0,600 Z"></path></svg>');
            z-index: 6;
        }

        /* BOOKING / EXPEDITION PLANNER SECTION */
        .planner-section {
            padding: 5rem 0;
            background: linear-gradient(to bottom, var(--midnight-navy), #0e1626);
            position: relative;
            z-index: 10;
        }

        .planner-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .planner-text h2 {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            color: var(--white);
        }

        .planner-text p {
            margin-bottom: 1.5rem;
            font-weight: 300;
            color: var(--ice-blue);
        }

        .form-card {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            padding: 3rem;
            border-radius: 8px;
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .form-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .form-group.full-width {
            grid-column: span 2;
        }

        .form-group label {
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: var(--summit-gold);
        }

        .form-group input, .form-group select {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--card-border);
            padding: 0.8rem 1rem;
            border-radius: 4px;
            color: var(--white);
            font-family: var(--font-body);
            transition: var(--transition);
        }

        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: var(--summit-gold);
            background: rgba(255, 255, 255, 0.1);
        }

        .form-card .btn {
            width: 100%;
            justify-content: center;
            margin-top: 1.5rem;
        }

        /* DESTINATIONS CAROUSEL/GRID */
        .destinations-section {
            padding: 8rem 0;
            background-color: #0e1626;
        }

        .destinations-tags {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 0.8rem;
            max-width: 900px;
            margin: 0 auto;
        }

        .desti-tag {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            padding: 0.5rem 1.5rem;
            border-radius: 50px;
            font-size: 0.9rem;
            font-weight: 500;
            transition: var(--transition);
            cursor: pointer;
        }

        .desti-tag:hover {
            background: var(--ice-blue);
            color: var(--midnight-navy);
            border-color: var(--ice-blue);
            transform: scale(1.05);
        }

        /* PACKAGES SECTION */
        .packages-section {
            padding: 8rem 0;
            background-color: var(--midnight-navy);
        }

        .packages-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
        }

        .package-card {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            border-radius: 6px;
            overflow: hidden;
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            position: relative;
        }

        .package-card:hover {
            transform: translateY(-10px);
            border-color: var(--summit-gold);
            box-shadow: 0 15px 30px rgba(0,0,0,0.4);
        }

        .package-img {
            height: 200px;
            background-size: cover;
            background-position: center;
            position: relative;
        }

        /* Placeholders mimicking clean structural visual layout assets */
        .pkg-1 { background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(10,14,26,0.9)), url('https://images.unsplash.com/photo-1544735716-392fe2489ffa?auto=format&fit=crop&w=600&q=80'); }
        .pkg-2 { background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(10,14,26,0.9)), url('https://images.unsplash.com/photo-1491884661188-7a232e8bf817?auto=format&fit=crop&w=600&q=80'); }
        .pkg-3 { background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(10,14,26,0.9)), url('https://images.unsplash.com/photo-1522163182402-834f871fd851?auto=format&fit=crop&w=600&q=80'); }
        .pkg-4 { background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(10,14,26,0.9)), url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=80'); }
        .pkg-5 { background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(10,14,26,0.9)), url('https://images.unsplash.com/photo-1533240332313-0db49b459ad6?auto=format&fit=crop&w=600&q=80'); }
        .pkg-6 { background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(10,14,26,0.9)), url('https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?auto=format&fit=crop&w=600&q=80'); }
        .pkg-7 { background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(10,14,26,0.9)), url('https://images.unsplash.com/photo-1502784444187-359ac186c5bb?auto=format&fit=crop&w=600&q=80'); }
        .pkg-8 { background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(10,14,26,0.9)), url('https://images.unsplash.com/photo-1542601906990-b4d3fb778b09?auto=format&fit=crop&w=600&q=80'); }

        .package-badge {
            position: absolute;
            top: 1rem;
            left: 1rem;
            background: var(--moss-green);
            color: var(--white);
            padding: 0.3rem 0.8rem;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
            border-radius: 4px;
            letter-spacing: 0.5px;
        }

        .package-content {
            padding: 1.5rem;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .package-title {
            font-size: 1.4rem;
            color: var(--white);
            margin-bottom: 1rem;
            line-height: 1.2;
        }

        .package-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-top: 1px solid var(--card-border);
            padding-top: 1rem;
            margin-top: 1.5rem;
        }

        .package-price {
            font-family: var(--font-display);
            font-size: 1.3rem;
            color: var(--summit-gold);
        }

        .package-price span {
            font-size: 0.8rem;
            font-family: var(--font-body);
            color: var(--ice-blue);
        }

        /* STUDENT PROGRAM / PROMO BANNER BAR */
        .promo-banner {
            background: linear-gradient(135deg, #162238 0%, var(--midnight-navy) 100%);
            border-y: 1px solid var(--card-border);
            padding: 6rem 0;
            text-align: center;
            position: relative;
        }

        .promo-banner::before {
            content: '';
            position: absolute;
            inset: 0;
            background: radial-gradient(circle at 80% 20%, rgba(212, 168, 83, 0.05) 0%, transparent 50%);
            pointer-events: none;
        }

        .promo-content {
            max-width: 750px;
            margin: 0 auto;
        }

        .promo-tag {
            color: var(--summit-gold);
            font-family: var(--font-display);
            font-size: 1.4rem;
            letter-spacing: 2px;
            margin-bottom: 1rem;
            display: block;
        }

        .promo-content h2 {
            font-size: 4rem;
            line-height: 1;
            margin-bottom: 1.5rem;
            color: var(--white);
        }

        .promo-content p {
            color: var(--ice-blue);
            font-size: 1.1rem;
            margin-bottom: 2.5rem;
            font-weight: 300;
        }

        /* PROGRAM MODULE IN-DEPTH SECTION */
        .program-section {
            padding: 8rem 0;
            background-color: #0e1626;
        }

        .program-showcase {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .program-features {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }

        .feature-card {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            padding: 2rem;
            border-radius: 6px;
            transition: var(--transition);
        }

        .feature-card:hover {
            border-color: var(--ice-blue);
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 2rem;
            color: var(--summit-gold);
            margin-bottom: 1rem;
        }

        .feature-card h3 {
            font-size: 1.5rem;
            color: var(--white);
            margin-bottom: 0.5rem;
        }

        .feature-card p {
            font-size: 0.9rem;
            color: var(--ice-blue);
            font-weight: 300;
        }

        /* THE APEX BLOG HUB */
        .blog-section {
            padding: 8rem 0;
            background-color: var(--midnight-navy);
        }

        .blog-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2.5rem;
        }

        .blog-card {
            background: var(--card-bg);
            border-radius: 6px;
            overflow: hidden;
            border: 1px solid var(--card-border);
            transition: var(--transition);
        }

        .blog-card:hover {
            transform: translateY(-5px);
            border-color: var(--summit-gold);
        }

        .blog-info {
            padding: 2rem;
        }

        .blog-meta {
            font-size: 0.8rem;
            color: var(--summit-gold);
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 0.5rem;
        }

        .blog-title {
            font-size: 1.6rem;
            color: var(--white);
            line-height: 1.2;
            margin-bottom: 1rem;
        }

        .blog-link {
            font-family: var(--font-display);
            color: var(--ice-blue);
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            margin-top: 1rem;
        }

        .blog-link:hover {
            color: var(--white);
        }

        /* FOOTER SYSTEM */
        footer {
            background-color: #05070d;
            padding: 6rem 0 2rem 0;
            border-top: 1px solid var(--card-border);
        }

        .footer-grid {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr;
            gap: 4rem;
            margin-bottom: 4rem;
        }

        .footer-brand p {
            color: var(--ice-blue);
            font-weight: 300;
            margin: 1.5rem 0;
            font-size: 0.95rem;
        }

        .social-row {
            display: flex;
            gap: 1rem;
        }

        .social-icon {
            width: 40px;
            height: 40px;
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            transition: var(--transition);
        }

        .social-icon:hover {
            background: var(--summit-gold);
            color: var(--midnight-navy);
            transform: scale(1.1);
        }

        .footer-col h4 {
            font-size: 1.3rem;
            color: var(--white);
            margin-bottom: 1.5rem;
            position: relative;
        }

        .footer-col ul {
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
        }

        .footer-col a {
            color: var(--ice-blue);
            font-size: 0.95rem;
            font-weight: 300;
        }

        .footer-col a:hover {
            color: var(--summit-gold);
            padding-left: 5px;
        }

        .footer-bottom {
            border-top: 1px solid var(--card-border);
            padding-top: 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.85rem;
            color: rgba(240, 244, 248, 0.4);
        }

        /* RESPONSIVE LAYOUT BREAKPOINTS */
        @media (max-width: 1024px) {
            .hero-content h1 { font-size: 4.5rem; }
            .planner-grid, .program-showcase { grid-template-columns: 1fr; gap: 3rem; }
            .blog-grid { grid-template-columns: repeat(2, 1fr); }
            .footer-grid { grid-template-columns: 1fr 1fr; }
        }

        @media (max-width: 768px) {
            .top-bar { display: none; }
            header { top: 0; }
            .mobile-toggle { display: block; }
            .nav-links {
                position: fixed;
                top: 80px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 80px);
                background-color: var(--midnight-navy);
                flex-direction: column;
                padding: 4rem 2rem;
                transition: var(--transition);
                z-index: 99;
                align-items: flex-start;
            }
            .nav-links.active { left: 0; }
            .hero-content h1 { font-size: 3.5rem; }
            .blog-grid { grid-template-columns: 1fr; }
            .form-grid { grid-template-columns: 1fr; }
            .form-group.full-width { grid-column: span 1; }
            .section-title { font-size: 2.5rem; }
            .footer-grid { grid-template-columns: 1fr; gap: 2.5rem; }
        }
    </style>
</head>
<body>

    <!-- TOP UTIL BAR -->
    <div class="top-bar">
        <div class="container">
            <div class="top-info">
                <a href="tel:+27725212269"><i class="fa-solid fa-phone"></i> +27 72 521 2269</a>
                <a href="mailto:info@apexsummittrails.com"><i class="fa-solid fa-envelope"></i> info@apexsummittrails.com</a>
            </div>
            <div class="top-tagline">Global Leaders in Student Expeditions</div>
        </div>
    </div>

    <!-- MAIN HEADER NAV -->
    <header id="main-header">
        <div class="container nav-container">
            <a href="#" class="logo">
                <i class="fa-solid fa-mountain-sun"></i> APEX <span>SUMMIT TRAILS</span>
            </a>
            <nav class="nav-links" id="nav-menu">
                <a href="#">Home</a>
                <a href="#destinations">Destinations</a>
                <a href="#packages">Our Packages</a>
                <a href="#program">Leadership Programme</a>
                <a href="#blog">Blog</a>
                <a href="#planner" class="btn btn-primary" style="padding: 0.5rem 1.5rem;">Book Tour</a>
            </nav>
            <div class="mobile-toggle" id="mobile-btn">
                <i class="fa-solid fa-bars"></i>
            </div>
        </div>
    </header>

    <!-- LAYERED PARALLAX MOTION GRAPHIC HERO -->
    <section class="parallax-hero">
        <div class="parallax-layer layer-bg" data-speed="0.05"></div>
        <div class="parallax-layer layer-stars" data-speed="0.1"></div>
        <div class="parallax-layer layer-mountains-back" data-speed="0.25"></div>
        <div class="parallax-layer layer-mountains-mid" data-speed="0.4"></div>
        
        <div class="hero-content">
            <h1 class="reveal">CONQUER THE WORLD'S<br><span>MOST ICONIC PEAKS</span></h1>
            <p class="reveal">Embark on unforgettable journeys where elite adventure meets character transformation. Expert-guided expeditions tailored for student leaders and dynamic world travelers.</p>
            <div class="reveal" style="display: flex; gap: 1rem; justify-content: center;">
                <a href="#planner" class="btn btn-primary">Plan Your Expedition</a>
                <a href="#packages" class="btn btn-outline">Explore Treks</a>
            </div>
        </div>

        <div class="parallax-layer layer-mountains-front" data-speed="0.6"></div>
    </section>

    <!-- EXPEDITION PLANNER FORM SECTION -->
    <section id="planner" class="planner-section">
        <div class="container">
            <div class="planner-grid">
                <div class="planner-text reveal">
                    <h2>LET'S PLAN YOUR NEXT EXPEDITION</h2>
                    <p>Whether you are seeking an adrenaline-pumping mountain climb, a structured global high-school program, or a restorative wilderness journey, let's tailor the trek to your potential.</p>
                    <p>Our global support staff and local expert guides ensure premium execution, risk mitigation, and world-class peak leadership alignment from start to finish.</p>
                </div>
                <div class="form-card reveal">
                    <form onsubmit="event.preventDefault(); alert('Thank you! Our expedition leaders will reach out shortly.');">
                        <div class="form-grid">
                            <div class="form-group">
                                <label>First Name *</label>
                                <input type="text" required placeholder="John">
                            </div>
                            <div class="form-group">
                                <label>Last Name</label>
                                <input type="text" placeholder="Doe">
                            </div>
                            <div class="form-group">
                                <label>Email Address *</label>
                                <input type="email" required placeholder="john@example.com">
                            </div>
                            <div class="form-group">
                                <label>Phone Number</label>
                                <input type="tel" placeholder="+1 (555) 000-0000">
                            </div>
                            <div class="form-group">
                                <label>No. of Travellers *</label>
                                <input type="number" min="1" required placeholder="1">
                            </div>
                            <div class="form-group">
                                <label>Destination Peak *</label>
                                <select required>
                                    <option value="">Select Target Destination</option>
                                    <option value="kilimanjaro">Mount Kilimanjaro (Tanzania)</option>
                                    <option value="fuji">Mount Fuji (Japan)</option>
                                    <option value="ebc">Everest Base Camp (Nepal)</option>
                                    <option value="toubkal">Mount Toubkal (Morocco)</option>
                                    <option value="kinabalu">Mount Kinabalu (Malaysia)</option>
                                </select>
                            </div>
                        </div>
                        <button type="submit" class="btn btn-primary">Let’s Go! <i class="fa-solid fa-arrow-right"></i></button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- DESTINATIONS SELECTION SYSTEM -->
    <section id="destinations" class="destinations-section">
        <div class="container">
            <h2 class="section-title reveal">+25 GLOBAL DESTINATIONS</h2>
            <p class="section-subtitle reveal">We maintain an active on-the-ground operating presence in the world's most compelling geo-locations, coordinating safely across cultural borders.</p>
            <div class="destinations-tags reveal">
                <div class="desti-tag">Japan</div>
                <div class="desti-tag">Kenya</div>
                <div class="desti-tag">Switzerland</div>
                <div class="desti-tag">Tanzania</div>
                <div class="desti-tag">Norway</div>
                <div class="desti-tag">Iceland</div>
                <div class="desti-tag">Germany</div>
                <div class="desti-tag">Nepal</div>
                <div class="desti-tag">China</div>
                <div class="desti-tag">Indonesia</div>
                <div class="desti-tag">South Africa</div>
                <div class="desti-tag">Portugal</div>
                <div class="desti-tag">Uganda</div>
                <div class="desti-tag">Greece</div>
            </div>
        </div>
    </section>

    <!-- MOST POPULAR PACKAGES SYSTEM -->
    <section id="packages" class="packages-section">
        <div class="container">
            <h2 class="section-title reveal">FEATURED MOUNTAIN TREKS & ADVENTURES</h2>
            <p class="section-subtitle reveal">Expertly engineered itineraries balancing technical challenge, local cultural integration, and optimal acclimatization management protocols.</p>
            
            <div class="packages-grid">
                <!-- Card 1 -->
                <div class="package-card reveal">
                    <div class="package-img pkg-1">
                        <span class="package-badge">12 Days</span>
                    </div>
                    <div class="package-content">
                        <h3 class="package-title">Mount Kilimanjaro Trek & Safari Adventure</h3>
                        <div class="package-meta">
                            <div class="package-price">Enquire <span>/ Custom Price</span></div>
                            <a href="#planner" class="btn btn-outline" style="padding: 0.4rem 1rem; font-size: 0.9rem;">Details</a>
                        </div>
                    </div>
                </div>
                <!-- Card 2 -->
                <div class="package-card reveal">
                    <div class="package-img pkg-2">
                        <span class="package-badge">7 Days</span>
                    </div>
                    <div class="package-content">
                        <h3 class="package-title">Japan: Mt. Fuji Trekking & Cultural Experience</h3>
                        <div class="package-meta">
                            <div class="package-price">Enquire <span>/ Custom Price</span></div>
                            <a href="#planner" class="btn btn-outline" style="padding: 0.4rem 1rem; font-size: 0.9rem;">Details</a>
                        </div>
                    </div>
                </div>
                <!-- Card 3 -->
                <div class="package-card reveal">
                    <div class="package-img pkg-3">
                        <span class="package-badge">7 Days</span>
                    </div>
                    <div class="package-content">
                        <h3 class="package-title">Mount Kinabalu – Summit Adventure</h3>
                        <div class="package-meta">
                            <div class="package-price">Enquire <span>/ Custom Price</span></div>
                            <a href="#planner" class="btn btn-outline" style="padding: 0.4rem 1rem; font-size: 0.9rem;">Details</a>
                        </div>
                    </div>
                </div>
                <!-- Card 4 -->
                <div class="package-card reveal">
                    <div class="package-img pkg-4">
                        <span class="package-badge">7 Days</span>
                    </div>
                    <div class="package-content">
                        <h3 class="package-title">Mount Toubkal – High Atlas Expedition</h3>
                        <div class="package-meta">
                            <div class="package-price">Enquire <span>/ Custom Price</span></div>
                            <a href="#planner" class="btn btn-outline" style="padding: 0.4rem 1rem; font-size: 0.9rem;">Details</a>
                        </div>
                    </div>
                </div>
                <!-- Card 5 -->
                <div class="package-card reveal">
                    <div class="package-img pkg-5">
                        <span class="package-badge">10 Days</span>
                    </div>
                    <div class="package-content">
                        <h3 class="package-title">Everest Base Camp Trek - Summit Leaders</h3>
                        <div class="package-meta">
                            <div class="package-price">Enquire <span>/ Custom Price</span></div>
                            <a href="#planner" class="btn btn-outline" style="padding: 0.4rem 1rem; font-size: 0.9rem;">Details</a>
                        </div>
                    </div>
                </div>
                <!-- Card 6 -->
                <div class="package-card reveal">
                    <div class="package-img pkg-6">
                        <span class="package-badge">7 Days</span>
                    </div>
                    <div class="package-content">
                        <h3 class="package-title">Drakensberg Mountains Trek (South Africa)</h3>
                        <div class="package-meta">
                            <div class="package-price">Enquire <span>/ Custom Price</span></div>
                            <a href="#planner" class="btn btn-outline" style="padding: 0.4rem 1rem; font-size: 0.9rem;">Details</a>
                        </div>
                    </div>
                </div>
                <!-- Card 7 -->
                <div class="package-card reveal">
                    <div class="package-img pkg-7">
                        <span class="package-badge">7 Days</span>
                    </div>
                    <div class="package-content">
                        <h3 class="package-title">Niseko Grand Hirafu Ski Adventure</h3>
                        <div class="package-meta">
                            <div class="package-price">Enquire <span>/ Custom Price</span></div>
                            <a href="#planner" class="btn btn-outline" style="padding: 0.4rem 1rem; font-size: 0.9rem;">Details</a>
                        </div>
                    </div>
                </div>
                <!-- Card 8 -->
                <div class="package-card reveal">
                    <div class="package-img pkg-8">
                        <span class="package-badge">7 Days</span>
                    </div>
                    <div class="package-content">
                        <h3 class="package-title">Great Wall Trek & Beijing Exploration</h3>
                        <div class="package-meta">
                            <div class="package-price">Enquire <span>/ Custom Price</span></div>
                            <a href="#planner" class="btn btn-outline" style="padding: 0.4rem 1rem; font-size: 0.9rem;">Details</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- UNLOCK LEADERSHIP PROGRAMME PROMO -->
    <section class="promo-banner">
        <div class="container">
            <div class="promo-content reveal">
                <span class="promo-tag">Unlock Your Leadership Potential</span>
                <h2>SUMMIT LEADERS STUDENT PROGRAM</h2>
                <p>Sign up your school or educational group for our structured youth development framework. Transform outdoor wilderness milestones into character building, team operational fluidness, and grit.</p>
                <a href="#planner" class="btn btn-primary">Secure School Spots Today</a>
            </div>
        </div>
    </section>

    <!-- DETAILED LEADERSHIP VALUE PILLARS -->
    <section id="program" class="program-section">
        <div class="container">
            <div class="program-showcase">
                <div class="reveal">
                    <h2 class="display-font" style="font-size: 3.5rem; color: var(--white); margin-bottom: 1.5rem; line-height: 1;">A JOURNEY OF CHARACTER & MENTAL TRANSFORMATION</h2>
                    <p style="color: var(--ice-blue); font-weight:300; margin-bottom: 2rem;">Designed specifically for international students and active academic institutions, these transformative trekking structures enhance resilience, personal confidence, and baseline critical team alignment capabilities under calculated real-world conditions.</p>
                    <a href="#planner" class="btn btn-outline">Enquire for Group Rates</a>
                </div>
                <div class="program-features">
                    <div class="feature-card reveal">
                        <i class="fa-solid fa-shield-halved feature-icon"></i>
                        <h3>Safety First</h3>
                        <p>Industry-best satellite asset configurations, emergency mitigation routes, and highly certified wilderness response guides.</p>
                    </div>
                    <div class="feature-card reveal">
                        <i class="fa-solid fa-users-gear feature-icon"></i>
                        <h3>Team Building</h3>
                        <p>Reflective student debrief modules that contextualize physical climbing strain into active real-world leadership traits.</p>
                    </div>
                    <div class="feature-card reveal">
                        <i class="fa-solid fa-compass feature-icon"></i>
                        <h3>True Adventure</h3>
                        <p>Immerse student cohorts deeply into pristine environments, pristine mountain paths, and local regional global cultures.</p>
                    </div>
                    <div class="feature-card reveal">
                        <i class="fa-solid fa-camera-retro feature-icon"></i>
                        <h3>Lasting Memories</h3>
                        <p>Unique team bonding milestones tracked organically across extraordinary high-altitude global photography trails.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- THE APEX INSIGHTS BLOG HUB -->
    <section id="blog" class="blog-section">
        <div class="container">
            <h2 class="section-title reveal">THE APEX HUB FOR EXPLORATION</h2>
            <p class="section-subtitle reveal">Actionable technical resources, mental conditioning strategies, and structural journals from our ongoing international climbs.</p>
            
            <div class="blog-grid">
                <div class="blog-card reveal">
                    <div class="blog-info">
                        <div class="blog-meta">Sanaa Rajkumar &bull; Mar 10, 2025</div>
                        <h3 class="blog-title">Conquer Kilimanjaro: The Ultimate Guide to Trekking Africa's Highest Peak</h3>
                        <a href="#planner" class="blog-link">Read Full Guide <i class="fa-solid fa-arrow-right-long"></i></a>
                    </div>
                </div>
                <div class="blog-card reveal">
                    <div class="blog-info">
                        <div class="blog-meta">Sanaa Rajkumar &bull; Oct 6, 2024</div>
                        <h3 class="blog-title">Global Mountain Trekking Adventures for High School Cohorts</h3>
                        <a href="#planner" class="blog-link">Read Full Guide <i class="fa-solid fa-arrow-right-long"></i></a>
                    </div>
                </div>
                <div class="blog-card reveal">
                    <div class="blog-info">
                        <div class="blog-meta">Sanaa Rajkumar &bull; Oct 6, 2024</div>
                        <h3 class="blog-title">Solo Mountain Expedition Tours Worldwide: Safe Strategy Frameworks</h3>
                        <a href="#planner" class="blog-link">Read Full Guide <i class="fa-solid fa-arrow-right-long"></i></a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CORE PREMIUM FOOTER MODULE -->
    <footer>
        <div class="container">
            <div class="footer-grid">
                <div class="footer-brand">
                    <a href="#" class="logo">
                        <i class="fa-solid fa-mountain-sun"></i> APEX <span>SUMMIT TRAILS</span>
                    </a>
                    <p>Conquer New Heights, Explore the World. Global leaders in highly structured premium youth expeditions and high-altitude trekking experiences.</p>
                    <div class="social-row">
                        <a href="#" class="social-icon"><i class="fa-brands fa-instagram"></i></a>
                        <a href="#" class="social-icon"><i class="fa-brands fa-facebook-f"></i></a>
                        <a href="#" class="social-icon"><i class="fa-brands fa-linkedin-in"></i></a>
                        <a href="#" class="social-icon"><i class="fa-brands fa-x-twitter"></i></a>
                    </div>
                </div>
                <div class="footer-col">
                    <h4>Quick Links</h4>
                    <ul>
                        <li><a href="#">Home</a></li>
                        <li><a href="#planner">About Us</a></li>
                        <li><a href="#destinations">Our Destinations</a></li>
                        <li><a href="#packages">Book Your Tour</a></li>
                        <li><a href="#planner">Contact Us</a></li>
                    </ul>
                </div>
                <div class="footer-col">
                    <h4>Our Programs</h4>
                    <ul>
                        <li><a href="#program">Summit Leaders Student Program</a></li>
                        <li><a href="#packages">High Altitude Trekking</a></li>
                        <li><a href="#planner">Visa & Logistics Assistance</a></li>
                        <li><a href="#blog">The Apex Travel Blog</a></li>
                        <li><a href="#planner">Request Custom Quote</a></li>
                    </ul>
                </div>
                <div class="footer-col">
                    <h4>Global HQs</h4>
                    <p style="font-size: 0.95rem; color: var(--ice-blue); font-weight: 300; margin-bottom: 0.5rem;">Cape Town, South Africa</p>
                    <p style="font-size: 0.95rem; color: var(--ice-blue); font-weight: 300;">Chamonix, France</p>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2026 Apex Summit Trails. All Rights Reserved.</p>
                <p>Designed strictly via Design Plan Token Configurations.</p>
            </div>
        </div>
    </footer>

    <!-- INTERACTIVE MOTION SCRIPTING -->
    <script>
        // Multi-Layer Custom Parallax Computation Engine
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const layers = document.querySelectorAll('.parallax-layer');
            
            layers.forEach(layer => {
                const speed = layer.getAttribute('data-speed');
                const yPos = -(scrolled * speed);
                layer.style.transform = `translateY(${yPos}px)`;
            });

            // Sticky Header Compression Animation Trigger
            const header = document.getElementById('main-header');
            if (scrolled > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });

        // Dynamic Intersection Observer Element Entry Reveals
        const revealElements = document.querySelectorAll('.reveal');
        const revealObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if(entry.isIntersecting) {
                    entry.target.classList.add('active');
                }
            });
        }, {
            threshold: 0.1,
            rootMargin: "0px 0px -50px 0px"
        });

        revealElements.forEach(element => {
            revealObserver.observe(element);
        });

        // Mobile Responsiveness Side Navigation Drawer Toggle Control
        const mobileBtn = document.getElementById('mobile-btn');
        const navMenu = document.getElementById('nav-menu');

        mobileBtn.addEventListener('click', () => {
            navMenu.classList.toggle('active');
            const icon = mobileBtn.querySelector('i');
            if (navMenu.classList.contains('active')) {
                icon.className = 'fa-solid fa-xmark';
            } else {
                icon.className = 'fa-solid fa-bars';
            }
        });

        // Auto collapse menu after selecting target anchor link elements
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                navMenu.classList.remove('active');
                mobileBtn.querySelector('i').className = 'fa-solid fa-bars';
            });
        });
    </script>
</body>
</html>

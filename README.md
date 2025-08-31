
<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.vidstack.io/player/theme.css" />
    <link rel="stylesheet" href="https://cdn.vidstack.io/player/video.css" />
    
    <style>
        :root {
            --primary: #007bff; /* FanCode Blue */
            --primary-dark: #0056b3;
            --secondary: #e74c3c; /* FanCode Red for Live */
            --accent: #3498db; /* Blue for upcoming */
            --dark-bg: #1a1a2e;
            --dark-card: #2c2c40;
            --light-bg: #f5f7ff;
            --light-card: #ffffff;
            --text-light: #ffffff;
            --text-dark: #222233;
            --text-secondary: #a0a0c0;
            --success: #2ecc71;
            --warning: #f1c40f;
            --error: #e74c3c;
            --header-bg: rgba(26, 26, 46, 0.9);
            --footer-bg: rgba(26, 26, 46, 0.9);
            --glass-effect: rgba(44, 44, 64, 0.7);
            --glass-border: rgba(255, 255, 255, 0.15);
            --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.1);
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            --radius: 12px;
        }

        [data-theme="light"] {
            --dark-bg: var(--light-bg);
            --dark-card: var(--light-card);
            --text-light: var(--text-dark);
            --text-secondary: #666677;
            --header-bg: rgba(245, 247, 255, 0.9);
            --footer-bg: rgba(245, 247, 255, 0.9);
            --glass-effect: rgba(255, 255, 255, 0.7);
            --glass-border: rgba(0, 0, 0, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'SF Pro Display', -apple-system, BlinkMacSystemFont, sans-serif;
        }

        body {
            background-color: var(--dark-bg);
            color: var(--text-light);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Particle Background */
        #particles-js {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(135deg, #10101e 0%, #1a1a2e 100%);
        }

        [data-theme="light"] #particles-js {
            background: linear-gradient(135deg, #e0e5ff 0%, #f0f5ff 100%);
        }

        /* Header */
        header {
            background-color: var(--header-bg);
            padding: 0.8rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--glass-border);
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }

        .scrolled header {
            padding: 0.5rem 1.5rem;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .logo-container img {
            height: 42px;
            object-fit: contain;
            border-radius: 10px;
            transition: transform 0.3s ease;
        }

        .logo-container img:hover {
            transform: scale(1.08);
        }

        .gradient-text {
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-weight: 800;
            font-size: 1.8rem;
            letter-spacing: -0.5px;
        }

        .gradient-text span {
            color: var(--text-light);
            background: none;
            -webkit-background-clip: initial;
            background-clip: initial;
        }
        
        /* New Styles for Eagle Royal Text */
        .banner-text {
            font-size: 2em;
            font-weight: bold;
            letter-spacing: 2px;
            text-transform: uppercase;
            background: linear-gradient(120deg, #ff0000, #ff8c00, #ffff00, #008000, #0000ff, #4b0082, #9400d3);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: text-glow 5s linear infinite;
        }
        @keyframes text-glow {
            from { background-position: 0% center; }
            to { background-position: 200% center; }
        }

        .header-controls {
            display: flex;
            gap: 1rem;
        }

        .header-btn {
            background: var(--glass-effect);
            border: none;
            color: var(--text-light);
            width: 42px;
            height: 42px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.1rem;
            backdrop-filter: blur(5px);
            -webkit-backdrop-filter: blur(5px);
            transition: var(--transition);
            position: relative;
        }

        .header-btn:hover {
            background: rgba(255, 255, 255, 0.15);
            transform: scale(1.08);
        }

        .header-btn .badge {
            position: absolute;
            top: -5px;
            right: -5px;
            background: var(--primary);
            color: white;
            font-size: 0.6rem;
            width: 18px;
            height: 18px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }

        /* Search Container */
        .search-container {
            position: fixed;
            top: -100px;
            left: 0;
            width: 100%;
            padding: 1.2rem 2rem;
            background-color: var(--header-bg);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            z-index: 99;
            display: flex;
            gap: 1rem;
            transition: top 0.4s ease;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
        }

        .search-container.active {
            top: 70px;
        }

        #channelSearch {
            flex: 1;
            padding: 1rem 1.8rem;
            border-radius: 50px;
            border: 1px solid var(--glass-border);
            background: var(--glass-effect);
            color: var(--text-light);
            font-size: 1rem;
            outline: none;
            transition: var(--transition);
            backdrop-filter: blur(10px);
        }

        #channelSearch:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.2);
        }

        .close-search {
            background: none;
            border: none;
            color: var(--text-light);
            font-size: 1.5rem;
            cursor: pointer;
            width: 44px;
            height: 44px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            transition: var(--transition);
        }

        .close-search:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: rotate(90deg);
        }

        /* Main Content */
        main {
            flex: 1;
            padding: 2.5rem;
            max-width: 1600px;
            margin: 0 auto;
            width: 100%;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2.5rem;
        }

        .section-title {
            font-size: 2rem;
            font-weight: 700;
            position: relative;
            padding-bottom: 0.8rem;
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 60px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            border-radius: 2px;
        }

        .section-title i {
            color: var(--primary);
            font-size: 1.8rem;
        }

        .controls {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .category-filter select {
            padding: 0.7rem 1.2rem;
            border-radius: 50px;
            border: 1px solid var(--glass-border);
            background: var(--glass-effect);
            color: var(--text-light);
            font-size: 0.95rem;
            outline: none;
            cursor: pointer;
            backdrop-filter: blur(5px);
            transition: var(--transition);
        }

        .category-filter select:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.2);
        }

        .refresh-btn {
            background: var(--glass-effect);
            border: 1px solid var(--glass-border);
            color: var(--text-light);
            padding: 0.7rem 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.95rem;
            transition: var(--transition);
            backdrop-filter: blur(5px);
        }

        .refresh-btn:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-2px);
        }

        /* Tabs */
        .tabs {
            display: flex;
            gap: 1rem;
            margin-bottom: 2rem;
            padding: 0.5rem;
            background: var(--glass-effect);
            border-radius: 50px;
            backdrop-filter: blur(10px);
            max-width: fit-content;
            border: 1px solid var(--glass-border);
        }

        .tab {
            padding: 0.7rem 1.8rem;
            border-radius: 50px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 600;
            font-size: 0.95rem;
        }

        .tab.active {
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            color: white;
            box-shadow: 0 5px 15px rgba(0, 123, 255, 0.3);
        }
        
        .tab-icon {
            margin-right: 8px;
        }

        /* Match Grid */
        .match-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
        }

        .match-card {
            background: var(--dark-card);
            border-radius: var(--radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            cursor: pointer;
            transition: var(--transition);
            position: relative;
            transform: translateY(0);
            border: 1px solid var(--glass-border);
        }

        .match-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
            border-color: rgba(255, 255, 255, 0.2);
        }
        
        .match-image {
            width: 100%;
            height: 180px;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .match-card:hover .match-image {
            transform: scale(1.08);
        }

        .match-info {
            padding: 1.2rem;
        }

        .match-title {
            font-weight: 700;
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .teams-list {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-top: 10px;
        }
        
        .team-info {
            text-align: center;
            flex: 1;
        }
        
        .team-logo {
            width: 60px;
            height: 60px;
            object-fit: contain;
            transition: transform 0.3s ease;
        }
        
        .team-info:hover .team-logo {
            transform: scale(1.1);
        }

        .vs-text {
            font-weight: bold;
            font-size: 1.2em;
            color: var(--text-secondary);
            margin: 0 10px;
        }

        .status-badge {
            position: absolute;
            top: 12px;
            left: 12px;
            background: var(--error);
            color: white;
            font-size: 0.7rem;
            padding: 0.2rem 0.7rem;
            border-radius: 30px;
            font-weight: 700;
            z-index: 2;
            display: flex;
            align-items: center;
            gap: 0.3rem;
            text-transform: uppercase;
        }
        
        .status-badge.live {
            background-color: var(--error);
        }
        
        .status-badge.upcoming {
            background-color: var(--accent);
        }

        .live-indicator::before {
            content: '';
            width: 8px;
            height: 8px;
            background: white;
            border-radius: 50%;
            display: block;
            animation: pulse 1.5s infinite;
        }

        .watch-btn-group {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-top: 15px;
        }

        .watch-btn, .coming-soon-btn {
            border: none;
            padding: 10px 15px;
            border-radius: 50px;
            font-weight: bold;
            text-decoration: none;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .watch-btn {
            background: var(--secondary);
            color: white;
        }
        
        .watch-btn:hover {
            background: var(--primary-dark);
        }
        
        .coming-soon-btn {
            background: var(--dark-bg);
            color: var(--text-secondary);
            cursor: default;
        }
        
        .player-select-modal-content {
            background: var(--dark-card);
            padding: 2rem;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            text-align: center;
        }
        
        .player-select-modal-content h3 {
            margin-bottom: 1.5rem;
        }
        
        .player-options {
            display: flex;
            gap: 1rem;
            justify-content: center;
        }
        
        .player-option {
            background: var(--glass-effect);
            color: var(--text-light);
            padding: 1rem 2rem;
            border-radius: var(--radius);
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.5rem;
            border: 1px solid var(--glass-border);
        }
        
        .player-option:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-5px);
        }

        .player-option i {
            font-size: 2rem;
        }

        /* Loading Spinner */
        .loading-spinner {
            grid-column: 1 / -1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 1.5rem;
            padding: 4rem;
            min-height: 50vh;
        }

        .spinner-circle {
            width: 60px;
            height: 60px;
            border: 5px solid rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            border-top-color: var(--primary);
            animation: spin 1.2s linear infinite;
        }

        .spinner-text {
            font-size: 1.1rem;
            color: var(--text-light);
            opacity: 0.8;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        @keyframes pulse {
            0% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.1); opacity: 0.7; }
            100% { transform: scale(1); opacity: 1; }
        }

        /* Footer */
        footer {
            background-color: var(--footer-bg);
            padding: 2rem;
            text-align: center;
            margin-top: auto;
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-top: 1px solid var(--glass-border);
        }

        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 1.5rem;
        }

        .social-links {
            display: flex;
            gap: 1.5rem;
        }

        .social-link {
            color: var(--text-light);
            font-size: 1.4rem;
            transition: var(--transition);
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background: var(--glass-effect);
            backdrop-filter: blur(5px);
        }

        .social-link:hover {
            background: var(--primary);
            transform: translateY(-5px) scale(1.1);
            box-shadow: 0 8px 20px rgba(0, 123, 255, 0.4);
        }

        .copyright {
            font-size: 0.95rem;
            opacity: 0.7;
            max-width: 600px;
            line-height: 1.7;
        }

        /* Back to Top Button */
        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            background: var(--primary);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            opacity: 0;
            transform: translateY(20px);
            transition: var(--transition);
            z-index: 90;
            box-shadow: 0 5px 15px rgba(0, 123, 255, 0.4);
        }

        .back-to-top.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .back-to-top:hover {
            background: var(--primary-dark);
            transform: translateY(-3px);
        }

        /* Video Player Modal Styles */
        .dplayer-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: rgba(0, 0, 0, 0.95);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.4s ease, visibility 0.4s ease;
        }

        .dplayer-modal.active {
            opacity: 1;
            visibility: visible;
        }

        .dplayer-modal-content {
            position: relative;
            width: 90%;
            max-width: 1280px;
            height: 90%;
            max-height: 720px;
            background-color: var(--dark-card);
            border-radius: var(--radius);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
            border: 1px solid var(--glass-border);
        }
        
        .player-container {
            width: 100%;
            height: 100%;
            flex: 1;
            display: none;
        }

        .player-container.active {
            display: block;
        }

        .dplayer-header {
            padding: 1.2rem 1.5rem;
            background: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--glass-border);
        }

        .dplayer-channel-info {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .dplayer-channel-logo {
            width: 40px;
            height: 40px;
            border-radius: 8px;
            object-fit: cover;
        }

        .dplayer-channel-title {
            font-weight: 700;
            font-size: 1.2rem;
        }

        .dplayer-close-btn {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            font-size: 1.5rem;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: var(--transition);
        }

        .dplayer-close-btn:hover {
            background: var(--primary);
            transform: rotate(90deg);
        }
        
        #player-container media-player {
            width: 100%;
            height: 100%;
            border-radius: 0;
        }
        
        #hls-player, #another-player {
            width: 100%;
            height: 100%;
            background-color: #000;
        }

        /* Toast Notifications */
        .toast {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: var(--dark-card);
            color: var(--text-light);
            padding: 1rem 2rem;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 1rem;
            z-index: 1000;
            opacity: 0;
            transition: transform 0.4s ease, opacity 0.4s ease;
            border-left: 4px solid var(--primary);
        }

        .toast.visible {
            transform: translateX(-50%) translateY(0);
            opacity: 1;
        }

        .toast i {
            color: var(--primary);
            font-size: 1.5rem;
        }

        /* Responsive Adjustments */
        @media (max-width: 1200px) {
            .match-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
        }

        @media (max-width: 992px) {
            main {
                padding: 2rem;
            }
            
            .match-grid {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
                gap: 1.5rem;
            }
        }

        @media (max-width: 768px) {
            header, .search-container {
                padding: 0.8rem 1.5rem;
            }

            main {
                padding: 1.5rem;
            }

            .section-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 1.2rem;
                margin-bottom: 2rem;
            }

            .controls {
                width: 100%;
                justify-content: space-between;
            }

            .match-grid {
                grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
                gap: 1.2rem;
            }

            .logo-container .banner-text {
                font-size: 1.5rem;
            }
            
            .dplayer-modal-content {
                width: 95%;
                height: 85%;
            }
        }

        @media (max-width: 576px) {
            .match-grid {
                grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
            }

            .tabs {
                width: 100%;
                overflow-x: auto;
                padding: 0.5rem;
                justify-content: flex-start;
            }
            
            .tab {
                padding: 0.6rem 1.2rem;
                font-size: 0.85rem;
                white-space: nowrap;
            }
            
            .back-to-top {
                bottom: 20px;
                right: 20px;
                width: 45px;
                height: 45px;
            }
            
            .player-options {
                flex-direction: column;
            }
        }

        /* Animations */
        .animate-pop-in {
            animation: popIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        @keyframes popIn {
            0% {
                opacity: 0;
                transform: scale(0.8) translateY(20px);
            }
            100% {
                opacity: 1;
                transform: scale(1) translateY(0);
            }
        }
    </style>
</head>
<body>
    <div id="particles-js"></div>
    
    <header class="animate__animated animate__fadeInDown">
        <div class="logo-container">
            <div style="background: linear-gradient(135deg, var(--primary), var(--secondary)); width: 42px; height: 42px; border-radius: 12px; display: flex; align-items: center; justify-content: center;">
                <i class="fas fa-bullseye" style="color: white; font-size: 1.4rem;"></i>
            </div>
            <h1 class="banner-text">Eagle Royal 🦅</h1>
        </div>
        <div class="header-controls">
            <button class="header-btn" id="themeToggle">
                <span id="themeIcon">🌙</span>
            </button>
            <button class="header-btn" id="searchToggle">
                <i class="fas fa-search"></i>
            </button>
        </div>
    </header>
    
    <div class="search-container" id="searchContainer">
        <input type="text" id="matchSearch" placeholder="Search matches...">
        <button class="close-search" id="closeSearch">
            <i class="fas fa-times"></i>
        </button>
    </div>
    
    <main class="animate__animated animate__fadeIn">
        <div class="section-header">
            <h2 class="section-title">
                <i class="fas fa-fire"></i>
                Live Matches
            </h2>
        </div>
        
        <div class="tabs">
            <div class="tab active" data-tab="live">
                <i class="fas fa-fire tab-icon"></i>
                Live
            </div>
            <div class="tab" data-tab="upcoming">
                <i class="fas fa-calendar-alt tab-icon"></i>
                Upcoming
            </div>
        </div>
        
        <div class="match-grid" id="matchGrid">
            <div class="loading-spinner">
                <div class="spinner-circle"></div>
                <div class="spinner-text">
                    Loading Matches...
                </div>
            </div>
        </div>
    </main>
    
    <footer class="animate__animated animate__fadeInUp">
        <div class="footer-content">
            <div class="social-links">
                <a href="https://t.me/EAGLEROYALM3u8" class="social-link" target="_blank">
                    <i class="fab fa-telegram"></i>
                </a>
                <a href="#" class="social-link">
                    <i class="fab fa-twitter"></i>
                </a>
                <a href="#" class="social-link">
                    <i class="fab fa-instagram"></i>
                </a>
                <a href="#" class="social-link">
                    <i class="fab fa-youtube"></i>
                </a>
            </div>
            <div class="copyright">
                © 2025 Eagle Royal. All rights reserved.<br>
                Experience the thrill of live sports with our premium streaming service.
            </div>
        </div>
    </footer>
    
    <div class="back-to-top" id="backToTop">
        <i class="fas fa-arrow-up"></i>
    </div>
    
    <div class="dplayer-modal" id="playerSelectModal">
        <div class="player-select-modal-content">
            <h3>Choose Your Player</h3>
            <div class="player-options">
                <div class="player-option" onclick="openPlayerModal('Vidstack')">
                    <i class="fas fa-play-circle"></i>
                    <span>Vidstack Player</span>
                </div>
                <div class="player-option" onclick="openPlayerModal('Hlsjs')">
                    <i class="fas fa-film"></i>
                    <span>Hls.js Player</span>
                </div>
                <div class="player-option" onclick="openPlayerModal('Another')">
                    <i class="fas fa-video"></i>
                    <span>Another Player</span>
                </div>
            </div>
        </div>
    </div>
    
    <div class="dplayer-modal" id="dplayerModal">
        <div class="dplayer-modal-content">
            <div class="dplayer-header">
                <div class="dplayer-channel-info">
                    <img src="" alt="Team Logo" class="dplayer-channel-logo" id="matchLogo">
                    <div class="dplayer-channel-title" id="matchTitle"></div>
                </div>
                <button class="dplayer-close-btn" id="dplayerCloseBtn">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            <div id="vidstack-player-container" class="player-container">
                <media-player id="vidstack-player" playsinline title="Eagle Royal Live" poster="https://files.vidstack.io/sprite-fight/poster.webp">
                    <media-provider></media-provider>
                    <media-video-layout></media-video-layout>
                </media-player>
            </div>
            <div id="hlsjs-player-container" class="player-container">
                <video id="hlsjs-player" controls autoplay playsinline></video>
            </div>
            <div id="another-player-container" class="player-container">
                <video id="another-player" controls autoplay playsinline></video>
            </div>
        </div>
    </div>
    
    <div class="toast" id="toast">
        <i class="fas fa-check-circle"></i>
        <div id="toastMessage">Match added to favorites!</div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
    <script src="https://cdn.vidstack.io/player" type="module"></script>
    <script src="https://cdn.jsdelivr.net/npm/hls.js@1.5.8/dist/hls.min.js"></script>

    <script>
        // Initialize particles.js background
        particlesJS("particles-js", {
            particles: {
                number: { value: 60, density: { enable: true, value_area: 800 } },
                color: { value: "#ffffff" },
                shape: { type: "circle" },
                opacity: { value: 0.1, random: true },
                size: { value: 3, random: true },
                line_linked: {
                    enable: true,
                    distance: 150,
                    color: "#ffffff",
                    opacity: 0.05,
                    width: 1
                },
                move: {
                    enable: true,
                    speed: 1,
                    direction: "none",
                    random: true,
                    straight: false,
                    out_mode: "out",
                    bounce: false
                }
            },
            interactivity: {
                detect_on: "canvas",
                events: {
                    onhover: { enable: true, mode: "repulse" },
                    onclick: { enable: true, mode: "push" },
                    resize: true
                }
            },
            retina_detect: true
        });

        // Data Source (Matches)
        const apiData = {
            "Author": "DOCTOR_STRANGE",
            "name": "FanCode Live Matches API",
            "last_updated": "02:46:45 PM 28-08-2025",
            "headers": {
                "User-Agent": "ReactNativeVideo/7.19.1 (Linux;Android/13) AndroidXMedia3/1.1.1",
                "Referer": "https://fancode.com/"
            },
            "total_matches": 39,
            "live_matches": 5,
            "upcoming_matches": 34,
            "website_info": {
                "banner_text": "Eagle Royal 🦅",
                "telegram_channel": "https://t.me/EAGLEROYALM3u8",
                "homepage_url": "https://fancode.com/"
            },
            "matches": [
                {
                    "category": "Cricket",
                    "title": "Kochi Blue Tigers Vs Adani Trivandrum Royals",
                    "tournament": "Kerala Cricket League, 2025",
                    "match_id": 133890,
                    "status": "LIVE",
                    "streamingStatus": "STARTED",
                    "startTime": "28 August 2025 02:30 PM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-Web_1756275176751.jpg",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/133890_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-Web_1756275176751.jpg",
                        "PLAYBACK": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-Web_1756275176751.jpg",
                        "LOGO": "https://www.fancode.com/skillup-uploads/cms-media/Kerala-Cricket-League-Tour-Logo-(1).png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-Web_1756275176751.jpg",
                        "SPORT_BY_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-App_1756275183162.jpg",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/133890_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "Kochi Blue Tigers",
                            "shortName": "KBT",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-KBT@2x.png"
                            },
                            "isWinner": null,
                            "color": "#01c0f6",
                            "cricketScore": [
                                {
                                    "runs": 39,
                                    "overs": "3.4",
                                    "balls": "22",
                                    "status": "IN_PROGRESS",
                                    "wickets": 0
                                }
                            ],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": true
                                }
                            }
                        },
                        {
                            "name": "Adani Trivandrum Royals",
                            "shortName": "TR",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-TRK@2x.png"
                            },
                            "isWinner": null,
                            "color": "#74B8E1",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        }
                    ],
                    "language": "ENGLISH",
                    "adfree_stream": "https://in-mc-fdlive.fancode.com/mumbai/133890_english_hls_6a57cd7a3d63018ta-di_h264/index.m3u8",
                    "dai_stream": "https://dai.google.com/linear/hls/event/d7DZVmOpRQmPysTzLvkgcQ/master.m3u8",
                    "streaming_options": [
                        {
                            "label": "English Stream",
                            "url": "https://in-mc-fdlive.fancode.com/mumbai/132361_english_hls_75c67fcb9123457ta-di_h264/index.m3u8"
                        },
                        {
                            "label": "Hindi AI Stream",
                            "url": "https://in-mc-fdlive.fancode.com/mumbai/132361_hindi_hls_62f932e94986383ta-di_h264/index.m3u8"
                        }
                    ]
                },
                {
                    "category": "Cricket",
                    "title": "Kochi Blue Tigers Vs Adani Trivandrum Royals",
                    "tournament": "Kerala Cricket League, 2025",
                    "match_id": 133890,
                    "status": "LIVE",
                    "streamingStatus": "STARTED",
                    "startTime": "28 August 2025 02:30 PM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-Web_1756275176751.jpg",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/133890_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-Web_1756275176751.jpg",
                        "PLAYBACK": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-Web_1756275176751.jpg",
                        "LOGO": "https://www.fancode.com/skillup-uploads/cms-media/Kerala-Cricket-League-Tour-Logo-(1).png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-Web_1756275176751.jpg",
                        "SPORT_BY_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/133890_5600_KBT_TR_fc-App_1755807588935.jpg",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/133890_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "Kochi Blue Tigers",
                            "shortName": "KBT",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-KBT@2x.png"
                            },
                            "isWinner": null,
                            "color": "#01c0f6",
                            "cricketScore": [
                                {
                                    "runs": 39,
                                    "overs": "3.4",
                                    "balls": "22",
                                    "status": "IN_PROGRESS",
                                    "wickets": 0
                                }
                            ],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": true
                                }
                            }
                        },
                        {
                            "name": "Adani Trivandrum Royals",
                            "shortName": "TR",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-TRK@2x.png"
                            },
                            "isWinner": null,
                            "color": "#74B8E1",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        }
                    ],
                    "language": "MALAYALAM",
                    "adfree_stream": "https://in-mc-fdlive.fancode.com/mumbai/133890_malayalam_hls_69606395a164394ta-di_h264/index.m3u8",
                    "dai_stream": "https://dai.google.com/linear/hls/event/8f_tTEKKRXq6JBby5r3TZA/master.m3u8",
                    "STREAMING_CDN": {
                        "Primary_Playback_URL": "https://in-mc-fdlive.fancode.com/mumbai/133890_malayalam_hls_69606395a164394ta-di_h264/index.m3u8",
                        "fancode_cdn": "https://in-mc-fdlive.fancode.com/mumbai/133890_malayalam_hls_69606395a164394ta-di_h264/index.m3u8",
                        "dai_google_cdn": "https://dai.google.com/linear/hls/event/8f_tTEKKRXq6JBby5r3TZA/master.m3u8",
                        "cloudfront_cdn": "Unavailable",
                        "language": "MALAYALAM"
                    }
                },
                {
                    "category": "Cricket",
                    "title": "Chandigarh Kings Vs Altruistian",
                    "tournament": "Chandigarh Premier League T20 Tournament, 2025",
                    "match_id": 136207,
                    "status": "LIVE",
                    "streamingStatus": "STARTED",
                    "startTime": "28 August 2025 10:00 AM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://images.fancode.com/aig/match/v1/136207_CASACARDS_APP.png",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/136207_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://images.fancode.com/aig/match/v1/136207_CASACARDS_APP.png",
                        "PLAYBACK": "https://images.fancode.com/aig/match/v1/136207_CASACARDS_APP.png",
                        "LOGO": "https://www.fancode.com/skillup-uploads/cms-media/Chandigarh-premier-league.png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://images.fancode.com/aig/match/v1/136207_CASACARDS_APP.png",
                        "SPORT_BY_IMAGE": "https://images.fancode.com/aig/match/v1/136207_CASACARDS_SPORTY_APP.png",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/136207_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "Chandigarh Kings",
                            "shortName": "CST",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-CCST@2x.png"
                            },
                            "isWinner": true,
                            "color": "#B8142D",
                            "cricketScore": [
                                {
                                    "runs": 158,
                                    "overs": "15",
                                    "balls": "90",
                                    "status": "COMPLETED",
                                    "wickets": 4
                                }
                            ],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        },
                        {
                            "name": "Altruistian",
                            "shortName": "ALT",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-ALT@2x.png"
                            },
                            "isWinner": false,
                            "color": "#B8142D",
                            "cricketScore": [
                                {
                                    "runs": 140,
                                    "overs": "15",
                                    "balls": "90",
                                    "status": "IN_PROGRESS",
                                    "wickets": 6
                                }
                            ],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": true
                                }
                            }
                        }
                    ],
                    "language": "ENGLISH",
                    "adfree_stream": "https://in-mc-fdlive.fancode.com/mumbai/136207_english_hls_574928817b94826ta-di_h264/index.m3u8",
                    "dai_stream": "https://dai.google.com/linear/hls/event/FX5siArUT1mWzJGLc75anw/master.m3u8",
                    "STREAMING_CDN": {
                        "Primary_Playback_URL": "https://in-mc-fdlive.fancode.com/mumbai/136207_english_hls_574928817b94826ta-di_h264/index.m3u8",
                        "fancode_cdn": "https://in-mc-fdlive.fancode.com/mumbai/136207_english_hls_574928817b94826ta-di_h264/index.m3u8",
                        "dai_google_cdn": "https://dai.google.com/linear/hls/event/FX5siArUT1mWzJGLc75anw/master.m3u8",
                        "cloudfront_cdn": "Unavailable",
                        "language": "ENGLISH"
                    }
                },
                {
                    "category": "Cricket",
                    "title": "Dr Morepen Dazzlers Vs Capital Strikers",
                    "tournament": "Chandigarh Premier League T20 Tournament, 2025",
                    "match_id": 136208,
                    "status": "LIVE",
                    "streamingStatus": "STARTED",
                    "startTime": "28 August 2025 02:15 PM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/136208_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "PLAYBACK": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "LOGO": "https://www.fancode.com/skillup-uploads/cms-media/Chandigarh-premier-league.png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "SPORT_BY_IMAGE": "https://fancode.com/skillup-uploads/prod-images/2023/08/FC_Sports_Default_cricket.jpg",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/136208_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "Dr Morepen Dazzlers",
                            "shortName": "DMD",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-DMD@2x.png"
                            },
                            "isWinner": null,
                            "color": "#ABD5FF",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        },
                        {
                            "name": "Capital Strikers",
                            "shortName": "CST",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-CTS@2x.png"
                            },
                            "isWinner": null,
                            "color": "#B8142D",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        }
                    ],
                    "language": "ENGLISH",
                    "adfree_stream": "https://in-mc-fdlive.fancode.com/mumbai/136208_english_hls_8ff98f68db26014ta-di_h264/index.m3u8",
                    "dai_stream": "https://dai.google.com/linear/hls/event/JGcXbby6Sua40SkBq1WE3Q/master.m3u8",
                    "STREAMING_CDN": {
                        "Primary_Playback_URL": "https://in-mc-fdlive.fancode.com/mumbai/136208_english_hls_8ff98f68db26014ta-di_h264/index.m3u8",
                        "fancode_cdn": "https://in-mc-fdlive.fancode.com/mumbai/136208_english_hls_8ff98f68db26014ta-di_h264/index.m3u8",
                        "dai_google_cdn": "https://dai.google.com/linear/hls/event/JGcXbby6Sua40SkBq1WE3Q/master.m3u8",
                        "cloudfront_cdn": "Unavailable",
                        "language": "ENGLISH"
                    }
                },
                {
                    "category": "Cricket",
                    "title": "University Of Queensland Vs Wynnum Manly",
                    "tournament": "KFC T20 Max, 2025",
                    "match_id": 134899,
                    "status": "LIVE",
                    "streamingStatus": "STARTED",
                    "startTime": "28 August 2025 02:00 PM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://www.fancode.com/skillup-uploads/cms-media/134899_5623_UOQ_WYN_Fc-Web_1755807575943.jpg",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/134899_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://www.fancode.com/skillup-uploads/cms-media/134899_5623_UOQ_WYN_Fc-Web_1755807575943.jpg",
                        "PLAYBACK": "https://www.fancode.com/skillup-uploads/cms-media/134899_5623_UOQ_WYN_Fc-Web_1755807575943.jpg",
                        "LOGO": "https://fancode.com/skillup-uploads/prod-images/2024/08/KFC-T20-Max-Competition-2024-Tour-Logo.png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/134899_5623_UOQ_WYN_Fc-Web_1755807575943.jpg",
                        "SPORT_BY_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/134899_5623_UOQ_WYN_FC-App_1755807588935.jpg",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/134899_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "University Of Queensland",
                            "shortName": "UOQ",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-UOQ@2x.png"
                            },
                            "isWinner": null,
                            "color": "#dfa61e",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        },
                        {
                            "name": "Wynnum-Manly",
                            "shortName": "WYN",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-WYN@2x.png"
                            },
                            "isWinner": null,
                            "color": "#FFFFFF",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        }
                    ],
                    "language": "ENGLISH",
                    "adfree_stream": "https://in-mc-fdlive.fancode.com/mumbai/134899_english_hls_88bef0bf1c63714ta-di_h264/index.m3u8",
                    "dai_stream": "Unavailable",
                    "STREAMING_CDN": {
                        "Primary_Playback_URL": "https://in-mc-fdlive.fancode.com/mumbai/134899_english_hls_88bef0bf1c63714ta-di_h264/index.m3u8",
                        "fancode_cdn": "https://in-mc-fdlive.fancode.com/mumbai/134899_english_hls_88bef0bf1c63714ta-di_h264/index.m3u8",
                        "dai_google_cdn": "Unavailable",
                        "cloudfront_cdn": "Unavailable",
                        "language": "ENGLISH"
                    }
                },
                {
                    "category": "Cricket",
                    "title": "Hubli Tigers Vs Mangaluru Dragons",
                    "tournament": "Maharaja T20 Trophy, 2025",
                    "match_id": 132818,
                    "status": "NOT_STARTED",
                    "streamingStatus": "NOT_STARTED",
                    "startTime": "28 August 2025 06:30 PM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://www.fancode.com/skillup-uploads/cms-media/132794_5530_HT_MD_fc-Web_1755374792921.jpg",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/132818_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://www.fancode.com/skillup-uploads/cms-media/132794_5530_HT_MD_fc-Web_1755374792921.jpg",
                        "PLAYBACK": null,
                        "LOGO": "https://fancode.com/skillup-uploads/prod-images/2024/07/Maharaja-Trophy-KSCA-T20-Tour-Logo.png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/132794_5530_HT_MD_fc-Web_1755374792921.jpg",
                        "SPORT_BY_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/132794_5530_HT_MD_fc-App_1755374802483.jpg",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/132818_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "Hubli Tigers",
                            "shortName": "HT",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-HBT@2x.png"
                            },
                            "isWinner": null,
                            "color": "#272993",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        },
                        {
                            "name": "Mangaluru Dragons",
                            "shortName": "MD",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-MDR@2x.png"
                            },
                            "isWinner": null,
                            "color": "#fea129",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        }
                    ],
                    "language": "BLOODY_SWEET",
                    "adfree_stream": null,
                    "dai_stream": null,
                    "STREAMING_CDN": {
                        "language": "BLOODY_SWEET",
                        "Primary_Playback_URL": null
                    }
                },
                {
                    "category": "Cricket",
                    "title": "Aries Kollam Sailors Vs Alleppey Ripples",
                    "tournament": "Kerala Cricket League, 2025",
                    "match_id": 133891,
                    "status": "NOT_STARTED",
                    "streamingStatus": "NOT_STARTED",
                    "startTime": "28 August 2025 06:45 PM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://www.fancode.com/skillup-uploads/cms-media/133891_5600_AKS_AP_fc-Web_1756275176709.jpg",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/133891_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://www.fancode.com/skillup-uploads/cms-media/133891_5600_AKS_AP_fc-Web_1756275176709.jpg",
                        "PLAYBACK": null,
                        "LOGO": "https://www.fancode.com/skillup-uploads/cms-media/Kerala-Cricket-League-Tour-Logo-(1).png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/133891_5600_AKS_AP_fc-Web_1756275176709.jpg",
                        "SPORT_BY_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/133891_5600_AKS_AP_fc-App_1756275182366.jpg",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/133891_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "Aries Kollam Sailors",
                            "shortName": "AKS",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-AKS@2x.png"
                            },
                            "isWinner": null,
                            "color": "#b7e330",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        },
                        {
                            "name": "Alleppey Ripples",
                            "shortName": "AP",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-APK@2x.png"
                            },
                            "isWinner": null,
                            "color": "#8e5bf0",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        }
                    ],
                    "language": "BLOODY_SWEET",
                    "adfree_stream": null,
                    "dai_stream": null,
                    "STREAMING_CDN": {
                        "language": "BLOODY_SWEET",
                        "Primary_Playback_URL": null
                    }
                },
                {
                    "category": "Cricket",
                    "title": "North Delhi Strikers Vs New Delhi Tigers",
                    "tournament": "Delhi Premier League, 2025",
                    "match_id": 132503,
                    "status": "NOT_STARTED",
                    "streamingStatus": "NOT_STARTED",
                    "startTime": "28 August 2025 07:00 PM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://www.fancode.com/skillup-uploads/cms-media/132503_5521_NDS_NDT_fc-Web.jpg",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/132503_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://www.fancode.com/skillup-uploads/cms-media/132503_5521_NDS_NDT_fc-Web.jpg",
                        "PLAYBACK": null,
                        "LOGO": "https://www.fancode.com/skillup-uploads/cms-media/DPL_Tour_Logo.png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/132503_5521_NDS_NDT_fc-Web.jpg",
                        "SPORT_BY_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/132503_5521_NDS_NDT_fc-App.jpg",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/132503_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "North Delhi Strikers",
                            "shortName": "NDS",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-NDS@2x.png"
                            },
                            "isWinner": null,
                            "color": "#4686c7",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        },
                        {
                            "name": "New Delhi Tigers",
                            "shortName": "NDT",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/NDT-CR2@2x.png"
                            },
                            "isWinner": null,
                            "color": "#B8142D",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        }
                    ],
                    "language": "BLOODY_SWEET",
                    "adfree_stream": null,
                    "dai_stream": null,
                    "STREAMING_CDN": {
                        "language": "BLOODY_SWEET",
                        "Primary_Playback_URL": null
                    }
                },
                {
                    "category": "Cricket",
                    "title": "Southern Brave Women Vs Welsh Fire Women",
                    "tournament": "The Hundred Women, 2025",
                    "match_id": 136190,
                    "status": "NOT_STARTED",
                    "streamingStatus": "NOT_STARTED",
                    "startTime": "28 August 2025 07:30 PM",
                    "startDate": "01 January 1970 05:30 AM",
                    "image": "https://www.fancode.com/skillup-uploads/cms-media/132287_5506_SOB-W_WEF-W_Fc-Web.jpg",
                    "image_cdn": {
                        "TATAPLAY": "https://images.fancode.com/aig/match/v1/136190_CASACARDS_PARTNER_16_9_1920_1080.png",
                        "APP": "https://www.fancode.com/skillup-uploads/cms-media/132287_5506_SOB-W_WEF-W_Fc-Web.jpg",
                        "PLAYBACK": null,
                        "LOGO": "https://fancode.com/skillup-uploads/prod-images/2024/06/The-Hundred_Tour-Logo.png",
                        "SPORTS": "https://www.fancode.com/skillup-uploads/cms-media/Cricket_Fallback_Old_match-card.jpg",
                        "BG_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/132287_5506_SOB-W_WEF-W_Fc-Web.jpg",
                        "SPORT_BY_IMAGE": "https://www.fancode.com/skillup-uploads/cms-media/132287_5506_SOB-W_WEF-W_Fc-App.jpg",
                        "CLOUDFARE": "https://d229kpbsb5jevy.cloudfront.net/vffancode2/aig/match/v1/136190_CASACARDS_PARTNER_16_9_1920_1080.png"
                    },
                    "teams": [
                        {
                            "name": "Southern Brave Women",
                            "shortName": "SOB-W",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-SOUTHB@2x.png"
                            },
                            "isWinner": null,
                            "color": "#97c8a5",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        },
                        {
                            "name": "Welsh Fire Women",
                            "shortName": "WEF-W",
                            "flag": {
                                "src": "https://d13ir53smqqeyp.cloudfront.net/flags/cr-flags/FC-WEF@2x.png"
                            },
                            "isWinner": null,
                            "color": "#e0544f",
                            "cricketScore": [],
                            "kabaddiScore": null,
                            "footballScore": null,
                            "basketBallScore": null,
                            "hockeyScore": null,
                            "status": {
                                "cricket": {
                                    "isBatting": false
                                }
                            }
                        }
                    ],
                    "language": "BLOODY_SWEET",
                    "adfree_stream": null,
                    "dai_stream": null,
                    "STREAMING_CDN": {
                        "language": "BLOODY_SWEET",
                        "Primary_Playback_URL": null
                    }
                }
            ]
        };

        // DOM Elements
        const elements = {
            themeToggle: document.getElementById('themeToggle'),
            themeIcon: document.getElementById('themeIcon'),
            searchToggle: document.getElementById('searchToggle'),
            closeSearch: document.getElementById('closeSearch'),
            searchContainer: document.getElementById('searchContainer'),
            matchSearch: document.getElementById('matchSearch'),
            matchGrid: document.getElementById('matchGrid'),
            html: document.documentElement,
            playerSelectModal: document.getElementById('playerSelectModal'),
            dplayerModal: document.getElementById('dplayerModal'),
            dplayerCloseBtn: document.getElementById('dplayerCloseBtn'),
            matchTitle: document.getElementById('matchTitle'),
            matchLogo: document.getElementById('matchLogo'),
            backToTop: document.getElementById('backToTop'),
            toast: document.getElementById('toast'),
            toastMessage: document.getElementById('toastMessage'),
            tabs: document.querySelectorAll('.tab'),
            vidstackPlayerContainer: document.getElementById('vidstack-player-container'),
            hlsjsPlayerContainer: document.getElementById('hlsjs-player-container'),
            anotherPlayerContainer: document.getElementById('another-player-container'),
            vidstackPlayer: document.getElementById('vidstack-player'),
            hlsjsPlayer: document.getElementById('hlsjs-player'),
            anotherPlayer: document.getElementById('another-player')
        };
        
        let hlsInstance = null;
        let currentTab = 'live';
        let currentStreamUrl = '';
        let currentMatchTitle = '';
        let currentMatchLogo = '';

        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            initTheme();
            initEventListeners();
            initScrollEffects();
            renderMatches(currentTab);
        });

        function initTheme() {
            const savedTheme = localStorage.getItem('theme') || 'dark';
            elements.html.setAttribute('data-theme', savedTheme);
            updateThemeIcon(savedTheme);
        }

        function initEventListeners() {
            elements.themeToggle.addEventListener('click', toggleTheme);
            elements.searchToggle.addEventListener('click', toggleSearch);
            elements.closeSearch.addEventListener('click', toggleSearch);
            elements.matchSearch.addEventListener('input', searchMatches);
            elements.dplayerCloseBtn.addEventListener('click', closePlayerModal);
            window.addEventListener('scroll', toggleBackToTop);
            elements.backToTop.addEventListener('click', () => window.scrollTo({ top: 0, behavior: 'smooth' }));

            elements.tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    elements.tabs.forEach(t => t.classList.remove('active'));
                    tab.classList.add('active');
                    currentTab = tab.getAttribute('data-tab');
                    renderMatches(currentTab);
                });
            });
        }

        function toggleTheme() {
            const currentTheme = elements.html.getAttribute('data-theme');
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            elements.html.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
            updateThemeIcon(newTheme);
        }

        function updateThemeIcon(theme) {
            elements.themeIcon.innerHTML = theme === 'dark' ? '🌙' : '☀️';
        }

        function toggleSearch() {
            elements.searchContainer.classList.toggle('active');
            if (elements.searchContainer.classList.contains('active')) {
                elements.matchSearch.focus();
            }
        }

        function toggleBackToTop() {
            if (window.scrollY > 300) {
                elements.backToTop.classList.add('visible');
            } else {
                elements.backToTop.classList.remove('visible');
            }
        }

        function initScrollEffects() {
            let lastScrollY = window.scrollY;
            window.addEventListener('scroll', () => {
                if (window.scrollY > lastScrollY) {
                    document.querySelector('header').classList.remove('scrolled');
                } else {
                    document.querySelector('header').classList.add('scrolled');
                }
                lastScrollY = window.scrollY;
            });
        }

        function renderMatches(tab) {
            elements.matchGrid.innerHTML = '';
            
            const filteredMatches = apiData.matches.filter(m => {
                if (tab === 'live') {
                    return m.status === 'LIVE';
                } else if (tab === 'upcoming') {
                    return m.status === 'NOT_STARTED';
                }
                return true;
            });

            if (filteredMatches.length === 0) {
                elements.matchGrid.innerHTML = `
                    <div class="loading-spinner">
                        <div class="spinner-text">No matches found.</div>
                    </div>
                `;
                return;
            }

            filteredMatches.forEach((match, index) => {
                const matchCard = createMatchCard(match);
                matchCard.style.animationDelay = `${index * 0.1}s`;
                elements.matchGrid.appendChild(matchCard);
            });
        }
        
        function createMatchCard(match) {
            const matchCard = document.createElement('div');
            matchCard.className = 'match-card animate-pop-in';
            
            const teams = match.teams.map(team => `
                <div class="team-info">
                    <img src="${team.flag.src}" alt="${team.shortName} Flag" class="team-logo">
                    <p class="team-name">${team.shortName}</p>
                </div>
            `).join('');

            const statusClass = match.status === 'LIVE' ? 'live' : 'upcoming';
            const statusText = match.status === 'LIVE' ? 'LIVE' : 'UPCOMING';

            let actionButtons = '';
            if (match.status === 'LIVE' && match.STREAMING_CDN && match.STREAMING_CDN.Primary_Playback_URL) {
                actionButtons = `<button class="watch-btn" onclick="showPlayerSelection('${match.STREAMING_CDN.Primary_Playback_URL}', '${match.title}', '${match.teams[0].flag.src}')">Watch Now</button>`;
            } else {
                actionButtons = `<button class="coming-soon-btn">Coming Soon</button>`;
            }

            matchCard.innerHTML = `
                <div class="match-thumbnail-container">
                    <img src="${match.image}" alt="${match.title}" class="match-image">
                    <span class="status-badge ${statusClass}">
                        <i class="fas fa-circle live-indicator"></i> ${statusText}
                    </span>
                </div>
                <div class="match-info">
                    <h3 class="match-title">${match.title}</h3>
                    <div class="teams-list">
                        ${teams}
                    </div>
                    <div class="watch-btn-group">
                        ${actionButtons}
                    </div>
                </div>
            `;
            return matchCard;
        }
        
        function showPlayerSelection(url, title, logo) {
            currentStreamUrl = url;
            currentMatchTitle = title;
            currentMatchLogo = logo;
            elements.playerSelectModal.classList.add('active');
        }

        function openPlayerModal(playerType) {
            elements.playerSelectModal.classList.remove('active');
            elements.dplayerModal.classList.add('active');
            
            elements.matchTitle.textContent = currentMatchTitle;
            elements.matchLogo.src = currentMatchLogo;

            // Hide all players
            elements.vidstackPlayerContainer.classList.remove('active');
            elements.hlsjsPlayerContainer.classList.remove('active');
            elements.anotherPlayerContainer.classList.remove('active');

            // Reset all players
            const allPlayers = [elements.vidstackPlayer, elements.hlsjsPlayer, elements.anotherPlayer];
            allPlayers.forEach(player => {
                if (player) {
                    player.pause();
                    player.src = '';
                }
            });
            if (hlsInstance) {
                hlsInstance.destroy();
                hlsInstance = null;
            }

            // Show and initialize the selected player
            if (playerType === 'Vidstack') {
                elements.vidstackPlayerContainer.classList.add('active');
                playVidstack(currentStreamUrl);
            } else if (playerType === 'Hlsjs') {
                elements.hlsjsPlayerContainer.classList.add('active');
                playHlsjs(currentStreamUrl);
            } else if (playerType === 'Another') {
                elements.anotherPlayerContainer.classList.add('active');
                playAnother(currentStreamUrl);
            }
        }

        async function playVidstack(url) {
            await customElements.whenDefined('media-player');
            const mediaProvider = elements.vidstackPlayer.querySelector('media-provider');
            if (Hls.isSupported() && url.endsWith('.m3u8')) {
                // Vidstack automatically handles HLS with Hls.js
                elements.vidstackPlayer.src = url;
            } else {
                elements.vidstackPlayer.src = url;
            }
            elements.vidstackPlayer.play();
        }

        function playHlsjs(url) {
            if (Hls.isSupported()) {
                hlsInstance = new Hls({
                    pLoader: function(config) {
                        const loader = new Hls.DefaultConfig.loader(config);
                        loader.load = function(context, callbacks, data) {
                            context.headers = apiData.headers;
                            return Hls.DefaultConfig.loader.prototype.load.call(this, context, callbacks, data);
                        };
                        return loader;
                    }
                });
                hlsInstance.loadSource(url);
                hlsInstance.attachMedia(elements.hlsjsPlayer);
                hlsInstance.on(Hls.Events.MANIFEST_PARSED, function() {
                    elements.hlsjsPlayer.play();
                });
            } else if (elements.hlsjsPlayer.canPlayType('application/vnd.apple.mpegurl')) {
                elements.hlsjsPlayer.src = url;
                elements.hlsjsPlayer.play();
            }
        }
        
        function playAnother(url) {
            // This is a placeholder for a third player.
            // You can replace this with any other player library's logic.
            // For now, it will use the native HTML5 player.
            elements.anotherPlayer.src = url;
            elements.anotherPlayer.play();
        }

        function closePlayerModal() {
            elements.dplayerModal.classList.remove('active');
            
            // Stop and reset all players
            const allPlayers = [elements.vidstackPlayer, elements.hlsjsPlayer, elements.anotherPlayer];
            allPlayers.forEach(player => {
                if (player) {
                    player.pause();
                    player.src = '';
                }
            });

            if (hlsInstance) {
                hlsInstance.destroy();
                hlsInstance = null;
            }
        }
        
        function searchMatches(event) {
            const query = event.target.value.toLowerCase();
            const allMatchCards = document.querySelectorAll('.match-card');
            
            allMatchCards.forEach(card => {
                const title = card.querySelector('.match-title').textContent.toLowerCase();
                if (title.includes(query)) {
                    card.style.display = 'block';
                } else {
                    card.style.display = 'none';
                }
            });
        }
    </script>
</body>
</html>

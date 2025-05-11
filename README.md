<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WallHub - Premium Wallpapers</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f0f2f5;
            color: #333;
            overflow-x: hidden;
        }
        
        header {
            display: flex;
            justify-content: center;
            padding: 20px 0;
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .nav-container {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            border-radius: 50px;
            padding: 15px 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            display: flex;
            align-items: center;
            gap: 15px;
            width: auto;
            max-width: 800px;
        }
        
        .logo {
            font-weight: 700;
            font-size: 24px;
            color: #333;
            margin-right: 15px;
            display: flex;
            align-items: center;
        }
        
        .logo span {
            color: #4a6cf7;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
            gap: 10px;
        }
        
        .nav-links li {
            cursor: pointer;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: 500;
            transition: all 0.3s ease;
        }
        
        .nav-links li:hover {
            background-color: #f0f2f5;
        }
        
        .nav-links li.active {
            background-color: #4a6cf7;
            color: white;
        }
        
        .container {
            max-width: 1200px;
            margin: 20px auto;
            padding: 0 20px;
        }
        
        .section {
            display: none;
            animation: fadeIn 0.5s ease forwards;
        }
        
        .section.active {
            display: block;
        }
        
        h2 {
            font-size: 32px;
            margin-bottom: 30px;
            position: relative;
            padding-bottom: 10px;
        }
        
        h2::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            height: 4px;
            width: 60px;
            background-color: #4a6cf7;
            border-radius: 4px;
        }
        
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .wallpaper {
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            position: relative;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            aspect-ratio: 16/9;
        }
        
        .wallpaper:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }
        
        .wallpaper img, .wallpaper svg {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
        }
        
        .download-btn {
            position: absolute;
            bottom: 15px;
            right: 15px;
            background-color: rgba(255, 255, 255, 0.9);
            color: #333;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transform: translateY(10px);
            transition: all 0.3s ease;
            z-index: 10;
        }
        
        .wallpaper:hover .download-btn {
            opacity: 1;
            transform: translateY(0);
        }
        
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        /* Live wallpaper specific styles */
        .live-wallpaper {
            position: relative;
            overflow: hidden;
        }
        
        .live-wallpaper-1 {
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradient 15s ease infinite;
        }
        
        .live-wallpaper-2 {
            background: #000;
            overflow: hidden;
        }
        
        .live-wallpaper-2::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: conic-gradient(transparent, rgba(255, 255, 255, 0.4), transparent 30%);
            animation: rotate 4s linear infinite;
        }
        
        .live-wallpaper-3 {
            background: #0f0c29;
            background: linear-gradient(to right, #24243e, #302b63, #0f0c29);
        }
        
        .live-wallpaper-3::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background-image: radial-gradient(white 1px, transparent 1px);
            background-size: 30px 30px;
            animation: stars 3s linear infinite;
        }
        
        .live-wallpaper-4 {
            position: relative;
            background-color: #2c3e50;
            overflow: hidden;
        }
        
        .wave {
            position: absolute;
            width: 200%;
            height: 200px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: wave 3s ease-in-out infinite alternate;
        }
        
        .wave:nth-child(1) {
            bottom: -160px;
            animation-delay: 0s;
        }
        
        .wave:nth-child(2) {
            bottom: -190px;
            animation-delay: 0.5s;
        }
        
        .wave:nth-child(3) {
            bottom: -220px;
            animation-delay: 1s;
        }
        
        @keyframes gradient {
            0% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
            100% {
                background-position: 0% 50%;
            }
        }
        
        @keyframes rotate {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }
        
        @keyframes stars {
            0% {
                opacity: 0.1;
            }
            50% {
                opacity: 0.5;
            }
            100% {
                opacity: 0.1;
            }
        }
        
        @keyframes wave {
            0% {
                transform: translateX(-50%) scaleY(1);
            }
            100% {
                transform: translateX(-50%) scaleY(1.5);
            }
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        .modal.active {
            display: flex;
            opacity: 1;
        }
        
        .modal-content {
            max-width: 90%;
            max-height: 90%;
            position: relative;
        }
        
        .modal-content img, .modal-content svg {
            max-width: 100%;
            max-height: 90vh;
            display: block;
            border-radius: 10px;
            box-shadow: 0 5px 30px rgba(0, 0, 0, 0.3);
            background-color: white;
        }
        
        .close-modal {
            position: absolute;
            top: -40px;
            right: 0;
            color: white;
            font-size: 30px;
            cursor: pointer;
        }
        
        .welcome-section {
            text-align: center;
            padding: 80px 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            margin-bottom: 40px;
            border-radius: 20px;
        }
        
        .welcome-section h1 {
            font-size: 48px;
            margin-bottom: 20px;
        }
        
        .welcome-section p {
            font-size: 18px;
            max-width: 700px;
            margin: 0 auto 30px;
            opacity: 0.9;
        }
        
        .search-bar {
            max-width: 500px;
            margin: 0 auto;
            position: relative;
        }
        
        .search-bar input {
            width: 100%;
            padding: 15px 20px;
            border-radius: 30px;
            border: none;
            font-size: 16px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .search-bar button {
            position: absolute;
            right: 5px;
            top: 5px;
            background: #4a6cf7;
            color: white;
            border: none;
            border-radius: 30px;
            padding: 10px 20px;
            cursor: pointer;
        }
        
        /* Hide download links but make them functional */
        .download-link {
            position: absolute;
            opacity: 0;
            pointer-events: none;
        }
        
        /* Custom SVG patterns */
        .abstract-pattern-1 {
            background: 
                radial-gradient(circle at 80% 30%, #ff6b6b 0%, transparent 25%),
                radial-gradient(circle at 20% 70%, #4ecdc4 0%, transparent 25%),
                radial-gradient(circle at 50% 50%, #ffe66d 0%, transparent 40%);
            background-color: #3c3f58;
        }
        
        .abstract-pattern-2 {
            background-color: #2d4059;
            background-image: 
                linear-gradient(30deg, #ea5455 12%, transparent 12.5%, transparent 87%, #ea5455 87.5%, #ea5455),
                linear-gradient(150deg, #ea5455 12%, transparent 12.5%, transparent 87%, #ea5455 87.5%, #ea5455),
                linear-gradient(30deg, #ea5455 12%, transparent 12.5%, transparent 87%, #ea5455 87.5%, #ea5455),
                linear-gradient(150deg, #ea5455 12%, transparent 12.5%, transparent 87%, #ea5455 87.5%, #ea5455),
                linear-gradient(60deg, #ea545577 25%, transparent 25.5%, transparent 75%, #ea545577 75%, #ea545577);
            background-size: 80px 140px;
            background-position: 0 0, 0 0, 40px 70px, 40px 70px, 0 0;
        }
        
        .abstract-pattern-3 {
            background-color: #222831;
            background-image: 
                linear-gradient(0deg, rgba(244, 162, 97, 0.8) 50%, transparent 50%),
                linear-gradient(90deg, rgba(242, 132, 130, 0.8) 50%, transparent 50%);
            background-size: 40px 40px;
        }
        
        .abstract-pattern-4 {
            background: 
                linear-gradient(45deg, #00adb5 25%, transparent 25%) -50px 0,
                linear-gradient(135deg, #00adb5 25%, transparent 25%) -50px 0,
                linear-gradient(225deg, #00adb5 25%, transparent 25%) -50px 0,
                linear-gradient(315deg, #00adb5 25%, transparent 25%) -50px 0;
            background-color: #393e46;
            background-size: 100px 100px;
        }
        
        .cool-pattern-1 {
            background: 
                linear-gradient(45deg, #003049 25%, transparent 25%) -50px 0,
                linear-gradient(135deg, #003049 25%, transparent 25%) -50px 0,
                linear-gradient(225deg, #003049 25%, transparent 25%) -50px 0,
                linear-gradient(315deg, #003049 25%, transparent 25%) -50px 0;
            background-color: #d62828;
            background-size: 100px 100px;
        }
        
        .cool-pattern-2 {
            background-color: #118ab2;
            background-image: 
                linear-gradient(30deg, #073b4c 12%, transparent 12.5%, transparent 87%, #073b4c 87.5%, #073b4c),
                linear-gradient(150deg, #073b4c 12%, transparent 12.5%, transparent 87%, #073b4c 87.5%, #073b4c),
                linear-gradient(30deg, #073b4c 12%, transparent 12.5%, transparent 87%, #073b4c 87.5%, #073b4c),
                linear-gradient(150deg, #073b4c 12%, transparent 12.5%, transparent 87%, #073b4c 87.5%, #073b4c);
            background-size: 80px 140px;
            background-position: 0 0, 0 0, 40px 70px, 40px 70px;
        }
        
        .cool-pattern-3 {
            background: 
                linear-gradient(135deg, #0096c7 25%, transparent 25%) -50px 0,
                linear-gradient(225deg, #0096c7 25%, transparent 25%) -50px 0,
                linear-gradient(315deg, #0096c7 25%, transparent 25%) -50px 0,
                linear-gradient(45deg, #0096c7 25%, transparent 25%) -50px 0;
            background-color: #48cae4;
            background-size: 100px 100px;
        }
        
        .cool-pattern-4 {
            background: 
                radial-gradient(circle at 0% 50%, #023e8a 0%, transparent 50%),
                radial-gradient(circle at 100% 50%, #0077b6 0%, transparent 50%);
            background-color: #90e0ef;
        }
        
        .gradient-pattern-1 {
            background: linear-gradient(45deg, #001219, #005f73, #0a9396, #94d2bd);
        }
        
        .gradient-pattern-2 {
            background: linear-gradient(135deg, #9b5de5, #f15bb5, #fee440, #00bbf9, #00f5d4);
        }
        
        .gradient-pattern-3 {
            background: linear-gradient(to right, #12c2e9, #c471ed, #f64f59);
        }
        
        .gradient-pattern-4 {
            background: linear-gradient(to right, #2c3e50, #4ca1af);
        }
        
        .nature-pattern-1 {
            background-color: #52b788;
            background-image: 
                radial-gradient(circle at 50% 0, rgba(255, 255, 255, 0.5), rgba(0, 0, 0, 0) 70%),
                radial-gradient(circle at 6.7% 75%, rgba(255, 255, 255, 0.5), rgba(0, 0, 0, 0) 70%),
                radial-gradient(circle at 93.3% 75%, rgba(255, 255, 255, 0.5), rgba(0, 0, 0, 0) 70%);
            background-size: 50px 87px;
        }
        
        .nature-pattern-2 {
            background-color: #588157;
            background-image: 
                linear-gradient(90deg, transparent 79px, #3a5a40 79px, #3a5a40 81px, transparent 81px),
                linear-gradient(#3a5a40 79px, transparent 79px, transparent 81px, #3a5a40 81px);
            background-size: 160px 160px;
        }
        
        .nature-pattern-3 {
            background: 
                radial-gradient(circle at 100% 50%, transparent 20%, rgba(255, 255, 255, 0.3) 21%, rgba(255, 255, 255, 0.3) 34%, transparent 35%, transparent),
                radial-gradient(circle at 0% 50%, transparent 20%, rgba(255, 255, 255, 0.3) 21%, rgba(255, 255, 255, 0.3) 34%, transparent 35%, transparent);
            background-color: #386641;
            background-size: 50px 100px;
        }
        
        .nature-pattern-4 {
            background: 
                linear-gradient(27deg, #a3b18a 5px, transparent 5px) 0 5px,
                linear-gradient(207deg, #a3b18a 5px, transparent 5px) 10px 0px,
                linear-gradient(27deg, #a3b18a 5px, transparent 5px) 0px 10px,
                linear-gradient(207deg, #a3b18a 5px, transparent 5px) 10px 5px,
                linear-gradient(90deg, #a3b18a 10px, transparent 10px),
                linear-gradient(#a3b18a 25%, transparent 25%);
            background-color: #dad7cd;
            background-size: 20px 20px;
        }
        
        .minimal-pattern-1 {
            background-color: #f8f9fa;
            background-image: 
                linear-gradient(90deg, rgba(220, 220, 220, 0.5) 0%, rgba(220, 220, 220, 0.5) 1%, transparent 1%),
                linear-gradient(rgba(220, 220, 220, 0.5) 0%, rgba(220, 220, 220, 0.5) 1%, transparent 1%);
            background-size: 20px 20px;
        }
        
        .minimal-pattern-2 {
            background-color: #ffffff;
            background-image: radial-gradient(#e9ecef 2px, transparent 2px);
            background-size: 30px 30px;
        }
        
        .minimal-pattern-3 {
            background-color: #f1f3f5;
            background-image: 
                linear-gradient(45deg, #dee2e6 25%, transparent 25%, transparent 75%, #dee2e6 75%, #dee2e6),
                linear-gradient(45deg, #dee2e6 25%, transparent 25%, transparent 75%, #dee2e6 75%, #dee2e6);
            background-size: 60px 60px;
            background-position: 0 0, 30px 30px;
        }
        
        .minimal-pattern-4 {
            background-color: #f8f9fa;
            background-image: 
                linear-gradient(0deg, transparent 9px, #ced4da 10px),
                linear-gradient(90deg, transparent 9px, #ced4da 10px);
            background-size: 10px 10px;
        }
    </style>
</head>
<body>
    <header>
        <div class="nav-container">
            <div class="logo">Wall<span>Hub</span></div>
            <ul class="nav-links">
                <li class="active" data-target="abstract">Abstract</li>
                <li data-target="cool">Cool</li>
                <li data-target="live">Live</li>
                <li data-target="gradient">Gradient</li>
                <li data-target="nature">Nature</li>
                <li data-target="minimal">Minimal</li>
            </ul>
        </div>
    </header>
    
    <div class="welcome-section">
        <h1>Find Your Perfect Wallpaper</h1>
        <p>Browse our collection of high-quality wallpapers for desktop and mobile</p>
        <div class="search-bar">
            <input type="text" placeholder="Search wallpapers...">
            <button>Search</button>
        </div>
    </div>
    
    <div class="container">
        <section id="abstract" class="section active">
            <h2>Abstract Wallpapers</h2>
            <div class="grid">
                <div class="wallpaper">
                    <div class="abstract-pattern-1" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="abstract-pattern-1">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="abstract-pattern-2" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="abstract-pattern-2">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="abstract-pattern-3" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="abstract-pattern-3">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="abstract-pattern-4" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="abstract-pattern-4">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
            </div>
        </section>
        
        <section id="cool" class="section">
            <h2>Cool Wallpapers</h2>
            <div class="grid">
                <div class="wallpaper">
                    <div class="cool-pattern-1" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="cool-pattern-1">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="cool-pattern-2" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="cool-pattern-2">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="cool-pattern-3" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="cool-pattern-3">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="cool-pattern-4" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="cool-pattern-4">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
            </div>
        </section>
        
        <section id="live" class="section">
            <h2>Live Wallpapers</h2>
            <div class="grid">
                <div class="wallpaper live-wallpaper live-wallpaper-1">
                    <a href="#" class="download-btn" data-pattern="live-wallpaper-1">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper live-wallpaper live-wallpaper-2">
                    <a href="#" class="download-btn" data-pattern="live-wallpaper-2">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper live-wallpaper live-wallpaper-3">
                    <a href="#" class="download-btn" data-pattern="live-wallpaper-3">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper live-wallpaper live-wallpaper-4">
                    <div class="wave"></div>
                    <div class="wave"></div>
                    <div class="wave"></div>
                    <a href="#" class="download-btn" data-pattern="live-wallpaper-4">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
            </div>
        </section>
        
        <section id="gradient" class="section">
            <h2>Gradient Wallpapers</h2>
            <div class="grid">
                <div class="wallpaper">
                    <div class="gradient-pattern-1" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="gradient-pattern-1">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="gradient-pattern-2" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="gradient-pattern-2">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="gradient-pattern-3" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="gradient-pattern-3">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="gradient-pattern-4" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="gradient-pattern-4">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
            </div>
        </section>
        
        <section id="nature" class="section">
            <h2>Nature Wallpapers</h2>
            <div class="grid">
                <div class="wallpaper">
                    <div class="nature-pattern-1" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="nature-pattern-1">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="nature-pattern-2" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="nature-pattern-2">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="nature-pattern-3" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="nature-pattern-3">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="nature-pattern-4" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="nature-pattern-4">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
            </div>
        </section>
        
        <section id="minimal" class="section">
            <h2>Minimal Wallpapers</h2>
            <div class="grid">
                <div class="wallpaper">
                    <div class="minimal-pattern-1" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="minimal-pattern-1">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="minimal-pattern-2" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="minimal-pattern-2">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="minimal-pattern-3" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="minimal-pattern-3">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
                <div class="wallpaper">
                    <div class="minimal-pattern-4" style="width:100%; height:100%;"></div>
                    <a href="#" class="download-btn" data-pattern="minimal-pattern-4">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                            <polyline points="7 10 12 15 17 10"></polyline>
                            <line x1="12" y1="15" x2="12" y2="3"></line>
                        </svg>
                    </a>
                </div>
            </div>
        </section>
    </div>
    
    <div class="modal" id="modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <div id="modal-display"></div>
        </div>
    </div>
    
    <script>
        // Navigation functionality
        const navLinks = document.querySelectorAll('.nav-links li');
        const sections = document.querySelectorAll('.section');
        
        navLinks.forEach(link => {
            link.addEventListener('click', () => {
                const target = link.getAttribute('data-target');
                
                // Update active link
                navLinks.forEach(item => item.classList.remove('active'));
                link.classList.add('active');
                
                // Update active section
                sections.forEach(section => {
                    section.classList.remove('active');
                    if (section.id === target) {
                        section.classList.add('active');
                    }
                });
            });
        });
        
        // Modal functionality
        const modal = document.getElementById('modal');
        const modalDisplay = document.getElementById('modal-display');
        const closeModal = document.querySelector('.close-modal');
        const wallpapers = document.querySelectorAll('.wallpaper');
        
        // Function to create a wallpaper preview
        function createWallpaperPreview(element) {
            const clone = element.cloneNode(true);
            clone.style.width = '800px';
            clone.style.height = '450px';
            clone.style.cursor = 'default';
            
            // Remove download button from clone
            const downloadBtn = clone.querySelector('.download-btn');
            if (downloadBtn) {
                downloadBtn.remove();
            }
            
            return clone;
        }
        
        wallpapers.forEach(wallpaper => {
            wallpaper.addEventListener('click', (e) => {
                // Only open modal if not clicking download button
                if (!e.target.classList.contains('download-btn') && !e.target.closest('.download-btn')) {
                    modal.classList.add('active');
                    
                    // Clear previous content
                    modalDisplay.innerHTML = '';
                    
                    // Create and append wallpaper preview
                    const preview = createWallpaperPreview(wallpaper);
                    modalDisplay.appendChild(preview);
                }
            });
        });
        
        closeModal.addEventListener('click', () => {
            modal.classList.remove('active');
        });
        
        window.addEventListener('click', (e) => {
            if (e.target === modal) {
                modal.classList.remove('active');
            }
        });
        
        // Download functionality
        const downloadBtns = document.querySelectorAll('.download-btn');
        
        // Function to convert div with CSS to canvas and download
        function downloadWallpaper(pattern) {
            // Create a temporary div with the pattern
            const tempDiv = document.createElement('div');
            tempDiv.className = pattern;
            tempDiv.style.width = '1920px';
            tempDiv.style.height = '1080px';
            tempDiv.style.position = 'absolute';
            tempDiv.style.left = '-9999px';
            document.body.appendChild(tempDiv);
            
            // Use html2canvas to convert the div to canvas
            html2canvas(tempDiv).then(canvas => {
                // Create download link
                const link = document.createElement('a');
                link.download = `wallhub-${pattern}.png`;
                link.href = canvas.toDataURL('image/png');
                link.click();
                
                // Clean up
                document.body.removeChild(tempDiv);
            });
        }
        
        // Simplified version for this demo
        downloadBtns.forEach(btn => {
            btn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                
                const pattern = btn.getAttribute('data-pattern');
                
                // For demo purposes, we'll simulate the download
                // In a real app, you would use the downloadWallpaper function
                const filename = `wallhub-${pattern}.png`;
                
                // Create a fake download link
                const link = document.createElement('a');
                link.href = '#';
                link.download = filename;
                link.style.display = 'none';
                document.body.appendChild(link);
                
                // Simulate click and clean up
                link.click();
                document.body.removeChild(link);
                
                // Show success message
                alert(`Downloading ${filename}`);
            });
        });
        
        // Mock implementation of html2canvas for demo purposes
        function html2canvas(element) {
            return new Promise(resolve => {
                const canvas = document.createElement('canvas');
                canvas.width = element.offsetWidth;
                canvas.height = element.offsetHeight;
                
                // In a real app, this would render the element to the canvas
                // For this demo, we're just returning an empty canvas
                
                resolve(canvas);
            });
        }
        
        // Search functionality
        const searchButton = document.querySelector('.search-bar button');
        const searchInput = document.querySelector('.search-bar input');
        
        searchButton.addEventListener('click', () => {
            const query = searchInput.value.trim().toLowerCase();
            if (query) {
                // Find matching section based on query
                const sections = ['abstract', 'cool', 'live', 'gradient', 'nature', 'minimal'];
                const matchingSection = sections.find(section => section.includes(query));
                
                if (matchingSection) {
                    // Activate matching nav link
                    const matchingLink = document.querySelector(`.nav-links li[data-target="${matchingSection}"]`);
                    if (matchingLink) {
                        matchingLink.click();
                    }
                }
                
                // Show search results alert
                alert(`Showing wallpapers matching: ${query}`);
            }
        });
        
        searchInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                searchButton.click();
            }
        });
    </script>
</body>
</html>
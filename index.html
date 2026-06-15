<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AVA Theater - Advanced Search Portal</title>
    <style>
        /* تعریف پلت رنگی نئونی استودیو */
        :root {
            --bg-color: #060810;
            --card-bg: rgba(15, 20, 35, 0.7);
            --neon-blue: #00f0ff;
            --neon-glow-blue: rgba(0, 240, 255, 0.35);
            --neon-green: #00ffaa;
            --anime-gradient: linear-gradient(135deg, #ff6b00, #ff0055, #7000ff);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, sans-serif;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            color: #ffffff;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 110px 15px 20px 15px; /* پدینگ بالا برای جلوگیری از رفتن محتوا زیر سرچ‌بار فیکس شده */
            position: relative;
            overflow-x: hidden;
        }

        /* پس‌زمینه کهکشانی متحرک نئونی */
        body::before {
            content: "";
            position: fixed;
            top: 0; left: 0; width: 100%; height: 200%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="140" height="140" viewBox="0 0 140 140"><text x="15" y="30" fill="rgba(0, 240, 255, 0.35)" font-size="18">🎥</text><text x="85" y="25" fill="rgba(0, 255, 170, 0.30)" font-size="16">🎬</text><text x="50" y="65" fill="rgba(0, 240, 255, 0.30)" font-size="15">📺</text><text x="110" y="70" fill="rgba(0, 255, 170, 0.35)" font-size="17">🎞️</text><text x="75" y="115" fill="rgba(0, 255, 170, 0.38)" font-size="18">🍿</text><text x="115" y="120" fill="rgba(0, 240, 255, 0.30)" font-size="15">🕶️</text><text x="80" y="75" fill="rgba(255, 255, 255, 0.35)" font-size="10">✨</text></svg>');
            background-repeat: repeat;
            z-index: -1;
            animation: spaceScroll 30s linear infinite;
        }

        @keyframes spaceScroll {
            0% { transform: translateY(0); }
            100% { transform: translateY(-50%); }
        }

        /* --- بخش سرچ بار کاملا فیکس و شناور در بالای صفحه --- */
        .search-universe {
            position: fixed;
            top: 15px;
            left: 50%;
            transform: translateX(-50%);
            width: calc(100% - 30px);
            max-width: 480px;
            z-index: 1000;
            padding: 2px;
            background: var(--anime-gradient);
            background-size: 200% auto;
            border-radius: 50px;
            animation: moveGrad 3s linear infinite;
            box-shadow: 0 10px 30px rgba(0,0,0,0.7), 0 0 20px rgba(0, 240, 255, 0.2);
        }

        .search-box-wrapper {
            position: relative;
            width: 100%;
            background: rgba(15, 20, 32, 0.95);
            border-radius: 50px;
            display: flex;
            align-items: center;
        }

        .search-icon {
            position: absolute;
            left: 18px;
            font-size: 1.1rem;
            z-index: 2;
            pointer-events: none;
        }

        .search-input {
            width: 100%;
            padding: 16px 20px;
            padding-left: 48px;
            font-size: 1.05rem;
            background: transparent;
            border: none;
            border-radius: 50px;
            color: #fff;
            outline: none;
            transition: all 0.4s ease;
            position: relative;
            z-index: 1;
        }

        .search-input::placeholder {
            background: var(--anime-gradient);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: moveGrad 3s linear infinite;
            opacity: 0.75;
            font-weight: 600;
        }

        .search-results-panel {
            position: absolute;
            top: 115%;
            left: 0;
            width: 100%;
            background: rgba(10, 14, 26, 0.95);
            border: 1px solid rgba(0, 240, 255, 0.3);
            border-radius: 16px;
            max-height: 280px;
            overflow-y: auto;
            display: none;
            box-shadow: 0 20px 50px rgba(0,0,0,0.8), 0 0 30px rgba(0, 240, 255, 0.1);
            backdrop-filter: blur(10px);
            z-index: 2000;
        }

        .result-tab-item {
            display: flex;
            align-items: center;
            padding: 12px 18px;
            cursor: pointer;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            transition: all 0.3s ease;
        }

        .result-tab-item:last-child {
            border-bottom: none;
        }

        .result-tab-item:hover {
            background: rgba(0, 240, 255, 0.15);
            padding-left: 25px;
        }

        .result-thumb {
            width: 35px;
            height: 45px;
            object-fit: cover;
            border-radius: 4px;
            margin-right: 15px;
            border: 1px solid rgba(0, 240, 255, 0.3);
        }

        .result-title {
            font-size: 1rem;
            font-weight: 600;
            color: #fff;
        }

        /* --- ساختار طرح‌بندی اصلی سایت (پشتیبانی از سایدبار تبلیغ دسکتاپ) --- */
        .main-layout-wrapper {
            width: 100%;
            max-width: 1450px;
            display: block;
        }

        .movies-container {
            width: 100%;
            display: grid;
            grid-template-columns: 1fr;
            gap: 30px;
            margin-bottom: 50px;
            justify-items: center;
        }

        /* چوکات یا بلوک کلی نگه‌دارنده هر فیلم و تبلیغ زیر آن */
        .movie-block-wrapper {
            width: 100%;
            max-width: 340px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .movie-premium-card {
            width: 100%;
            background: var(--card-bg);
            border: 1px solid rgba(255, 255, 255, 0.06);
            border-radius: 24px;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            box-shadow: 0 20px 45px rgba(0,0,0,0.6);
            backdrop-filter: blur(12px);
            transition: transform 0.4s ease, border-color 0.4s ease;
            scroll-margin-top: 110px;
        }

        .movie-premium-card:hover {
            border-color: rgba(0, 240, 255, 0.4);
            transform: translateY(-5px);
        }

        .movie-poster {
            width: auto;
            height: auto;
            max-width: 100%;
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.7);
            margin-bottom: 20px;
            object-fit: contain;
            display: block;
        }

        .movie-details-box {
            width: 100%;
            text-align: left;
            margin-bottom: 20px;
            padding: 0 5px;
        }

        .movie-title-header {
            font-size: 1.25rem;
            font-weight: 800;
            color: #ffffff;
            margin-bottom: 15px;
            border-left: 4px solid var(--neon-blue);
            padding-left: 10px;
            line-height: 1.2;
        }

        .meta-info-line {
            font-size: 0.9rem;
            color: #cdd5e0;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .meta-label {
            color: rgba(255, 255, 255, 0.5);
            font-weight: 600;
        }

        .premium-download-btn {
            background: var(--anime-gradient);
            background-size: 200% auto;
            color: #ffffff;
            width: 100%;
            padding: 13px 0;
            text-align: center;
            font-size: 1rem;
            font-weight: 800;
            border-radius: 50px;
            text-decoration: none;
            display: inline-block;
            border: 1px solid rgba(255, 255, 255, 0.25);
            box-shadow: 0 12px 35px rgba(255, 107, 0, 0.35);
            transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            letter-spacing: 0.5px;
            animation: moveGrad 3s linear infinite, pulseGlow 1.8s infinite alternate;
            margin-top: auto; 
            cursor: pointer;
        }

        /* بخش چوکات زیرین تبلیغات بنری بر اساس ابعاد دستگاه */
        .card-banner-placement {
            margin-top: 15px;
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 50px;
        }

        .desktop-sidebar-ad {
            display: none;
        }

        /* تبلت: ۲ کادر در یک خط */
        @media (min-width: 680px) and (max-width: 991px) {
            .movies-container {
                grid-template-columns: repeat(2, 1fr);
            }
            .card-banner-placement .banner-mobile { display: none !important; }
            .card-banner-placement .banner-tablet { display: block !important; }
        }

        /* موبایل مینی */
        @media (max-width: 679px) {
            .card-banner-placement .banner-mobile { display: block !important; }
            .card-banner-placement .banner-tablet { display: none !important; }
        }

        /* دسکتاپ و مانیتور بزرگ (۳ فیلم در خط + ستون سمت راست تبلیغات) */
        @media (min-width: 992px) {
            .main-layout-wrapper {
                display: grid;
                grid-template-columns: 1fr 320px;
                gap: 30px;
            }
            .movies-container {
                grid-template-columns: repeat(3, 1fr);
            }
            /* پنهان کردن تبلیغات زیر کادر فیلم در دسکتاپ */
            .card-banner-placement {
                display: none !important;
            }
            /* نمایش سایدبار پیشرفته نئونی سمت راست */
            .desktop-sidebar-ad {
                display: block;
                width: 100%;
                background: rgba(10, 15, 30, 0.8);
                border: 1px solid rgba(0, 240, 255, 0.15);
                border-radius: 24px;
                padding: 10px;
                height: fit-content;
                position: sticky;
                top: 110px;
                box-shadow: 0 20px 45px rgba(0,0,0,0.5);
                backdrop-filter: blur(10px);
                text-align: center;
            }
            .sidebar-ad-title {
                font-size: 0.8rem;
                color: rgba(0, 240, 255, 0.7);
                margin-bottom: 10px;
                text-transform: uppercase;
                letter-spacing: 1px;
                font-weight: bold;
            }
        }

        @keyframes moveGrad {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes pulseGlow {
            0% { box-shadow: 0 12px 30px rgba(255, 107, 0, 0.3), 0 0 15px rgba(255, 0, 85, 0.2); }
            100% { box-shadow: 0 20px 45px rgba(255, 107, 0, 0.55), 0 0 35px rgba(112, 0, 255, 0.4); filter: brightness(1.05); }
        }

        .premium-download-btn:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 22px 50px rgba(255, 107, 0, 0.65);
        }

        /* --- استایل فوق پیشرفته پاپ‌آپ تمام صفحه لوکس با فاصله ظریف --- */
        .gateway-overlay {
            position: fixed;
            top: 15px; left: 15px; right: 15px; bottom: 15px;
            background: rgba(5, 8, 18, 0.85);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border: 2px solid rgba(255, 107, 0, 0.25);
            border-radius: 28px;
            z-index: 10000;
            display: none;
            overflow: hidden; /* غیر قابل اسکرول کردن */
            box-shadow: 0 0 60px rgba(0,0,0,0.9), inset 0 0 40px rgba(112, 0, 255, 0.15);
        }

        /* ساختار داخلی پاپ‌آپ چند لایه هماهنگ با دیوایس‌ها */
        .gateway-content-container {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
        }

        /* بخش مرکزی محتوا و لودینگ */
        .gateway-center-zone {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
        }

        /* انیمیشن زنده شمارنده تایمر */
        .gateway-timer-display {
            font-size: 5rem;
            font-weight: 900;
            background: var(--anime-gradient);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: moveGrad 3s linear infinite, timerScale 1s infinite ease-in-out;
            line-height: 1;
            margin-bottom: 10px;
        }

        @keyframes timerScale {
            0% { transform: scale(1); opacity: 0.9; }
            50% { transform: scale(1.1); opacity: 1; filter: drop-shadow(0 0 15px rgba(255,0,85,0.6)); }
            100% { transform: scale(1); opacity: 0.9; }
        }

        .gateway-cyber-brand {
            font-size: 1.6rem;
            font-weight: 800;
            color: #ffffff;
            letter-spacing: 2px;
            text-shadow: 0 0 10px var(--neon-blue);
            margin-bottom: 15px;
        }

        .gateway-status-text {
            font-size: 1rem;
            color: #a0aec0;
            max-width: 400px;
            line-height: 1.5;
            font-weight: 500;
        }

        /* بخش قرارگیری تبلیغات داخل پاپ‌آپ */
        .gateway-ad-holder {
            display: flex;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.2);
            padding: 15px;
        }

        /* چیدمان‌های اختصاصی پاپ‌آپ بر اساس نوع دستگاه */
        @media (max-width: 991px) {
            /* در تبلت و موبایل تبلیغ به سمت راست میچسبد */
            .gateway-content-container {
                flex-direction: row-reverse;
            }
            .gateway-ad-holder {
                width: 340px;
                height: 100%;
                border-left: 1px solid rgba(255,255,255,0.05);
            }
        }

        @media (min-width: 992px) {
            /* در دسکتاپ تبلیغ به پایین پاپ‌آپ منتقل شده و محتوا در وسط قرار میگیرد */
            .gateway-content-container {
                flex-direction: column;
            }
            .gateway-ad-holder {
                width: 100%;
                height: auto;
                border-top: 1px solid rgba(255,255,255,0.05);
                padding: 20px 10px;
                margin-top: auto;
            }
        }
    </style>
</head>
<body>

    <div class="search-universe">
        <div class="search-box-wrapper">
            <span class="search-icon">🔍</span>
            <input type="text" id="movieSearchInput" class="search-input" placeholder="Search your movie...">
            <div id="searchResultsDropdown" class="search-results-panel"></div>
        </div>
    </div>

    <div class="main-layout-wrapper">
        
        <div class="movies-container">

            <div class="movie-block-wrapper">
                <div class="movie-premium-card" id="movie-The-Marked-Woman">
                    <img src="https://images.justwatch.com/poster/344584556/s718/the-marked-woman.jpg" alt="The Marked Woman Poster" class="movie-poster">
                    <div class="movie-details-box">
                        <h2 class="movie-title-header">🎬 The Marked Woman</h2>
                        <div class="meta-info-line"><span class="meta-label">📅 Year:</span> 2026</div>
                        <div class="meta-info-line"><span class="meta-label">⭐ IMDb:</span> N/A</div>
                        <div class="meta-info-line"><span class="meta-label">🎭 Genre:</span> Thriller, Mystery, Crime</div>
                        <div class="meta-info-line"><span class="meta-label">🌍 Country:</span> Spain</div>
                        <div class="meta-info-line"><span class="meta-label">⏱ Runtime:</span> 109 min</div>
                    </div>
                    <button onclick="triggerDownloadGateway('https://t.me/AVA_Movies_Animes/9')" class="premium-download-btn">DOWNLOAD NOW</button>
                </div>
                <div class="card-banner-placement">
                    <div class="banner-mobile">
                        <script>
                            atOptions = { 'key' : '9e5c12a031e3b2a16c1d328d29e5dab4', 'format' : 'iframe', 'height' : 50, 'width' : 320, 'params' : {} };
                        </script>
                        <script src="https://www.highperformanceformat.com/9e5c12a031e3b2a16c1d328d29e5dab4/invoke.js"></script>
                    </div>
                    <div class="banner-tablet">
                        <script>
                            atOptions = { 'key' : '404c52513666d7584d5c00fe4d5ad86c', 'format' : 'iframe', 'height' : 60, 'width' : 468, 'params' : {} };
                        </script>
                        <script src="https://www.highperformanceformat.com/404c52513666d7584d5c00fe4d5ad86c/invoke.js"></script>
                    </div>
                </div>
            </div>

            <div class="movie-block-wrapper">
                <div class="movie-premium-card" id="Equilibrium">
                    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTzVWU77H_SgJSuhupxH1-c7pHcKN_cmjVXyBdn_2TjO4oc8SL8-T86nVo&s=10" alt="Equilibrium Poster" class="movie-poster">
                    <div class="movie-details-box">
                        <h2 class="movie-title-header">🎬 Equilibrium</h2>
                        <div class="meta-info-line"><span class="meta-label">📅 Year:</span> 2002</div>
                        <div class="meta-info-line"><span class="meta-label">⭐ IMDb:</span> 7.3/10</div>
                        <div class="meta-info-line"><span class="meta-label">🎭 Genre:</span> Action, Sci-Fi, Thriller</div>
                        <div class="meta-info-line"><span class="meta-label">🌍 Country:</span> United States</div>
                        <div class="meta-info-line"><span class="meta-label">⏱ Runtime:</span> 107 min</div>
                    </div>
                    <button onclick="triggerDownloadGateway('https://t.me/AVA_Movies_Animes/14')" class="premium-download-btn">DOWNLOAD NOW</button>
                </div>
                <div class="card-banner-placement">
                    <div class="banner-mobile">
                        <script>
                            atOptions = { 'key' : '9e5c12a031e3b2a16c1d328d29e5dab4', 'format' : 'iframe', 'height' : 50, 'width' : 320, 'params' : {} };
                        </script>
                        <script src="https://www.highperformanceformat.com/9e5c12a031e3b2a16c1d328d29e5dab4/invoke.js"></script>
                    </div>
                    <div class="banner-tablet">
                        <script>
                            atOptions = { 'key' : '404c52513666d7584d5c00fe4d5ad86c', 'format' : 'iframe', 'height' : 60, 'width' : 468, 'params' : {} };
                        </script>
                        <script src="https://www.highperformanceformat.com/404c52513666d7584d5c00fe4d5ad86c/invoke.js"></script>
                    </div>
                </div>
            </div>

        </div>

        <div class="desktop-sidebar-ad">
            <div class="sidebar-ad-title">Sponsored Advertisement</div>
            <div id="sidebar-native-container">
                <script async="async" data-cfasync="false" src="https://pl29741961.effectivecpmnetwork.com/46fa53bab184d6979bf4dbeee413d25f/invoke.js"></script>
                <div id="container-46fa53bab184d6979bf4dbeee413d25f"></div>
            </div>
        </div>

    </div>

    <div id="downloadGatewayModal" class="gateway-overlay">
        <div class="gateway-content-container">
            
            <div class="gateway-center-zone">
                <div id="gatewayCountdownTimer" class="gateway-timer-display">4</div>
                <div class="gateway-cyber-brand">DDOS GUARD</div>
                <p class="gateway-status-text">You will be redirected to the secure movie download page after the countdown completes.</p>
            </div>

            <div class="gateway-ad-holder">
                <div style="width:100%; max-width:320px; min-height:50px;">
                    <script async="async" data-cfasync="false" src="https://pl29741961.effectivecpmnetwork.com/46fa53bab184d6979bf4dbeee413d25f/invoke.js"></script>
                    <div id="container-popup-46fa53bab184d6979bf4dbeee413d25f"></div>
                </div>
            </div>

        </div>
    </div>

    <script>
        // دیتابیس فیلم‌ها برای سیستم سرچ بار شیک
        const moviesDatabase = [
            {
                id: "movie-The-Marked-Woman", 
                title: "The Marked Woman", 
                thumb: "https://images.justwatch.com/poster/344584556/s718/the-marked-woman.jpg" 
            },
            {
                id: "Equilibrium", 
                title: "Equilibrium", 
                thumb: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTzVWU77H_SgJSuhupxH1-c7pHcKN_cmjVXyBdn_2TjO4oc8SL8-T86nVo&s=10" 
            }
        ];

        const searchInput = document.getElementById('movieSearchInput');
        const resultsDropdown = document.getElementById('searchResultsDropdown');

        searchInput.addEventListener('input', function() {
            const query = this.value.toLowerCase().trim();
            resultsDropdown.innerHTML = '';

            if (query === '') {
                resultsDropdown.style.display = 'none';
                return;
            }

            const filteredMovies = moviesDatabase.filter(movie => 
                movie.title.toLowerCase().includes(query)
            );

            if (filteredMovies.length > 0) {
                filteredMovies.forEach(movie => {
                    const tab = document.createElement('div');
                    tab.className = 'result-tab-item';
                    tab.innerHTML = `
                        <img src="${movie.thumb}" class="result-thumb">
                        <span class="result-title">${movie.title}</span>
                    `;

                    tab.addEventListener('click', function() {
                        const targetCard = document.getElementById(movie.id);
                        if (targetCard) {
                            targetCard.scrollIntoView({ behavior: 'smooth', block: 'start' });
                            targetCard.style.borderColor = 'var(--neon-blue)';
                            setTimeout(() => {
                                targetCard.style.borderColor = 'rgba(255, 255, 255, 0.06)';
                            }, 2000);
                        }
                        searchInput.value = '';
                        resultsDropdown.style.display = 'none';
                    });

                    resultsDropdown.appendChild(tab);
                });
                resultsDropdown.style.display = 'block';
            } else {
                resultsDropdown.innerHTML = `<div style="padding: 15px; color: rgba(255,255,255,0.4); text-align:center; font-size:0.9rem;">No movies found</div>`;
                resultsDropdown.style.display = 'block';
            }
        });

        document.addEventListener('click', function(e) {
            if (!searchInput.contains(e.target) && !resultsDropdown.contains(e.target)) {
                resultsDropdown.style.display = 'none';
            }
        });

        // --- مکانیزم فوق حرفه‌ای کنترل پاپ‌آپ و تایمر بدون تکرار کد ---
        function triggerDownloadGateway(destinationUrl) {
            const modal = document.getElementById('downloadGatewayModal');
            const timerDisplay = document.getElementById('gatewayCountdownTimer');
            
            let timeLeft = 4;
            timerDisplay.innerText = timeLeft;
            modal.style.display = 'block';

            const countdownInterval = setInterval(() => {
                timeLeft--;
                timerDisplay.innerText = timeLeft;

                if (timeLeft <= 0) {
                    clearInterval(countdownInterval);
                    modal.style.display = 'none';
                    window.location.href = destinationUrl; // انتقال اتوماتیک به لینک تلگرام/دانلود
                }
            }, 1000);
        }

        // --- سیستم بارگذاری مجدد و هوشمند تبلیغات سایدبار دسکتاپ هر ۵۰ ثانیه ---
        setInterval(() => {
            const sidebarContainer = document.getElementById('sidebar-native-container');
            if (sidebarContainer && window.innerWidth >= 992) {
                sidebarContainer.innerHTML = ''; 
                
                const adScript = document.createElement('script');
                adScript.async = true;
                adScript.setAttribute('data-cfasync', 'false');
                adScript.src = 'https://pl29741961.effectivecpmnetwork.com/46fa53bab184d6979bf4dbeee413d25f/invoke.js';
                
                const adDiv = document.createElement('div');
                adDiv.id = 'container-46fa53bab184d6979bf4dbeee413d25f';
                
                sidebarContainer.appendChild(adScript);
                sidebarContainer.appendChild(adDiv);
            }
        }, 50000); // دقیقاً هر ۵0 ثانیه یکبار کل تبلیغ رفرش ریفرش و بازخوانی می‌شود.
    </script>
</body>
</html>

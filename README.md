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
            
            /* گرادینت محبوب انیمه/فیلم (نارنجی اتمی، ارغوانی، قرمز آتشین) */
            --anime-gradient: linear-gradient(135deg, #ff6b00, #ff0055, #7000ff);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, sans-serif;
        }

        /* اسکرول نرم برای جابجایی بین فیلم‌ها */
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
            padding: 20px 15px;
            position: relative;
            overflow-x: hidden;
        }

        /* پس‌زمینه کهکشانی متحرک نئونی - غلظت رنگ شکل‌ها جهت روشن‌تر و واضح‌تر شدن به 0.35 افزایش یافت */
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

        /* --- بخش سرچ بار با دیواره انیمیشنی گرادینت و ساختار فیکس شده --- */
        .search-universe {
            width: 100%;
            max-width: 480px;
            margin-top: 15px;
            margin-bottom: 40px;
            position: relative;
            z-index: 100;
            padding: 2px; /* فضا برای دیده شدن بوردر گرادینتی پشت سرمایه */
            background: var(--anime-gradient);
            background-size: 200% auto;
            border-radius: 50px;
            animation: moveGrad 3s linear infinite;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
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

        /* افکت انیمیشن رنگی برای متن کم‌رنگ پیش‌فرض (Placeholder) */
        .search-input::placeholder {
            background: var(--anime-gradient);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: moveGrad 3s linear infinite;
            opacity: 0.75;
            font-weight: 600;
        }

        /* پنجره کشویی نتایج جستجو (سبک تلگرام) */
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
            z-index: 1000;
        }

        /* تب‌های داخل پنجره نتایج */
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

        /* --- بخش نمایش فیلم‌ها (تغییر به ۴ تایی در دسکتاپ بزرگ) --- */
        .movies-container {
            width: 100%;
            max-width: 1400px; /* حداکثر عرض بیشتر برای جا شدن ۴ کارت */
            display: grid;
            grid-template-columns: 1fr; /* موبایل: ۱ کادر */
            gap: 25px;
            margin-bottom: 50px;
            justify-items: center;
        }

        /* تبلت: ۲ کادر */
        @media (min-width: 650px) and (max-width: 991px) {
            .movies-container {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        /* مانیتورهای معمولی: ۳ کادر */
        @media (min-width: 992px) and (max-width: 1199px) {
            .movies-container {
                grid-template-columns: repeat(3, 1fr);
            }
        }

        /* دسکتاپ‌های بزرگ و کامپیوتر: ۴ کادر در یک خط */
        @media (min-width: 1200px) {
            .movies-container {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        /* قالب (کارت) لوکس شیشه‌ای و نئونی معرفی فیلم */
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
            scroll-margin-top: 30px;
        }

        .movie-premium-card:hover {
            border-color: rgba(0, 240, 255, 0.4);
            transform: translateY(-5px);
        }

        /* پوستر اصلی داخل کارت */
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

        /* بخش مشخصات متنی فیلم */
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

        /* دکمه با آخرین متد گرادینت نئونی و فوق انیمه‌ای */
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

    <div class="movies-container">

        <div class="movie-premium-card" id="movie-The-Marked-Woman">
            <img src="https://images.justwatch.com/poster/344584556/s718/the-marked-woman.jpg" alt="The Marked Woman Poster" class="movie-poster">
            
            <div class="movie-details-box">
                <h2 class="movie-title-header">🎬 The Marked Woman</h2>
                <div class="meta-info-line">
                    <span class="meta-label">📅 Year:</span> 2026
                </div>
                <div class="meta-info-line">
                    <span class="meta-label">⭐ IMDb:</span> N/A
                </div>
                <div class="meta-info-line">
                    <span class="meta-label">🎭 Genre:</span> Thriller, Mystery, Crime
                </div>
                <div class="meta-info-line">
                    <span class="meta-label">🌍 Country:</span> Spain
                </div>
                <div class="meta-info-line">
                    <span class="meta-label">⏱ Runtime:</span> 109 min
                </div>
            </div>
            <a href="https://t.me/AVA_Movies_Animes/9" class="premium-download-btn">DOWNLOAD NOW</a>
        </div>

        <div class="movie-premium-card" id="Equilibrium">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTzVWU77H_SgJSuhupxH1-c7pHcKN_cmjVXyBdn_2TjO4oc8SL8-T86nVo&s=10" alt="Equilibrium Poster" class="movie-poster">
            
            <div class="movie-details-box">
                <h2 class="movie-title-header">🎬 Equilibrium</h2>
                <div class="meta-info-line">
                    <span class="meta-label">📅 Year:</span> 2002
                </div>
                <div class="meta-info-line">
                    <span class="meta-label">⭐ IMDb:</span> 7.3/10
                </div>
                <div class="meta-info-line">
                    <span class="meta-label">🎭 Genre:</span> Action, Sci-Fi, Thriller
                </div>
                <div class="meta-info-line">
                    <span class="meta-label">🌍 Country:</span> United States
                </div>
                <div class="meta-info-line">
                    <span class="meta-label">⏱ Runtime:</span> 107 min
                </div>
            </div>
            <a href="https://t.me/AVA_Movies_Animes/14" class="premium-download-btn">DOWNLOAD NOW</a>
        </div>

    </div>

    <script>
        // دیتابیس فیلم‌ها برای سیستم سرچ بار
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

            // 🟢 [جاخالی دیتابیس سرچ]: برای اضافه کردن فیلم‌های بعدی به سرچ، قالب زیر را کپی کن و با علامت کاما جدا کن:
            /*
            {
                id: "movie-شناسه_یکتای_فیلم", // دقیقا همان شناسه‌ای که در کدهای HTML بالا استفاده کردی را بگذار
                title: "نام فیلم برای سرچ کردن", 
                thumb: "آدرس_لینک_عکس_کوچک_پوستر" 
            },
            */
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
    </script>
</body>
</html>

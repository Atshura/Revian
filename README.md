<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untuk Ibu</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Montserrat:wght@400;500&display=swap');
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            font-family: 'Montserrat', sans-serif;
            background-color: #f0f0f0;
            overflow: hidden;
        }
        /* === PRELOADER === */
        .preloader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #d7e9d5;
            z-index: 9999;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: transform 1.2s cubic-bezier(0.77, 0, 0.175, 1);
        }
        .preloader.loaded {
            transform: translateY(-100%);
        }
        .heart {
            width: 100px;
            height: 100px;
            background-color: #f7c9d9;
            position: relative;
            transform: rotate(-45deg);
            animation: beat 1.4s ease-in-out infinite;
        }
        .heart::before,
        .heart::after {
            content: "";
            width: 100px;
            height: 100px;
            background-color: #f7c9d9;
            border-radius: 50%;
            position: absolute;
        }
        .heart::before {
            top: -50px;
            left: 0;
        }
        .heart::after {
            top: 0;
            left: 50px;
        }
        @keyframes beat {
            0% { transform: rotate(-45deg) scale(1); }
            30% { transform: rotate(-45deg) scale(1.1); }
            50% { transform: rotate(-45deg) scale(1); }
            70% { transform: rotate(-45deg) scale(1.1); }
            100% { transform: rotate(-45deg) scale(1); }
        }
        /* === MAIN PAGE === */
        .page-wrapper {
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .main-container {
            width: 100%;
            height: 100%;
            max-height: 900px;
            display: flex;
            flex-direction: column;
            background-color: #ffffff;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            opacity: 0;
            transform: scale(0.98);
            transition: opacity 0.8s ease-out 0.5s, transform 0.8s ease-out 0.5s;
        }
        body.loaded .main-container {
            opacity: 1;
            transform: scale(1);
        }
        .top-section {
            background-color: #d7e9d5;
            padding: 40px 20px 30px 20px;
            text-align: center;
        }
        .main-title {
            font-family: 'Dancing Script', cursive;
            font-size: 3.5em;
            color: #333;
            margin: 0;
            font-weight: 700;
        }
        .sub-title {
            font-family: 'Montserrat', sans-serif;
            font-size: 1em;
            color: #555;
            margin-top: 5px;
        }
        .content-section {
            flex-grow: 1;
            background-color: #ffffff;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            gap: 30px;
        }
        .media-box {
            width: 85%;
            aspect-ratio: 16 / 9;
            max-height: 150px;
            border: 8px solid #f7c9d9;
            border-radius: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #fff;
            color: #333;
            font-size: 1.5em;
            font-weight: 500;
        }
        .bottom-section {
            background-color: #d7e9d5;
            min-height: 10%;
        }
    </style>
</head>
<body>
    <div class="preloader">
        <div class="heart"></div>
    </div>
    <div class="page-wrapper">
        <div class="main-container">
            <div class="top-section">
                <h1 class="main-title">Untuk Ibu,</h1>
                <p class="sub-title">dari ayah, mas, adik</p>
            </div>
            <div class="content-section">
                <div class="media-box">Video</div>
                <div class="media-box">Foto</div>
            </div>
            <div class="bottom-section"></div>
        </div>
    </div>
    <script>
        window.addEventListener('load', function() {
            const preloader = document.querySelector('.preloader');
            const body = document.querySelector('body');
            setTimeout(function() {
                preloader.classList.add('loaded');
                body.classList.add('loaded');
                body.style.overflow = 'auto';
            }, 1500);
        });
    </script>
</body>
</html>

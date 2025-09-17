<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untuk Ibu</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Montserrat:wght@400;500;600&display=swap');   
        /* Reset dasar untuk memastikan tampilan fullscreen */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        html, body {
            width: 100%;
            height: 100%;
            font-family: 'Montserrat', sans-serif;
            overflow: hidden; /* Mencegah scroll saat loading */
        }
        /* === PRELOADER (Tetap sama, sudah berfungsi baik) === */
        .preloader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background-color: #c0e399; z-index: 9999; display: flex;
            justify-content: center; align-items: center;
            transition: transform 1.2s cubic-bezier(0.77, 0, 0.175, 1);
        }
        .preloader.loaded { transform: translateY(-100%); }
        .heart {
            width: 100px; height: 100px; background-color: #f7c9d9;
            position: relative; transform: rotate(-45deg);
            animation: beat 1.4s ease-in-out infinite;
        }
        .heart::before, .heart::after {
            content: ""; width: 100px; height: 100px;
            background-color: #f7c9d9; border-radius: 50%; position: absolute;
        }
        .heart::before { top: -50px; left: 0; }
        .heart::after { top: 0; left: 50px; }
        @keyframes beat {
            0%, 50%, 100% { transform: rotate(-45deg) scale(1); }
            30%, 70% { transform: rotate(-45deg) scale(1.1); }
        }
        /* === MAIN PAGE LAYOUT (FIXED UNTUK FULLSCREEN) === */
        .main-container {
            width: 100vw; /* 100% lebar viewport */
            height: 100vh; /* 100% tinggi viewport */
            display: flex; flex-direction: column;
            opacity: 0; transition: opacity 0.8s ease-out 0.5s;
            background-color: #fff; /* Latar dasar putih */
        }
        body.loaded .main-container { opacity: 1; }
        .top-section {
            background-color: #c0e399;
            padding: 40px 20px 30px 20px; text-align: center;
        }
        .main-title {
            font-family: 'Dancing Script', cursive; font-size: 3.5em;
            color: #333; margin: 0; font-weight: 700;
        }
        .sub-title {
            font-family: 'Montserrat', sans-serif; font-size: 1em;
            color: #555; margin-top: 5px;
        }
        .content-section {
            flex-grow: 1;
            position: relative; /* Kunci untuk tata letak warna */
            display: flex; flex-direction: column; align-items: center;
            justify-content: center; padding: 20px; gap: 25px;
        }
        /* Trik untuk membuat warna hijau di belakang amplop */
        .content-section::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 150px; /* Tinggi area hijau */
            background-color: #c0e399;
            z-index: 0;
        }
        .bottom-section {
            background-color: #c0e399;
            min-height: 8%;
        }
        /* === FITUR AMPLOP (BUG FIXED & LOGIC CHANGED) === */
        .envelope {
            position: relative; width: 280px; height: 180px;
            cursor: pointer;
            overflow: hidden; /* FIX UTAMA: Sembunyikan konten yang meluap */
            border-radius: 10px; /* Agar overflow mengikuti bentuk amplop */
            z-index: 1; /* Pastikan amplop di atas background hijau */
        }
        .envelope-back, .envelope-flap, .envelope-front-label, .letter {
            position: absolute;
            width: 100%; height: 100%;
        }
        .envelope-back {
            background-color: #f7c9d9;
        }
        .envelope-flap {
            background-color: #f5b9cd;
            transform-origin: top;
            transition: transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
            clip-path: polygon(0 0, 100% 0, 100% 50%, 50% 100%, 0 50%);
            z-index: 3;
        }
        .envelope-front-label {
            display: flex; justify-content: center; align-items: center;
            color: #333; font-size: 1.8em; font-weight: 600;
            transition: opacity 0.3s ease; z-index: 4;
        }
        .letter {
            top: 0; width: 95%; height: 95%; margin: 2.5%;
            background-color: white; border-radius: 8px;
            transform: translateY(100%); /* Mulai dari bawah, tersembunyi */
            transition: transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
            display: flex; flex-direction: column; justify-content: center;
            align-items: center; gap: 15px; z-index: 2;
        }
        .letter-content { font-size: 1.2em; color: #444; }
        .action-button {
            background-color: #f7c9d9; color: #333; border: none;
            padding: 10px 25px; border-radius: 20px; font-size: 1em;
            font-weight: 500; cursor: pointer;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        /* State saat amplop terbuka */
        .envelope.open .envelope-flap { transform: rotateX(180deg); }
        .envelope.open .letter { transform: translateY(0%); }
        .envelope.open .envelope-front-label { opacity: 0; }
    </style>
</head>
<body>
    <div class="preloader">
        <div class="heart"></div>
    </div>
    <div class="main-container">
        <div class="top-section">
            <h1 class="main-title">Untuk Ibu,</h1>
            <p class="sub-title">dari ayah, mas, adik</p>
        </div>
        <div class="content-section">
            <div class="envelope" id="videoEnvelope">
                <div class="envelope-back"></div>
                <div class="letter">
                    <div class="letter-content">Sebuah Pesan Video</div>
                    <a href="#" target="_blank"><button class="action-button">Lihat Video</button></a>
                </div>
                <div class="envelope-flap"></div>
                <div class="envelope-front-label">Video</div>
            </div>
            <div class="envelope" id="fotoEnvelope">
                <div class="envelope-back"></div>
                <div class="letter">
                    <div class="letter-content">Kenangan Kita</div>
                    <a href="galeri.html"><button class="action-button">Lihat Foto</button></a>
                </div>
                <div class="envelope-flap"></div>
                <div class="envelope-front-label">Foto</div>
            </div>
        </div>
        <div class="bottom-section"></div>
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
        // --- JAVASCRIPT BARU: AMPLOP TIDAK BISA DITUTUP LAGI ---
        const envelopes = document.querySelectorAll('.envelope');
        envelopes.forEach(envelope => {
            envelope.addEventListener('click', (event) => {
                // Jangan buka amplop jika yang diklik adalah link/tombol di dalamnya
                if (event.target.closest('a')) {
                    return;
                }
                // Hanya tambahkan kelas 'open', tidak bisa ditutup lagi
                envelope.classList.add('open');
            });
        });
    </script>
</body>
</html>            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .envelope.open .envelope-flap { transform: rotateX(180deg); }
        .envelope.open .letter { transform: translateY(0%); }
        .envelope.open .envelope-front-label { opacity: 0; }
    </style>
</head>
<body>
    <div class="preloader">
        <div class="heart"></div>
    </div>
    <div class="main-container">
        <div class="top-section">
            <h1 class="main-title">Untuk Ibu,</h1>
            <p class="sub-title">dari ayah, mas, adik</p>
        </div>
        <div class="content-section">
            <div class="envelope" id="videoEnvelope">
                <div class="envelope-back"></div>
                <div class="letter">
                    <div class="letter-content">Sebuah Pesan Video</div>
                    <a href="#" target="_blank"><button class="action-button">Lihat Video</button></a>
                </div>
                <div class="envelope-flap"></div>
                <div class="envelope-front-label">Video</div>
            </div>
            <div class="envelope" id="fotoEnvelope">
                <div class="envelope-back"></div>
                <div class="letter">
                    <div class="letter-content">Kenangan Kita</div>
                    <a href="galeri.html"><button class="action-button">Lihat Foto</button></a>
                </div>
                <div class="envelope-flap"></div>
                <div class="envelope-front-label">Foto</div>
            </div>
        </div>
        <div class="bottom-section"></div>
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
        const envelopes = document.querySelectorAll('.envelope');
        envelopes.forEach(envelope => {
            envelope.addEventListener('click', (event) => {
                // Pastikan klik bukan pada link/tombol di dalam amplop
                if (event.target.closest('a')) return;
                envelopes.forEach(otherEnvelope => {
                    if (otherEnvelope !== envelope) {
                        otherEnvelope.classList.remove('open');
                    }
                });
                envelope.classList.toggle('open');
            });
        });
    </script>
</body>
</html>

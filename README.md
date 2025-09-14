<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Website Estetik dengan Loading</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        /* CSS (Cascading Style Sheets) untuk mengatur tampilan dan gaya */
        /* Pegaturan dasar */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        html, body {
            height: 100%; /* Memastikan gradasi warna memenuhi seluruh tinggi layar */
        }
        body {
            font-family: 'Poppins', sans-serif; /* Menggunakan font Poppins */
            /* Gradasi warna split screen: hijau muda di atas, pink di bawah */
            background: linear-gradient(to bottom, #a8e6cf 50%, #ff8a80 50%);
            background-attachment: fixed; /* Membuat background tidak ikut scroll */
            overflow: hidden; /* Mencegah scroll saat loading screen aktif */
        }
        /* --- 1. Gaya untuk Loading Screen yang Indah --- */
        #loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            /* Latar belakang loading screen SAMA dengan body agar seamless */
            background: linear-gradient(to bottom, #a8e6cf 50%, #ff8a80 50%);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: opacity 1s ease-out; /* Animasi fade-out saat menghilang lebih lambat */
            flex-direction: column;
            text-align: center;
        }
        .loader-content h1 {
            font-size: 3rem;
            color: white;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.2);
            margin-bottom: 20px;
        }
        #startButton {
            font-family: 'Poppins', sans-serif;
            font-size: 1.2rem;
            font-weight: 600;
            padding: 15px 40px;
            border: 2px solid white;
            background-color: transparent;
            color: white;
            border-radius: 50px; /* Membuat tombol berbentuk kapsul */
            cursor: pointer;
            /* Awalnya tombol disembunyikan dan posisinya sedikit di bawah */
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1); /* Transisi untuk kemunculan dan hover */
        }
        #startButton.visible {
            opacity: 1;
            transform: translateY(0);
        }
        #startButton:hover {
            background-color: white;
            color: #ff8a80; /* Warna pink saat hover */
            transform: scale(1.05); /* Sedikit membesar saat disentuh */
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
        }
        /* --- 2. Gaya untuk Halaman Utama --- */
        #main-content {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            visibility: hidden;
            opacity: 0;
            transition: opacity 1s ease-in;
        }
        /* Gaya untuk kotak yang berisi video (Efek Kaca Buram) */
        .video-container {
            display: flex;
            flex-direction: row;
            gap: 25px;
            padding: 30px;
            /* Efek Frosted Glass */
            background-color: rgba(255, 255, 255, 0.6); /* Warna putih semi-transparan */
            backdrop-filter: blur(15px); /* Efek blur pada background di belakang elemen ini */
            -webkit-backdrop-filter: blur(15px); /* Untuk browser Safari */
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.15);
            max-width: 1200px;
            width: 100%;
        }
        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%; /* Rasio 16:9 */
            height: 0;
            overflow: hidden;
            flex: 1 1 300px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }
        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }
        /* --- 3. Aturan Responsif untuk Mobile --- */
        @media (max-width: 768px) {
            .loader-content h1 {
                font-size: 2rem;
            }
            .video-container {
                flex-direction: column; 
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <div id="loading-screen">
        <div class="loader-content">
            <h1>Selamat Datang</h1>
            <button id="startButton">Mulai</button>
        </div>
    </div>
    <main id="main-content">
        <div class="video-container">
            <div class="video-wrapper">
                <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>
            <div class="video-wrapper">
                <iframe src="https://www.youtube.com/embed/3JZ_D3ELwOQ" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>
            <div class="video-wrapper">
                <iframe src="https://www.youtube.com/embed/LXb3EKWsInQ" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>
        </div>
    </main>
    <script>
        // JavaScript untuk fungsionalitas website
        const loader = document.getElementById('loading-screen');
        const mainContent = document.getElementById('main-content');
        const startButton = document.getElementById('startButton');
        // Menjalankan fungsi setelah seluruh konten halaman selesai dimuat
        window.addEventListener('load', function() {
            // Setelah semua siap, munculkan tombol "Mulai" dengan animasi
            startButton.classList.add('visible');
        });
        // Menambahkan fungsi yang akan berjalan ketika tombol "Mulai" di-klik
        startButton.addEventListener('click', function() {
            // 1. Izinkan body untuk bisa di-scroll kembali
            document.body.style.overflow = 'auto';
            // 2. Mulai hilangkan loading screen
            loader.style.opacity = '0';
            // 3. Tampilkan konten utama
            mainContent.style.visibility = 'visible';
            mainContent.style.opacity = '1';
            // 4. Setelah animasi selesai, hapus elemen loading screen dari tampilan
            setTimeout(() => {
                loader.style.display = 'none';
            }, 1000); // Sesuaikan dengan durasi transisi di CSS (1s = 1000ms)
        });
    </script>

</body>
</html>

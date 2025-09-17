<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untuk Ibu</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        /* CSS (Cascading Style Sheets) untuk mengatur tampilan dan gaya */
        /* Pegaturan dasar */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        html, body {
            height: 100%;
        }
        body {
            font-family: 'Poppins', sans-serif;
            /* Gradasi warna BARU untuk background utama & loading */
            background: linear-gradient(to bottom, #c0e399 50%, #F7C0CA 50%);
            background-attachment: fixed;
            overflow: hidden; /* Mencegah scroll saat loading screen aktif */
            transition: background 0.5s ease; /* Transisi untuk perubahan background */
        }
        /* --- 1. Gaya untuk Loading Screen --- */
        #loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            /* Latar belakang loading screen SAMA dengan body */
            background: linear-gradient(to bottom, #c0e399 50%, #F7C0CA 50%);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: opacity 1s ease-out;
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
            border-radius: 50px;
            cursor: pointer;
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1);
        }
        #startButton.visible {
            opacity: 1;
            transform: translateY(0);
        }
        #startButton:hover {
            background-color: white;
            color: #F7C0CA; /* Warna pink BARU saat hover */
            transform: scale(1.05);
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
        }
        /* --- 2. Gaya untuk Halaman Utama (Sesuai Gambar) --- */
        #main-content {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 40px 20px; /* Memberi jarak atas-bawah dan kiri-kanan */
            visibility: hidden;
            opacity: 0;
            transition: opacity 1s ease-in;
            /* Background area konten dihapus agar menyatu dengan body */
        }
        /* Kartu utama yang membungkus semua konten */
        .content-card {
            background: linear-gradient(to bottom, #c0e399 40%, #ffffff 40%);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            max-width: 400px; /* Lebar maksimal seperti tampilan story di HP */
            width: 100%;
            padding-bottom: 30px; /* Jarak di bagian bawah kartu */
            overflow: hidden; /* Memastikan sudut rounded bekerja */
        }
        .title-section {
            padding: 40px 20px 20px 20px;
            text-align: left; /* Teks judul rata kiri */
        }
        .title-section h1 {
            font-family: 'Great Vibes', cursive; /* Font tulisan tangan */
            font-size: 3.5rem;
            color: #333;
            font-weight: 400;
            margin: 0;
        }
        .title-section p {
            font-size: 1rem;
            color: #555;
            margin-top: 5px;
        }     
        /* Kotak untuk menampung video dan foto */
        .media-box {
            background-color: white;
            border: 8px solid #F7C0CA; /* Border pink tebal */
            border-radius: 20px;
            margin: 0 30px 25px 30px; /* Jarak atas, kanan-kiri, bawah */
            padding: 15px; /* Jarak di dalam kotak */
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
        }
        /* Penampung video agar responsif */
        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%; /* Rasio 16:9 */
            height: 0;
            overflow: hidden;
            border-radius: 10px; /* Sudut rounded untuk video */
        }
        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }
        /* Placeholder untuk foto */
        .photo-placeholder {
            width: 100%;
            aspect-ratio: 1 / 1; /* Membuatnya menjadi persegi */
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #f0f0f0;
            border-radius: 10px;
        }
        .photo-placeholder p {
            font-size: 1.5rem;
            font-weight: 600;
            color: #aaa;
        }
        /* --- 3. Aturan Responsif untuk Mobile --- */
        @media (max-width: 768px) {
            .loader-content h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div id="loading-screen">
        <div class="loader-content">
            <h1>Selamat Datang</h1>
            <button id="startButton">Buka Undangan</button>
        </div>
    </div>
    <main id="main-content">
        <div class="content-card">      
            <div class="title-section">
                <h1>Untuk Ibu,</h1>
                <p>dari ayah, mas, adik</p>
            </div>
            <div class="media-box">
                <div class="video-wrapper">
                    <iframe src="https://www.youtube.com/embed/LXb3EKWsInQ" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
            </div>
            <div class="media-box">
                 <div class="photo-placeholder">
                    <p>Foto</p>
                </div>
            </div>
        </div>
    </main>
    <script>
        const loader = document.getElementById('loading-screen');
        const mainContent = document.getElementById('main-content');
        const startButton = document.getElementById('startButton');
        window.addEventListener('load', function() {
            setTimeout(() => { // Memberi jeda sedikit agar halaman benar-benar siap
                 startButton.classList.add('visible');
            }, 500);
        });
        startButton.addEventListener('click', function() {
            document.body.style.overflow = 'auto';
            document.body.style.background = '#f4f4f4'; // <-- BARIS INI MENGHILANGKAN GRADASI DI MAIN PAGE       
            loader.style.opacity = '0';
            mainContent.style.visibility = 'visible';
            mainContent.style.opacity = '1';
            setTimeout(() => {
                loader.style.display = 'none';
            }, 1000); 
        });
    </script>
</body>
</html>

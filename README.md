
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WiFi Customer Support</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            color: white;
        }

        /* Background for Login Screen */
        .login-bg {
            background: url('https://i.ibb.co.com/kMbTyGj/computer-8045000-1920-053402.jpg') no-repeat center center fixed;
            background-size: cover;
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
        }

        /* Background for Chatbot Screen */
        .chat-bg {
            background: url('https://i.ibb.co.com/C0VK24j/ai-generated-8030644-1920-053227.jpg') no-repeat center center fixed;
            background-size: cover;
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
        }

        .login-container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(0, 0, 0, 0.7);
            padding: 20px;
            border-radius: 10px;
            width: 300px;
        }

        .login-container input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
        }

        .login-container button {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .logo {
            position: absolute;
            top: 20px;
            left: 20px;
        }

        .real-time {
            position: absolute;
            top: 20px;
            right: 20px;
        }

        .chat-container {
            position: relative;
            width: 70%;
            margin: 50px auto;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 10px;
            padding: 20px;
            color: black;
        }

        .chat-container .message {
            padding: 10px;
            margin: 10px 0;
            border-radius: 10px;
        }

        .chat-container .user-message {
            background-color: #d1ecf1;
            text-align: right;
        }

        .chat-container .bot-message {
            background-color: #c3e6cb;
        }

        .copyright {
            text-align: center;
            position: absolute;
            bottom: 10px;
            width: 100%;
        }

        button.option {
            display: block;
            width: 100%;
            padding: 10px;
            margin-top: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <!-- Backgrounds -->
    <div class="login-bg" id="login-bg"></div>
    <div class="chat-bg" id="chat-bg" style="display: none;"></div>

    <!-- Login Screen -->
    <div class="login-container" id="login-container">
        <h2>Login</h2>
        <input type="text" id="username" placeholder="Username">
        <input type="text" id="ip-address" placeholder="IP Address">
        <button onclick="login()">Login</button>
    </div>

    <!-- Logos and Real-Time Clock for Login Screen -->
    <div class="logo">
        <img src="https://i.ibb.co.com/nnxZxwr/pngwing-com-053436.png" alt="ZTE Logo" width="50">
        <img src="https://i.ibb.co.com/6bmLskX/wifi-signal-053457.png" alt="WiFi Logo" width="50">
    </div>
    <div class="real-time" id="real-time"></div>

    <!-- Chatbot Screen (hidden by default) -->
    <div id="chat-container" class="chat-container" style="display: none;">
        <div class="message bot-message" id="chat-message">Selamat datang user <span id="user-name"></span> dengan IP <span id="user-ip"></span>. Apakah ada keluhan atau masalah pada server jaringan Anda yang saat ini sedang Anda hadapi? Jika YA, ketuk opsi di bawah ini:</div>
        <button class="option" onclick="handleOption(1)">Keluhan</button>
        <button class="option" onclick="handleOption(2)">Tidak ada</button>
    </div>

    <!-- Real-Time Clock for Chatbot Screen -->
    <div class="real-time" id="chat-real-time" style="display: none;"></div>

    <div class="copyright">
        &copy; 2024 ZTE Pusat Keluhan
    </div>

    <script>
        let userName = '';
        let userIp = '';
        let serverId = '';

        function updateClock() {
            const now = new Date();
            const timeString = now.toLocaleTimeString();
            const dateString = now.toLocaleDateString();
            document.getElementById('real-time').innerText = `${dateString} ${timeString}`;
            document.getElementById('chat-real-time').innerText = `${dateString} ${timeString}`;
        }

        function login() {
            userName = document.getElementById('username').value;
            userIp = document.getElementById('ip-address').value;
            document.getElementById('login-container').style.display = 'none';
            document.getElementById('login-bg').style.display = 'none';
            document.getElementById('chat-container').style.display = 'block';
            document.getElementById('chat-bg').style.display = 'block';
            document.getElementById('chat-real-time').style.display = 'block';
            document.getElementById('user-name').innerText = userName;
            document.getElementById('user-ip').innerText = userIp;
        }

        function handleOption(option) {
            const chatMessage = document.getElementById('chat-message');
            if (option === 1) {
                chatMessage.innerHTML = 'Keluhan apa yang sedang Anda hadapi? Pilih opsi di bawah ini:';
                document.querySelectorAll('.option').forEach((button, index) => {
                    button.innerText = index === 0 ? 'Masalah jaringan' : 'Kesalahan jaringan';
                    button.setAttribute('onclick', `handleComplaint(${index + 1})`);
                });
            } else if (option === 2) {
                chatMessage.innerHTML = 'Jika tidak ada keluhan, terimakasih telah masuk ke dalam website keluhan kami 🙏';
                document.querySelectorAll('.option').forEach(button => button.style.display = 'none');
            }
        }

        function handleComplaint(option) {
            const chatMessage = document.getElementById('chat-message');
            if (option === 1) {
                chatMessage.innerHTML = 'Apakah masalah jaringan yang sedang Anda hadapi adalah tidak dapat terkoneksi jaringan pada saat log in jaringan?';
                document.querySelectorAll('.option').forEach((button, index) => {
                    button.innerText = index === 0 ? 'Ya' : 'Tidak';
                    button.setAttribute('onclick', `handleConnectionIssue(${index + 1})`);
                });
            } else if (option === 2) {
                chatMessage.innerHTML = 'Mohon maaf, fitur ini belum tersedia. Silakan kembali ke halaman utama.';
                document.querySelectorAll('.option').forEach(button => button.style.display = 'none');
            }
        }

        function handleConnectionIssue(option) {
            const chatMessage = document.getElementById('chat-message');
            if (option === 1) {
                chatMessage.innerHTML = `Baik user ${userName} dengan IP ${userIp}, segera kami lakukan diagnostic server. Mohon tunggu sekitar 1 menit.`;
                document.querySelectorAll('.option').forEach(button => button.style.display = 'none');
                setTimeout(() => {
                    chatMessage.innerHTML = `Mohon maaf atas ketidaknyamanannya user ${userName}. Setelah kami lakukan diagnostic server, server IP Anda saat ini sedang down. Jika ingin tahu info lebih lanjut klik lanjut:`;
                    document.querySelectorAll('.option').forEach((button, index) => {
                        button.style.display = 'block';
                        button.innerText = index === 0 ? 'Lanjut' : 'Tidak, Terimakasih';
                        button.setAttribute('onclick', `handleDiagnostic(${index + 1})`);
                    });
                }, 10000); // 10 seconds delay
            } else if (option === 2) {
                chatMessage.innerHTML = 'Silakan kembali ke halaman utama.';
                document.querySelectorAll('.option').forEach(button => button.style.display = 'none');
            }
        }

        function handleDiagnostic(option) {
            const chatMessage = document.getElementById('chat-message');
            if (option === 1) {
                serverId = Math.floor(Math.random() * 1000000);
                chatMessage.innerHTML = `Nomor ID server ${serverId} dengan IP ${userIp} saat ini server Anda sedang down karena ada beberapa masalah pada keamanan sistem server. Untuk info lebih lengkap bisa menghubungi ADMIN center atau Admin reseller Anda. Jika Anda ingin mengetahui kapan server akan pulih atau jadwal pemeliharaan server akan dilakukan oleh pihak ZTE, pilih opsi di bawah ini:`;
                document.querySelectorAll('.option').forEach((button, index) => {
                    button.style.display = 'block';
                    button.innerText = index === 0 ? 'Waktu server saya pulih' : 'Jadwal pemeliharaan server';
                    button.setAttribute('onclick', `handleServerInfo(${index + 1})`);
                });
            } else if (option === 2) {
                chatMessage.innerHTML = 'Silakan kembali ke halaman utama.';
                document.querySelectorAll('.option').forEach(button => button.style.display = 'none');
            }
        }

        function handleServerInfo(option) {
            const chatMessage = document.getElementById('chat-message');
            if (option === 1) {
                chatMessage.innerHTML = `Server Anda akan pulih pada jam 9 siang dengan ID pesanan ${serverId} dan IP ${userIp}. Terimakasih...🙏`;
                document.querySelectorAll('.option').forEach(button => button.style.display = 'none');
            } else if (option === 2) {
                chatMessage.innerHTML = `Untuk user ${userName} dengan IP ${userIp}, jadwal pemeliharaan server karena bersifat sensitif dan privat tidak dapat diberikan secara langsung kepada setiap user. User bisa menghubungi admin retail. Terimakasih sudah menghubungi pusat keluhan ZTE 🙏!!`;
                document.querySelectorAll('.option').forEach(button => button.style.display = 'none');
            }
        }

        setInterval(updateClock, 1000);
    </script>
</body>
</html>

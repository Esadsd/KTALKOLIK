# KTALKOLIK

<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KTALKOLIK - Futbol Maçı İstatistikleri</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            text-align: center;
        }

        .container {
            background: rgba(255, 255, 255, 0.1);
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            max-width: 800px;
            width: 100%;
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            color: #fff;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .subtitle {
            font-size: 1.2rem;
            color: #e0e0e0;
            margin-bottom: 30px;
        }

        .menu {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .menu-button {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: white;
            font-size: 1rem;
            border-radius: 10px;
            cursor: pointer;
            transition: background 0.3s ease, transform 0.2s ease;
        }

        .menu-button:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-3px);
        }

        .menu-button i {
            font-size: 1.2rem;
        }

        .menu-button span {
            font-weight: 500;
        }

        .hidden {
            display: none;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            color: #e0e0e0;
        }

        input, select, textarea {
            width: 100%;
            padding: 8px;
            box-sizing: border-box;
            border: 1px solid rgba(255, 255, 255, 0.2);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            border-radius: 5px;
        }

        button {
            padding: 10px 20px;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: white;
            border-radius: 10px;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        button:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        .match-list {
            margin-top: 20px;
        }

        .match-item {
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            cursor: pointer;
            transition: transform 0.2s ease;
        }

        .match-item:hover {
            transform: translateY(-3px);
        }

        .delete-btn {
            background: #dc3545;
            border: none;
            padding: 5px 10px;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        .delete-btn:hover {
            background: #c82333;
        }

        #playerStats {
            margin-top: 20px;
            text-align: left;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
        }

        #playerStats h3 {
            margin-top: 0;
            color: #fff;
        }

        #playerStats p {
            margin: 5px 0;
            color: #e0e0e0;
        }

        #matchDetail {
            margin-top: 20px;
            text-align: left;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
        }

        #matchDetail h3 {
            margin-top: 0;
            color: #fff;
        }

        #matchDetail p {
            margin: 5px 0;
            color: #e0e0e0;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }

        th, td {
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 8px;
            text-align: left;
        }

        th {
            background: rgba(255, 255, 255, 0.1);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>KTALKOLIK</h1>
        <p class="subtitle">Futbol Maçı İstatistikleri ve Analiz Platformu</p>
        <div id="mainMenu" class="menu">
            <button onclick="showPlayerView()" class="menu-button">
                <i class="fas fa-user"></i>
                <span>Sporcu Girişi</span>
            </button>
            <button onclick="showAdminLogin()" class="menu-button">
                <i class="fas fa-lock"></i>
                <span>Yetkili Girişi</span>
            </button>
            <button onclick="showProfileView()" class="menu-button">
                <i class="fas fa-chart-line"></i>
                <span>Profil ve İstatistikler</span>
            </button>
        </div>

        <!-- Sporcu Görüntüleme Ekranı -->
        <div id="playerView" class="hidden">
            <h2>Maç İstatistikleri</h2>
            <div class="match-list" id="playerMatchList"></div>
            <button onclick="showMainMenu()">Ana Menüye Dön</button>
        </div>

        <!-- Yetkili Giriş Ekranı -->
        <div id="adminLogin" class="hidden">
            <h2>Yetkili Girişi</h2>
            <form id="adminForm">
                <div class="form-group">
                    <label for="adminPassword">Şifre:</label>
                    <input type="password" id="adminPassword" required>
                </div>
                <button type="submit">Giriş Yap</button>
            </form>
            <button onclick="showMainMenu()">Ana Menüye Dön</button>
        </div>

        <!-- Yetkili Maç İstatistikleri Ekranı -->
        <div id="adminView" class="hidden">
            <h2>Maç İstatistikleri (Yetkili)</h2>
            <form id="matchForm">
                <div class="form-group">
                    <label for="team1">Takım 1:</label>
                    <input type="text" id="team1" required>
                </div>
                <div class="form-group">
                    <label for="team2">Takım 2:</label>
                    <input type="text" id="team2" required>
                </div>
                <div class="form-group">
                    <label for="score1">Takım 1 Skor:</label>
                    <input type="number" id="score1" required>
                </div>
                <div class="form-group">
                    <label for="score2">Takım 2 Skor:</label>
                    <input type="number" id="score2" required>
                </div>
                <div class="form-group">
                    <label for="date">Maç Tarihi:</label>
                    <input type="date" id="date" required>
                </div>
                <div class="form-group">
                    <label for="team1Players">Takım 1 Oyuncuları (Forma No - İsim - Pozisyon - Gol - Asist - Sarı Kart - Kırmızı Kart):</label>
                    <textarea id="team1Players" rows="5" placeholder="Örnek: 10 - Messi - Forvet - 1 - 2 - 0 - 0"></textarea>
                </div>
                <div class="form-group">
                    <label for="team2Players">Takım 2 Oyuncuları (Forma No - İsim - Pozisyon - Gol - Asist - Sarı Kart - Kırmızı Kart):</label>
                    <textarea id="team2Players" rows="5" placeholder="Örnek: 7 - Ronaldo - Forvet - 2 - 0 - 1 - 0"></textarea>
                </div>
                <button type="submit">Maçı Kaydet</button>
            </form>
            <div class="match-list" id="adminMatchList"></div>
            <button onclick="showMainMenu()">Ana Menüye Dön</button>
        </div>

        <!-- Maç Detay Sayfası -->
        <div id="matchDetail" class="hidden">
            <h2>Maç Detayları</h2>
            <div id="detailContent"></div>
            <button onclick="closeDetail()">Geri Dön</button>
        </div>

        <!-- Profil ve İstatistikler Ekranı -->
        <div id="profileView" class="hidden">
            <h2>Oyuncu Profili ve İstatistikler</h2>
            <div class="form-group">
                <label for="playerSearch">Oyuncu Ara:</label>
                <input type="text" id="playerSearch" placeholder="Oyuncu adı girin...">
                <button onclick="searchPlayer()">Ara</button>
            </div>
            <div id="playerStats"></div>
            <button onclick="showMainMenu()">Ana Menüye Dön</button>
        </div>
    </div>

    <script>
        const mainMenu = document.getElementById('mainMenu');
        const playerView = document.getElementById('playerView');
        const adminLogin = document.getElementById('adminLogin');
        const adminView = document.getElementById('adminView');
        const profileView = document.getElementById('profileView');
        const playerMatchList = document.getElementById('playerMatchList');
        const adminMatchList = document.getElementById('adminMatchList');
        const adminForm = document.getElementById('adminForm');
        const matchForm = document.getElementById('matchForm');
        const matchDetail = document.getElementById('matchDetail');
        const detailContent = document.getElementById('detailContent');
        const playerStatsDiv = document.getElementById('playerStats');
        const editMatchView = document.getElementById('editMatchView');
        const editMatchForm = document.getElementById('editMatchForm');

        let matches = JSON.parse(localStorage.getItem('matches')) || [];
        let editingMatchIndex = null;

        function showMainMenu() {
            mainMenu.classList.remove('hidden');
            playerView.classList.add('hidden');
            adminLogin.classList.add('hidden');
            adminView.classList.add('hidden');
            profileView.classList.add('hidden');
            matchDetail.classList.add('hidden');
        }

        function showPlayerView() {
            mainMenu.classList.add('hidden');
            playerView.classList.remove('hidden');
            adminLogin.classList.add('hidden');
            adminView.classList.add('hidden');
            profileView.classList.add('hidden');
            matchDetail.classList.add('hidden');
            updatePlayerMatchList();
        }

        function showAdminLogin() {
            mainMenu.classList.add('hidden');
            playerView.classList.add('hidden');
            adminLogin.classList.remove('hidden');
            adminView.classList.add('hidden');
            profileView.classList.add('hidden');
            matchDetail.classList.add('hidden');
        }

        function showAdminView() {
            mainMenu.classList.add('hidden');
            playerView.classList.add('hidden');
            adminLogin.classList.add('hidden');
            adminView.classList.remove('hidden');
            profileView.classList.add('hidden');
            matchDetail.classList.add('hidden');
            updateAdminMatchList();
        }

        function showProfileView() {
            mainMenu.classList.add('hidden');
            playerView.classList.add('hidden');
            adminLogin.classList.add('hidden');
            adminView.classList.add('hidden');
            profileView.classList.remove('hidden');
            matchDetail.classList.add('hidden');
        }

        function showMatchDetail(index) {
            const match = matches[index];
            detailContent.innerHTML = `
                <h3>${match.team1} ${match.score1} - ${match.score2} ${match.team2}</h3>
                <p><strong>Tarih:</strong> ${match.date}</p>
                <h4>${match.team1} Kadrosu:</h4>
                ${createTable(match.team1Players)}
                <h4>${match.team2} Kadrosu:</h4>
                ${createTable(match.team2Players)}
            `;
            matchDetail.classList.remove('hidden');
        }

        function closeDetail() {
            matchDetail.classList.add('hidden');
        }

        function createTable(players) {
            const rows = players.split('\n').filter(row => row.trim() !== '');
            let table = '<table>';
            table += '<tr><th>Forma No</th><th>İsim</th><th>Pozisyon</th><th>Gol</th><th>Asist</th><th>Sarı Kart</th><th>Kırmızı Kart</th></tr>';
            rows.forEach(row => {
                const [number, name, position, goals, assists, yellowCards, redCards] = row.split(' - ');
                table += `<tr><td>${number}</td><td>${name}</td><td>${position}</td><td>${goals}</td><td>${assists}</td><td>${yellowCards}</td><td>${redCards}</td></tr>`;
            });
            table += '</table>';
            return table;
        }

        function updatePlayerMatchList() {
            playerMatchList.innerHTML = '';
            matches.forEach((match, index) => {
                const matchItem = document.createElement('div');
                matchItem.classList.add('match-item');
                matchItem.innerHTML = `
                    <strong>${match.team1} ${match.score1} - ${match.score2} ${match.team2}</strong><br>
                    <em>Tarih: ${match.date}</em>
                `;
                matchItem.addEventListener('click', () => showMatchDetail(index));
                playerMatchList.appendChild(matchItem);
            });
        }

        function updateAdminMatchList() {
            adminMatchList.innerHTML = '';
            matches.forEach((match, index) => {
                const matchItem = document.createElement('div');
                matchItem.classList.add('match-item');
                matchItem.innerHTML = `
                    <strong>${match.team1} ${match.score1} - ${match.score2} ${match.team2}</strong><br>
                    <em>Tarih: ${match.date}</em>
                    <button class="delete-btn" onclick="deleteMatch(${index})">Sil</button>
                    <button class="delete-btn" style="background-color: #ffc107; color: black;" onclick="editMatch(${index})">Düzenle</button>
                `;
                adminMatchList.appendChild(matchItem);
            });
        }

        function deleteMatch(index) {
            matches.splice(index, 1);
            localStorage.setItem('matches', JSON.stringify(matches));
            updateAdminMatchList();
            updatePlayerMatchList();
        }

        function editMatch(index) {
            editingMatchIndex = index;
            const match = matches[index];
            document.getElementById('team1').value = match.team1;
            document.getElementById('team2').value = match.team2;
            document.getElementById('score1').value = match.score1;
            document.getElementById('score2').value = match.score2;
            document.getElementById('date').value = match.date;
            document.getElementById('team1Players').value = match.team1Players;
            document.getElementById('team2Players').value = match.team2Players;
            showAdminView();
        }

        function searchPlayer() {
            const playerName = document.getElementById('playerSearch').value.trim();
            if (!playerName) {
                alert("Lütfen bir oyuncu adı girin!");
                return;
            }

            let totalStats = {
                matchesPlayed: 0,
                goals: 0,
                assists: 0,
                yellowCards: 0,
                redCards: 0
            };

            matches.forEach(match => {
                const team1Players = match.team1Players.split('\n').filter(row => row.trim() !== '');
                const team2Players = match.team2Players.split('\n').filter(row => row.trim() !== '');
                const allPlayers = [...team1Players, ...team2Players];

                allPlayers.forEach(player => {
                    const [number, name, position, goals, assists, yellowCards, redCards] = player.split(' - ');
                    if (name.trim().toLowerCase() === playerName.toLowerCase()) {
                        totalStats.matchesPlayed += 1;
                        totalStats.goals += parseInt(goals) || 0;
                        totalStats.assists += parseInt(assists) || 0;
                        totalStats.yellowCards += parseInt(yellowCards) || 0;
                        totalStats.redCards += parseInt(redCards) || 0;
                    }
                });
            });

            if (totalStats.matchesPlayed > 0) {
                playerStatsDiv.innerHTML = `
                    <h3>${playerName} İstatistikleri</h3>
                    <p><strong>Oynanan Maç Sayısı:</strong> ${totalStats.matchesPlayed}</p>
                    <p><strong>Toplam Gol:</strong> ${totalStats.goals}</p>
                    <p><strong>Toplam Asist:</strong> ${totalStats.assists}</p>
                    <p><strong>Toplam Sarı Kart:</strong> ${totalStats.yellowCards}</p>
                    <p><strong>Toplam Kırmızı Kart:</strong> ${totalStats.redCards}</p>
                `;
            } else {
                playerStatsDiv.innerHTML = `<p>${playerName} adında bir oyuncu bulunamadı.</p>`;
            }
        }

        adminForm.addEventListener('submit', function(event) {
            event.preventDefault();
            const password = document.getElementById('adminPassword').value;
            if (password === '12345') {
                showAdminView();
            } else {
                alert('Hatalı şifre!');
            }
            adminForm.reset();
        });

        matchForm.addEventListener('submit', function(event) {
            event.preventDefault();
            const team1 = document.getElementById('team1').value;
            const team2 = document.getElementById('team2').value;
            const score1 = document.getElementById('score1').value;
            const score2 = document.getElementById('score2').value;
            const date = document.getElementById('date').value;
            const team1Players = document.getElementById('team1Players').value;
            const team2Players = document.getElementById('team2Players').value;

            if (editingMatchIndex !== null) {
                // Düzenleme modunda
                matches[editingMatchIndex] = { team1, team2, score1, score2, date, team1Players, team2Players };
                editingMatchIndex = null;
            } else {
                // Yeni maç ekleme
                matches.push({ team1, team2, score1, score2, date, team1Players, team2Players });
            }

            localStorage.setItem('matches', JSON.stringify(matches));
            updateAdminMatchList();
            updatePlayerMatchList();
            matchForm.reset();
            showAdminView();
        });

        updateAdminMatchList();
        updatePlayerMatchList();
        showMainMenu();
    </script>
</body>
</html>

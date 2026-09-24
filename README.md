<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#0b0f1a">
  <title>FireZone Tournament</title>

  <style>
    :root {
      --bg: #080b14;
      --panel: #111827;
      --panel-2: #182235;
      --line: rgba(255,255,255,.09);
      --text: #f8fafc;
      --muted: #94a3b8;
      --orange: #ff6b00;
      --yellow: #ffc107;
      --green: #22d3a1;
      --blue: #5b7cff;
      --red: #ff5370;
      --radius: 18px;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Inter, "Segoe UI", Arial, sans-serif;
    }

    body {
      min-height: 100vh;
      color: var(--text);
      background:
        radial-gradient(circle at 10% 0%, rgba(255,107,0,.18), transparent 28%),
        radial-gradient(circle at 100% 20%, rgba(91,124,255,.13), transparent 30%),
        var(--bg);
    }

    button,
    input {
      font: inherit;
    }

    button {
      cursor: pointer;
    }

    .app {
      width: 100%;
      max-width: 500px;
      min-height: 100vh;
      margin: auto;
      background: rgba(8,11,20,.94);
      overflow: hidden;
      position: relative;
      padding-bottom: 82px;
    }

    .hidden {
      display: none !important;
    }

    /* Login */
    .login-screen {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 22px;
    }

    .login-box {
      width: 100%;
      max-width: 410px;
    }

    .brand {
      text-align: center;
      margin-bottom: 25px;
    }

    .brand-mark {
      width: 94px;
      height: 94px;
      margin: auto auto 15px;
      display: grid;
      place-items: center;
      font-size: 42px;
      background: linear-gradient(135deg, var(--orange), var(--yellow));
      clip-path: polygon(50% 0, 93% 25%, 93% 75%, 50% 100%, 7% 75%, 7% 25%);
      box-shadow: 0 0 35px rgba(255,107,0,.42);
    }

    .brand h1 {
      font-size: 29px;
      letter-spacing: 2px;
      font-weight: 950;
      background: linear-gradient(90deg, #ff6b00, #ffd166);
      color: transparent;
      background-clip: text;
    }

    .brand p {
      color: var(--muted);
      font-size: 13px;
      margin-top: 6px;
    }

    .login-card {
      padding: 22px;
      border: 1px solid var(--line);
      border-radius: 22px;
      background: linear-gradient(145deg, #151f32, #0e1524);
      box-shadow: 0 18px 45px rgba(0,0,0,.28);
    }

    .login-card h2 {
      text-align: center;
      margin-bottom: 18px;
      font-size: 20px;
    }

    .input-group {
      margin-bottom: 14px;
    }

    .input-group label {
      display: block;
      color: var(--muted);
      font-size: 12px;
      margin-bottom: 7px;
    }

    input {
      width: 100%;
      padding: 13px 14px;
      border: 1px solid var(--line);
      border-radius: 12px;
      outline: none;
      color: var(--text);
      background: #080d18;
    }

    input:focus {
      border-color: var(--orange);
      box-shadow: 0 0 0 3px rgba(255,107,0,.12);
    }

    .primary-btn,
    .green-btn,
    .outline-btn {
      width: 100%;
      border: 0;
      border-radius: 12px;
      padding: 13px;
      font-weight: 850;
      color: white;
      transition: .2s;
    }

    .primary-btn {
      background: linear-gradient(100deg, var(--orange), #ff9d00);
      box-shadow: 0 10px 22px rgba(255,107,0,.22);
    }

    .green-btn {
      background: linear-gradient(100deg, #10b981, var(--green));
    }

    .outline-btn {
      color: var(--yellow);
      background: transparent;
      border: 1px solid rgba(255,193,7,.35);
    }

    button:hover {
      transform: translateY(-1px);
      filter: brightness(1.06);
    }

    .demo-note {
      color: var(--muted);
      text-align: center;
      font-size: 11px;
      line-height: 1.5;
      margin-top: 15px;
    }

    /* Header */
    .topbar {
      position: sticky;
      top: 0;
      z-index: 10;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 14px 16px;
      border-bottom: 1px solid var(--line);
      background: rgba(8,11,20,.88);
      backdrop-filter: blur(15px);
    }

    .mini-brand {
      display: flex;
      align-items: center;
      gap: 9px;
      font-weight: 900;
      letter-spacing: .7px;
    }

    .mini-logo {
      width: 34px;
      height: 34px;
      display: grid;
      place-items: center;
      border-radius: 10px;
      background: linear-gradient(135deg, var(--orange), var(--yellow));
      font-size: 18px;
    }

    .wallet {
      display: flex;
      align-items: center;
      gap: 7px;
      padding: 8px 11px;
      border-radius: 999px;
      color: var(--green);
      font-weight: 850;
      background: rgba(34,211,161,.1);
      border: 1px solid rgba(34,211,161,.35);
      cursor: pointer;
    }

    /* Main */
    .content {
      padding: 16px;
    }

    .hero {
      position: relative;
      overflow: hidden;
      padding: 22px 18px;
      border-radius: 22px;
      background:
        linear-gradient(120deg, rgba(255,107,0,.95), rgba(113,38,0,.8)),
        url("");
      box-shadow: 0 16px 35px rgba(255,107,0,.16);
    }

    .hero::after {
      content: "🔥";
      position: absolute;
      right: -8px;
      bottom: -25px;
      font-size: 120px;
      opacity: .16;
      transform: rotate(-15deg);
    }

    .hero small {
      font-weight: 800;
      opacity: .85;
    }

    .hero h2 {
      max-width: 270px;
      font-size: 27px;
      line-height: 1.1;
      margin: 8px 0;
    }

    .hero p {
      max-width: 280px;
      font-size: 12px;
      opacity: .86;
      line-height: 1.5;
    }

    .hero button {
      margin-top: 15px;
      border: 0;
      border-radius: 10px;
      padding: 10px 14px;
      background: #fff;
      color: #9a3900;
      font-size: 12px;
      font-weight: 900;
    }

    .stats {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 9px;
      margin: 15px 0;
    }

    .stat {
      padding: 13px 8px;
      text-align: center;
      border: 1px solid var(--line);
      background: rgba(255,255,255,.035);
      border-radius: 14px;
    }

    .stat strong {
      display: block;
      font-size: 17px;
      color: var(--yellow);
    }

    .stat span {
      color: var(--muted);
      font-size: 10px;
      margin-top: 3px;
      display: block;
    }

    .section-head {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin: 21px 0 11px;
    }

    .section-head h3 {
      font-size: 17px;
    }

    .section-head span {
      color: var(--orange-2);
      font-size: 11px;
      font-weight: 800;
    }

    .tabs {
      display: flex;
      gap: 8px;
      overflow-x: auto;
      scrollbar-width: none;
      margin-bottom: 13px;
    }

    .tabs button {
      flex: 0 0 auto;
      padding: 8px 13px;
      border: 1px solid var(--line);
      border-radius: 999px;
      color: var(--muted);
      background: transparent;
      font-size: 11px;
      font-weight: 800;
    }

    .tabs button.active {
      color: #16100a;
      background: var(--yellow);
      border-color: var(--yellow);
    }

    /* Tournament cards */
    .tournament-card {
      padding: 15px;
      margin-bottom: 12px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: linear-gradient(145deg, #151f32, #0f1726);
      box-shadow: 0 10px 24px rgba(0,0,0,.15);
    }

    .card-top {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      gap: 10px;
    }

    .game-type {
      color: var(--green);
      font-size: 10px;
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: .6px;
    }

    .tournament-card h4 {
      font-size: 17px;
      margin: 5px 0;
    }

    .time-badge {
      color: var(--yellow);
      padding: 6px 8px;
      border-radius: 8px;
      white-space: nowrap;
      background: rgba(255,193,7,.1);
      font-size: 10px;
      font-weight: 800;
    }

    .card-info {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 8px;
      padding: 13px 0;
      margin-top: 11px;
      border-top: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
    }

    .info-box span {
      display: block;
      color: var(--muted);
      font-size: 10px;
      margin-bottom: 3px;
    }

    .info-box strong {
      font-size: 13px;
    }

    .card-bottom {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-top: 12px;
    }

    .progress {
      flex: 1;
    }

    .progress-text {
      display: flex;
      justify-content: space-between;
      color: var(--muted);
      font-size: 10px;
      margin-bottom: 5px;
    }

    .progress-bar {
      height: 6px;
      overflow: hidden;
      border-radius: 99px;
      background: #263248;
    }

    .progress-bar i {
      display: block;
      height: 100%;
      border-radius: inherit;
      background: linear-gradient(90deg, var(--orange), var(--yellow));
    }

    .join-btn {
      border: 0;
      border-radius: 10px;
      padding: 10px 13px;
      color: white;
      background: linear-gradient(100deg, #10b981, #22d3a1);
      font-size: 12px;
      font-weight: 900;
    }

    .referral {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      margin-top: 17px;
      padding: 14px;
      border: 1px dashed rgba(255,193,7,.45);
      border-radius: 15px;
      background: rgba(255,193,7,.06);
    }

    .referral strong {
      color: var(--yellow);
      display: block;
      font-size: 14px;
    }

    .referral small {
      display: block;
      color: var(--muted);
      font-size: 10px;
      margin-top: 4px;
    }

    .share-btn {
      border: 0;
      border-radius: 9px;
      padding: 9px 12px;
      color: #201500;
      background: var(--yellow);
      font-size: 11px;
      font-weight: 900;
    }

    /* Bottom nav */
    .bottom-nav {
      position: fixed;
      bottom: 0;
      left: 50%;
      z-index: 20;
      width: 100%;
      max-width: 500px;
      transform: translateX(-50%);
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      padding: 10px 8px calc(10px + env(safe-area-inset-bottom));
      border-top: 1px solid var(--line);
      background: rgba(12,18,31,.95);
      backdrop-filter: blur(16px);
    }

    .nav-btn {
      border: 0;
      color: var(--muted);
      background: transparent;
      font-size: 10px;
      font-weight: 800;
    }

    .nav-btn span {
      display: block;
      font-size: 19px;
      margin-bottom: 3px;
    }

    .nav-btn.active {
      color: var(--orange-2);
    }

    /* Modal */
    .modal {
      position: fixed;
      inset: 0;
      z-index: 50;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 20px;
      background: rgba(0,0,0,.76);
    }

    .modal.show {
      display: flex;
    }

    .modal-card {
      width: 100%;
      max-width: 390px;
      padding: 20px;
      border: 1px solid var(--line);
      border-radius: 20px;
      background: linear-gradient(145deg, #172238, #0d1524);
    }

    .modal-card h3 {
      margin-bottom: 15px;
      text-align: center;
      color: var(--yellow);
    }

    .modal-actions {
      display: flex;
      gap: 9px;
      margin-top: 12px;
    }

    .modal-actions button {
      flex: 1;
      border: 0;
      border-radius: 10px;
      padding: 12px;
      font-weight: 850;
    }

    .cancel {
      color: white;
      background: #293449;
    }

    .confirm {
      color: white;
      background: linear-gradient(100deg, #10b981, #22d3a1);
    }

    .toast {
      position: fixed;
      left: 50%;
      bottom: 90px;
      z-index: 100;
      opacity: 0;
      transform: translate(-50%, 14px);
      padding: 10px 14px;
      border: 1px solid var(--line);
      border-radius: 999px;
      color: white;
      background: #111827;
      font-size: 12px;
      font-weight: 800;
      transition: .25s;
      pointer-events: none;
    }

    .toast.show {
      opacity: 1;
      transform: translate(-50%, 0);
    }

    @media (max-width: 370px) {
      .hero h2 {
        font-size: 23px;
      }

      .time-badge {
        font-size: 9px;
      }

      .card-bottom {
        align-items: stretch;
        flex-direction: column;
      }

      .join-btn {
        width: 100%;
      }
    }
  </style>
</head>

<body>
  <div class="app">

    <!-- LOGIN -->
    <section id="loginScreen" class="login-screen">
      <div class="login-box">
        <div class="brand">
          <div class="brand-mark">🔥</div>
          <h1>FIREZONE</h1>
          <p>India's Next Gaming Tournament Arena</p>
        </div>

        <div class="login-card">
          <h2>Start Your Battle</h2>

          <div class="input-group">
            <label>Your Name</label>
            <input id="nameInput" type="text" placeholder="Enter your name">
          </div>

          <div class="input-group">
            <label>Free Fire UID</label>
            <input id="uidInput" type="number" placeholder="Enter your FF UID">
          </div>

          <button class="primary-btn" onclick="loginUser()">
            Enter Arena
          </button>

          <p class="demo-note">
            Demo version: login और wallet data इसी browser में save होगा।
          </p>
        </div>
      </div>
    </section>

    <!-- APP -->
    <section id="appScreen" class="hidden">
      <header class="topbar">
        <div class="mini-brand">
          <div class="mini-logo">🔥</div>
          <span>FIREZONE</span>
        </div>

        <div class="wallet" onclick="openWallet()">
          💰 <span id="walletAmount">₹0</span>
        </div>
      </header>

      <main class="content">

        <div class="hero">
          <small>WELCOME BACK, <span id="userName">PLAYER</span></small>
          <h2>Prove Your Skills. Win Big.</h2>
          <p>Daily Free Fire tournaments में participate करें और leaderboard पर अपनी जगह बनाएं।</p>
          <button onclick="scrollToMatches()">Explore Matches →</button>
        </div>

        <div class="stats">
          <div class="stat">
            <strong>12K+</strong>
            <span>Players</span>
          </div>
          <div class="stat">
            <strong>₹2.5L</strong>
            <span>Prize Won</span>
          </div>
          <div class="stat">
            <strong>24/7</strong>
            <span>Matches</span>
          </div>
        </div>

        <div class="section-head">
          <h3>Live Arena</h3>
          <span>VIEW ALL</span>
        </div>

        <div class="tabs">
          <button class="active" onclick="filterMatches('all', this)">All</button>
          <button onclick="filterMatches('solo', this)">Solo</button>
          <button onclick="filterMatches('duo', this)">Duo</button>
          <button onclick="filterMatches('squad', this)">Squad</button>
        </div>

        <div id="matches"></div>

        <div class="referral">
          <div>
            <strong>Refer & Earn ₹2</strong>
            <small>Friends को invite करें और rewards पाएं।</small>
          </div>
          <button class="share-btn" onclick="shareWebsite()">SHARE</button>
        </div>

      </main>

      <nav class="bottom-nav">
        <button class="nav-btn active" onclick="navMessage('Home', this)">
          <span>⌂</span>Home
        </button>
        <button class="nav-btn" onclick="navMessage('My Matches', this)">
          <span>🎮</span>Matches
        </button>
        <button class="nav-btn" onclick="navMessage('Leaderboard', this)">
          <span>🏆</span>Rank
        </button>
        <button class="nav-btn" onclick="navMessage('Profile', this)">
          <span>👤</span>Profile
        </button>
      </nav>
    </section>
  </div>

  <!-- WALLET MODAL -->
  <div id="walletModal" class="modal">
    <div class="modal-card">
      <h3>Demo Wallet</h3>

      <div class="input-group">
        <label>Amount Add करें</label>
        <input id="amountInput" type="number" min="1" placeholder="Enter amount">
      </div>

      <p class="demo-note">
        यह केवल testing wallet है। Real payment connected नहीं है।
      </p>

      <div class="modal-actions">
        <button class="cancel" onclick="closeWallet()">Cancel</button>
        <button class="confirm" onclick="addMoney()">Add Money</button>
      </div>
    </div>
  </div>

  <div id="toast" class="toast"></div>

  <script>
    const matches = [
      {
        type: "solo",
        title: "Solo Clash Premium",
        time: "05:00 PM",
        entry: 10,
        prize: 200,
        players: "38/48",
        progress: 80
      },
      {
        type: "duo",
        title: "Duo Thunder Cup",
        time: "06:30 PM",
        entry: 20,
        prize: 500,
        players: "26/32",
        progress: 81
      },
      {
        type: "squad",
        title: "Squad Battle Royale",
        time: "08:00 PM",
        entry: 40,
        prize: 1000,
        players: "44/48",
        progress: 92
      },
      {
        type: "solo",
        title: "Night Sniper Challenge",
        time: "10:00 PM",
        entry: 15,
        prize: 350,
        players: "18/32",
        progress: 56
      }
    ];

    let wallet = Number(localStorage.getItem("fz_wallet") || 0);

    function loginUser() {
      const name = document.getElementById("nameInput").value.trim();
      const uid = document.getElementById("uidInput").value.trim();

      if (!name || !uid) {
        showToast("Name और FF UID दोनों भरें");
        return;
      }

      localStorage.setItem("fz_name", name);
      localStorage.setItem("fz_uid", uid);

      document.getElementById("userName").textContent = name.toUpperCase();
      document.getElementById("loginScreen").classList.add("hidden");
      document.getElementById("appScreen").classList.remove("hidden");

      updateWallet();
      renderMatches("all");
      showToast("Welcome to FireZone!");
    }

    function renderMatches(type) {
      const box = document.getElementById("matches");

      const list = type === "all"
        ? matches
        : matches.filter(item => item.type === type);

      box.innerHTML = list.map((match, index) => `
        <article class="tournament-card">
          <div class="card-top">
            <div>
              <div class="game-type">${match.type} tournament</div>
              <h4>${match.title}</h4>
            </div>
            <div class="time-badge">🕒 ${match.time}</div>
          </div>

          <div class="card-info">
            <div class="info-box">
              <span>Entry Fee</span>
              <strong>₹${match.entry}</strong>
            </div>
            <div class="info-box">
              <span>Prize Pool</span>
              <strong>₹${match.prize}</strong>
            </div>
            <div class="info-box">
              <span>Players</span>
              <strong>${match.players}</strong>
            </div>
          </div>

          <div class="card-bottom">
            <div class="progress">
              <div class="progress-text">
                <span>Slots Filled</span>
                <span>${match.progress}%</span>
              </div>
              <div class="progress-bar">
                <i style="width:${match.progress}%"></i>
              </div>
            </div>
            <button class="join-btn"
              onclick="joinMatch(${match.entry}, '${match.title}')">
              JOIN
            </button>
          </div>
        </article>
      `).join("");

      if (!list.length) {
        box.innerHTML = `<p class="demo-note">इस category में अभी कोई match नहीं है।</p>`;
      }
    }

    function filterMatches(type, button) {
      document.querySelectorAll(".tab

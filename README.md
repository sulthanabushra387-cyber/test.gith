<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Suraksha Alert – Child & Women Safety</title>

  <!-- =========================
       BASIC STYLES (CSS)
       ========================= -->
  <style>
    :root {
      --danger-red: #b00020;
      --alert-yellow: #ffcc00;
      --dark: #1f1f1f;
      --light: #ffffff;
      --gray: #f4f4f4;
    }

    * {
      box-sizing: border-box;
      font-family: Arial, Helvetica, sans-serif;
    }

    body {
      margin: 0;
      background: var(--gray);
      color: var(--dark);
    }

    header {
      background: #003366;
      color: white;
      padding: 1rem;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 1.5rem;
    }

    header p {
      margin: 0.3rem 0 0;
      font-size: 0.9rem;
    }

    main {
      padding: 1rem;
    }

    /* =========================
       ALERT POPUP
       ========================= */
    #alertPopup {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.9);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 9999;
    }

    .alert-box {
      background: linear-gradient(135deg, var(--danger-red), var(--alert-yellow));
      color: white;
      width: 95%;
      max-width: 500px;
      padding: 1.2rem;
      border-radius: 12px;
      text-align: center;
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.03); }
      100% { transform: scale(1); }
    }

    .alert-box h2 {
      margin-top: 0;
      font-size: 1.4rem;
    }

    .alert-box button {
      margin-top: 1rem;
      padding: 0.7rem 1.2rem;
      font-size: 1rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }

    .close-btn {
      background: #222;
      color: white;
      opacity: 0.5;
      pointer-events: none;
    }

    /* =========================
       ALERT DETAILS CARD
       ========================= */
    .card {
      background: white;
      border-radius: 10px;
      padding: 1rem;
      margin-bottom: 1rem;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    .card h3 {
      margin-top: 0;
      color: var(--danger-red);
    }

    .person-photo {
      width: 100%;
      height: 180px;
      background: #ddd;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 8px;
      margin-bottom: 0.5rem;
      font-size: 0.9rem;
    }

    /* =========================
       ACTION BUTTONS
       ========================= */
    .actions {
      display: flex;
      flex-direction: column;
      gap: 0.7rem;
    }

    .actions button {
      padding: 0.9rem;
      font-size: 1rem;
      border-radius: 10px;
      border: none;
      cursor: pointer;
    }

    .seen-btn { background: #006600; color: white; }
    .tip-btn { background: #004c99; color: white; }
    .call-btn { background: var(--danger-red); color: white; }

    /* =========================
       FORMS
       ========================= */
    form input, form textarea, form select {
      width: 100%;
      padding: 0.6rem;
      margin-bottom: 0.6rem;
      border-radius: 6px;
      border: 1px solid #ccc;
    }

    form button {
      padding: 0.7rem;
      background: #003366;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }

    /* =========================
       FOOTER
       ========================= */
    footer {
      background: #003366;
      color: white;
      text-align: center;
      padding: 0.7rem;
      font-size: 0.8rem;
    }

    @media (min-width: 600px) {
      main {
        max-width: 800px;
        margin: auto;
      }
    }
  </style>
</head>
<body>

  <!-- =========================
       HEADER
       ========================= -->
  <header>
    <h1>Suraksha Alert</h1>
    <p>National Child & Women Safety Emergency System</p>
  </header>

  <main>

    <!-- =========================
         ALERT DETAILS
         ========================= -->
    <section class="card">
      <h3>🚨 Missing Child Alert</h3>
      <div class="person-photo">Photo Placeholder</div>
      <p><strong>Age:</strong> 7 Years</p>
      <p><strong>Last Seen:</strong> 16 Sept, 9:30 PM</p>
      <p><strong>Location:</strong> 16th Street, City Center</p>
      <p><strong>Clothing:</strong> Tan skirt, white top</p>
      <p><strong>Instructions:</strong> Check abandoned buildings, nearby theaters, and private properties.</p>
    </section>

    <!-- =========================
         MAP PLACEHOLDER
         ========================= -->
    <section class="card">
      <h3>📍 Last Seen Location</h3>
      <div style="height:200px;background:#ccc;border-radius:8px;display:flex;align-items:center;justify-content:center;">
        Google Maps Placeholder
      </div>
    </section>

    <!-- =========================
         PUBLIC ACTIONS
         ========================= -->
    <section class="card">
      <h3>🤝 Public Action</h3>
      <div class="actions">
        <button class="seen-btn">I Have Seen This Person</button>
        <button class="tip-btn" onclick="toggleTipForm()">Submit a Tip</button>
        <button class="call-btn" onclick="callEmergency()">Call Emergency (112)</button>
      </div>
    </section>

    <!-- =========================
         TIP FORM
         ========================= -->
    <section class="card" id="tipForm" style="display:none;">
      <h3>📝 Submit Tip</h3>
      <form onsubmit="submitTip(event)">
        <input type="text" placeholder="Your Name (optional)" />
        <input type="text" placeholder="Your Location" required />
        <textarea placeholder="Message" required></textarea>
        <button type="submit">Send Tip</button>
      </form>
    </section>

    <!-- =========================
         ADMIN PANEL (MOCK)
         ========================= -->
    <section class="card">
      <h3>🔐 Admin Alert Panel (Demo)</h3>
      <form>
        <select>
          <option>Missing Child</option>
          <option>Missing Woman</option>
        </select>
        <input type="file" />
        <input type="text" placeholder="Description" />
        <select>
          <option>High Urgency</option>
          <option>Medium</option>
        </select>
        <button type="button" onclick="triggerAlert()">Trigger Alert</button>
      </form>
    </section>

    <!-- =========================
         ALERT HISTORY
         ========================= -->
    <section class="card">
      <h3>📜 Alert History</h3>
      <ul>
        <li>12 Sept – Missing Child – <strong>Found Safe</strong></li>
        <li>10 Sept – Missing Woman – <strong>Under Investigation</strong></li>
      </ul>
    </section>

  </main>

  <footer>
    <p>Emergency: 112 | Childline: 1098</p>
    <p>Disclaimer: This is a demo system for awareness & safety.</p>
  </footer>

  <!-- =========================
       ALERT POPUP UI
       ========================= -->
  <div id="alertPopup">
    <div class="alert-box">
      <h2>🚨 EMERGENCY ALERT</h2>
      <p>Missing Child Reported Nearby</p>
      <button class="close-btn" id="closeAlert">Close Alert (10s)</button>
    </div>
  </div>

  <!-- =========================
       JAVASCRIPT LOGIC
       ========================= -->
  <script>
    const popup = document.getElementById('alertPopup');
    const closeBtn = document.getElementById('closeAlert');

    // Siren sound (simple beep placeholder)
    const siren = new Audio('https://actions.google.com/sounds/v1/alarms/alarm_clock.ogg');

    function triggerAlert() {
      popup.style.display = 'flex';
      siren.loop = true;
      siren.play();

      // Enable close after 10 seconds
      setTimeout(() => {
        closeBtn.style.pointerEvents = 'auto';
        closeBtn.style.opacity = '1';
        closeBtn.textContent = 'Close Alert';
      }, 10000);
    }

    closeBtn.onclick = () => {
      popup.style.display = 'none';
      siren.pause();
    };

    function toggleTipForm() {
      const form = document.getElementById('tipForm');
      form.style.display = form.style.display === 'none' ? 'block' : 'none';
    }

    function submitTip(e) {
      e.preventDefault();
      alert('Thank you. Your tip has been submitted to authorities.');
      e.target.reset();
    }

    function callEmergency() {
      window.location.href = 'tel:112';
    }

    // Auto trigger demo alert on page load
    window.onload = triggerAlert;
  </script>
</body>
</html>

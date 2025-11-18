<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Home Appliance Service</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg: #000000;
      --gold: #d1a766;
      --gold-soft: #e3c792;
      --text: #f7f2e7;
      --muted: #a48a63;
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      min-height: 100vh;
      background: radial-gradient(circle at top, #151515 0, #000 45%, #000 100%);
      color: var(--text);
      font-family: Inter, system-ui, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 24px 12px;
    }

    .card {
      width: 100%;
      max-width: 480px;
      background: #000;
      border-radius: 18px;
      border: 1px solid rgba(209,167,102,0.85);
      padding: 34px 24px 30px;
      text-align: center;
      box-shadow: 0 26px 70px rgba(0,0,0,0.9);
    }

    h1 {
      font-family: "Playfair Display", serif;
      font-size: 24px;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--gold-soft);
      margin-bottom: 22px;
    }

    .services {
      font-size: 13px;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--gold-soft);
      margin-bottom: 18px;
    }

    .rule-line {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 12px;
      margin-bottom: 22px;
      color: var(--gold-soft);
    }
    .rule-line span {
      flex: 1;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--gold-soft));
    }
    .rule-line span:last-child {
      background: linear-gradient(90deg, var(--gold-soft), transparent);
    }

    .phone {
      font-size: 18px;
      margin-bottom: 10px;
      color: var(--gold);
    }

    .email {
      font-size: 14px;
      color: var(--muted);
      margin-bottom: 30px;
    }

    .btn-main {
      padding: 13px 40px;
      border-radius: 999px;
      border: none;
      background: linear-gradient(135deg, #d6ad69, #b78645);
      color: #1b1308;
      font-size: 18px;
      cursor: pointer;
      box-shadow: 0 10px 30px rgba(0,0,0,0.7);
    }

    /* MODAL */
    .modal {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.75);
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      pointer-events: none;
      transition: .15s;
      z-index: 10;
    }
    .modal.show {
      opacity: 1;
      pointer-events: auto;
    }

    .modal-content {
      background: #050505;
      border: 1px solid rgba(209,167,102,0.75);
      border-radius: 18px;
      padding: 20px;
      width: 100%;
      max-width: 380px;
      box-shadow: 0 20px 60px rgba(0,0,0,0.9);
      position: relative;
    }

    .close-btn {
      position: absolute;
      top: 10px;
      right: 14px;
      background: none;
      border: none;
      font-size: 22px;
      color: var(--muted);
      cursor: pointer;
    }

    .modal-title {
      text-align: center;
      color: var(--gold-soft);
      font-family: "Playfair Display", serif;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      margin-bottom: 10px;
      font-size: 18px;
    }

    label {
      font-size: 13px;
      color: var(--muted);
      display: block;
      margin-bottom: 8px;
    }

    input[type="text"],
    input[type="tel"],
    input[type="date"],
    textarea {
      width: 100%;
      padding: 8px 12px;
      border-radius: 999px;
      border: 1px solid rgba(209,167,102,0.5);
      background: #000;
      color: var(--text);
      font-size: 14px;
      margin-top: 4px;
      outline: none;
    }

    textarea {
      border-radius: 14px;
      min-height: 70px;
      resize: vertical;
    }

    input:focus,
    textarea:focus {
      border-color: var(--gold);
    }

    .slots {
      margin: 10px 0 14px;
    }
    .slots label {
      display: flex;
      align-items: center;
      gap: 8px;
      color: var(--text);
      margin-bottom: 6px;
    }
    .slots input {
      width: auto;
      accent-color: var(--gold);
    }

    .btn-small {
      margin-top: 10px;
      padding: 10px 26px;
      background: linear-gradient(135deg, #d6ad69, #b78645);
      border-radius: 999px;
      border: none;
      font-size: 15px;
      cursor: pointer;
      width: 100%;
    }
  </style>
</head>

<body>

  <!-- ВИЗИТКА -->
  <div class="card">
    <h1>HOME APPLIANCE SERVICE</h1>

    <p class="services">
      Washers Dryers Ovens Refrigerators Dishwashers
    </p>

    <div class="rule-line">
      <span></span><div>✧</div><span></span>
    </div>

    <p class="phone">Call/Text (253) 213-1651</p>
    <p class="email">homeapplianceservice888@gmail.com</p>

    <button id="openSchedule" class="btn-main">Make Schedule</button>
  </div>

  <!-- МОДАЛЬНОЕ ОКНО -->
  <div id="calendarModal" class="modal">
    <div class="modal-content">
      <button class="close-btn" id="closeModal">&times;</button>
      <h2 class="modal-title">Schedule</h2>

      <form id="scheduleForm">
        <label>
          Name
          <input type="text" id="nameInput" required />
        </label>

        <label>
          Phone
          <input type="tel" id="phoneInput" required />
        </label>

        <label>
          Address
          <input type="text" id="addressInput" required />
        </label>

        <label>
          Date
          <input type="date" id="dateInput" required />
        </label>

        <div class="slots">
          <label><input type="radio" name="slot" value="8:00–12:00" required> 8:00 – 12:00</label>
          <label><input type="radio" name="slot" value="12:00–16:00"> 12:00 – 4:00 PM</label>
          <label><input type="radio" name="slot" value="16:00–20:00"> 4:00 – 8:00 PM</label>
        </div>

        <label>
          Problem description
          <textarea id="problemInput" placeholder="Noise, leak, not starting, not cooling, etc."></textarea>
        </label>

        <button class="btn-small" type="submit">Confirm</button>
      </form>
    </div>
  </div>

  <script>
    const openBtn  = document.getElementById("openSchedule");
    const modal    = document.getElementById("calendarModal");
    const closeBtn = document.getElementById("closeModal");
    const form     = document.getElementById("scheduleForm");
    const dateInput = document.getElementById("dateInput");

    // минимальная дата — сегодня
    dateInput.min = new Date().toISOString().split("T")[0];

    openBtn.addEventListener("click", () => modal.classList.add("show"));
    closeBtn.addEventListener("click", () => modal.classList.remove("show"));
    modal.addEventListener("click", e => {
      if (e.target === modal) modal.classList.remove("show");
    });

    form.addEventListener("submit", e => {
      e.preventDefault();

      const name    = document.getElementById("nameInput").value.trim();
      const phone   = document.getElementById("phoneInput").value.trim();
      const address = document.getElementById("addressInput").value.trim();
      const date    = document.getElementById("dateInput").value;
      const slotEl  = document.querySelector("input[name='slot']:checked");
      const problem = document.getElementById("problemInput").value.trim();

      if (!name || !phone || !address || !date || !slotEl) return;
      const slot = slotEl.value;

      const subject = encodeURIComponent(`Service Request — ${date} ${slot}`);
      const body = encodeURIComponent(
        `New schedule request:\n\n` +
        `Name: ${name}\n` +
        `Phone: ${phone}\n` +
        `Address: ${address}\n\n` +
        `Date: ${date}\n` +
        `Time window: ${slot}\n\n` +
        `Problem:\n${problem || "not specified"}\n\n` +
        `Thank you.`
      );

      window.location.href =
        `mailto:homeapplianceservice888@gmail.com?subject=${subject}&body=${body}`;

      modal.classList.remove("show");
    });
  </script>

</body>
</html>

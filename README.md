<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Filletia — Ikan Fillet Premium</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@400;500&display=swap" rel="stylesheet" />
  <style>
    :root {
      --orange: #FF6B35;
      --orange-light: #FF8C42;
      --orange-pale: #FFF0E8;
      --bg: #FAFAF8;
      --card: #FFFFFF;
      --text: #1A1A1A;
      --muted: #888880;
      --border: rgba(0,0,0,0.08);
      --radius-sm: 12px;
      --radius-md: 16px;
      --radius-lg: 24px;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: 'DM Sans', sans-serif;
      background: var(--bg);
      color: var(--text);
      min-height: 100vh;
    }

    /* ─── HERO ─────────────────────────── */
    .hero {
      background: var(--orange);
      padding: 3rem 1.5rem 2rem;
      position: relative;
      overflow: hidden;
    }
    .hero::before {
      content: "";
      position: absolute;
      width: 280px; height: 280px;
      background: rgba(255,255,255,0.07);
      border-radius: 50%;
      top: -80px; right: -60px;
    }
    .hero::after {
      content: "";
      position: absolute;
      width: 180px; height: 180px;
      background: rgba(255,255,255,0.05);
      border-radius: 50%;
      bottom: -60px; left: -40px;
    }
    .hero-tag {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: rgba(255,255,255,0.2);
      color: white;
      font-size: 11px;
      font-weight: 500;
      padding: 5px 12px;
      border-radius: 20px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-bottom: 14px;
    }
    .hero h1 {
      font-family: 'Syne', sans-serif;
      font-size: 52px;
      font-weight: 800;
      color: white;
      letter-spacing: -2px;
      line-height: 1;
      margin-bottom: 10px;
    }
    .hero p {
      color: rgba(255,255,255,0.82);
      font-size: 14px;
      max-width: 260px;
    }
    .hero-fish {
      position: absolute;
      right: 1.5rem;
      bottom: 1rem;
      font-size: 80px;
      opacity: 0.15;
      transform: scaleX(-1);
    }

    /* ─── LAYOUT ─────────────────────────── */
    .container { max-width: 480px; margin: 0 auto; padding: 0 1.25rem 3rem; }

    .section { margin-top: 2rem; }
    .section-label {
      font-size: 11px;
      font-weight: 500;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.1em;
      margin-bottom: 14px;
    }

    /* ─── PRODUCTS ─────────────────────────── */
    .product-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
    .product-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius-md);
      padding: 16px;
      cursor: pointer;
      transition: transform 0.2s, box-shadow 0.2s, border-color 0.2s;
    }
    .product-card:hover { transform: translateY(-3px); box-shadow: 0 8px 24px rgba(255,107,53,0.12); }
    .product-card.selected { border-color: var(--orange); background: var(--orange-pale); }
    .fish-icon { font-size: 32px; margin-bottom: 10px; display: block; }
    .product-name {
      font-family: 'Syne', sans-serif;
      font-size: 14px;
      font-weight: 700;
      color: var(--text);
      margin-bottom: 3px;
    }
    .product-price { font-size: 12px; color: var(--orange); font-weight: 500; }
    .spice-row { display: flex; gap: 6px; flex-wrap: wrap; margin-top: 10px; }
    .spice-pill {
      font-size: 10px;
      padding: 4px 9px;
      border-radius: 20px;
      border: 1px solid var(--border);
      background: transparent;
      color: var(--muted);
      cursor: pointer;
      transition: all 0.15s;
      white-space: nowrap;
      font-family: 'DM Sans', sans-serif;
    }
    .spice-pill:hover { border-color: var(--orange); color: var(--orange); }
    .spice-pill.active { background: var(--orange); border-color: var(--orange); color: white; }

    /* ─── AI CARD ─────────────────────────── */
    .ai-card {
      background: var(--text);
      border-radius: var(--radius-md);
      padding: 1.1rem 1.25rem;
      display: flex;
      align-items: center;
      gap: 14px;
    }
    .ai-dot {
      width: 36px; height: 36px;
      background: var(--orange);
      border-radius: 10px;
      display: flex; align-items: center; justify-content: center;
      font-size: 18px;
      flex-shrink: 0;
    }
    .ai-label { font-size: 10px; color: rgba(255,255,255,0.45); text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 3px; }
    .ai-text { font-size: 13px; color: white; }
    .ai-text span { color: var(--orange); font-weight: 500; }

    /* ─── CART ─────────────────────────── */
    .cart-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px 14px;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      margin-bottom: 8px;
      animation: slideIn 0.2s ease;
    }
    @keyframes slideIn { from { opacity: 0; transform: translateY(-6px); } to { opacity: 1; transform: none; } }
    .cart-name { font-size: 13px; font-weight: 500; color: var(--text); }
    .cart-meta { font-size: 11px; color: var(--muted); margin-top: 2px; }
    .cart-price { font-size: 13px; font-weight: 500; color: var(--orange); }
    .cart-empty {
      text-align: center; padding: 1.5rem 1rem;
      font-size: 13px; color: var(--muted);
      background: var(--card); border: 1px dashed var(--border); border-radius: var(--radius-md);
    }
    .cart-total {
      display: flex; justify-content: space-between; align-items: center;
      padding: 12px 14px;
      border-top: 1px solid var(--border);
      margin-top: 4px;
    }
    .cart-total-label { font-size: 12px; color: var(--muted); }
    .cart-total-value { font-family: 'Syne', sans-serif; font-size: 18px; font-weight: 700; color: var(--orange); }

    /* ─── BUTTONS ─────────────────────────── */
    .btn-row { display: flex; gap: 10px; }
    .btn-primary {
      flex: 1;
      background: var(--orange);
      color: white;
      border: none;
      border-radius: var(--radius-sm);
      padding: 14px;
      font-size: 14px;
      font-weight: 500;
      font-family: 'DM Sans', sans-serif;
      cursor: pointer;
      transition: opacity 0.15s, transform 0.1s;
    }
    .btn-primary:hover { opacity: 0.88; }
    .btn-primary:active { transform: scale(0.98); }
    .btn-outline {
      flex: 1;
      background: transparent;
      color: var(--orange);
      border: 1.5px solid var(--orange);
      border-radius: var(--radius-sm);
      padding: 14px;
      font-size: 14px;
      font-weight: 500;
      font-family: 'DM Sans', sans-serif;
      cursor: pointer;
      transition: background 0.15s;
    }
    .btn-outline:hover { background: var(--orange-pale); }

    /* ─── REVIEW ─────────────────────────── */
    .input-field {
      width: 100%;
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 12px 14px;
      font-size: 13px;
      font-family: 'DM Sans', sans-serif;
      background: var(--card);
      color: var(--text);
      margin-bottom: 10px;
      outline: none;
      transition: border-color 0.15s;
      display: block;
    }
    .input-field:focus { border-color: var(--orange); }
    textarea.input-field { resize: none; min-height: 88px; }

    .star-row { display: flex; gap: 6px; margin-bottom: 12px; }
    .star { font-size: 24px; cursor: pointer; opacity: 0.25; transition: opacity 0.1s, transform 0.1s; color: var(--orange); }
    .star.lit { opacity: 1; }
    .star:hover { transform: scale(1.2); }

    .review-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 12px 14px;
      margin-top: 10px;
      animation: slideIn 0.2s ease;
    }
    .review-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px; }
    .review-name { font-size: 12px; font-weight: 500; color: var(--orange); }
    .review-stars { font-size: 12px; color: var(--orange); }
    .review-text { font-size: 13px; color: var(--text); line-height: 1.5; }

    /* ─── TOAST ─────────────────────────── */
    .toast {
      position: fixed;
      bottom: 28px; left: 50%;
      transform: translateX(-50%) translateY(40px);
      background: var(--text);
      color: white;
      font-size: 13px;
      font-family: 'DM Sans', sans-serif;
      padding: 11px 22px;
      border-radius: 30px;
      opacity: 0;
      transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
      pointer-events: none;
      white-space: nowrap;
      z-index: 999;
    }
    .toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }
  </style>
</head>
<body>

  <!-- HERO -->
  <div class="hero">
    <div class="hero-tag">✦ fresh daily</div>
    <h1>Filletia</h1>
    <p>Ikan fillet premium + bumbu rempah hits ✨</p>
    <div class="hero-fish">🐟</div>
  </div>

  <div class="container">

    <!-- PRODUCTS -->
    <div class="section">
      <p class="section-label">Pilih produkmu</p>
      <div class="product-grid" id="product-grid"></div>
    </div>

    <!-- AI RECOMMENDATION -->
    <div class="section">
      <div class="ai-card">
        <div class="ai-dot">✦</div>
        <div>
          <div class="ai-label">AI Pick</div>
          <div class="ai-text" id="ai-text">Pilih produk dulu yuk~ ✦</div>
        </div>
      </div>
    </div>

    <!-- CART -->
    <div class="section">
      <p class="section-label">Keranjang</p>
      <div id="cart-list"></div>
    </div>

    <!-- ORDER BUTTONS -->
    <div class="section">
      <div class="btn-row">
        <button class="btn-primary" onclick="showToast('Delivery order disiapkan! 🛵')">Delivery Order</button>
        <button class="btn-outline" onclick="showToast('Pre-order berhasil dicatat! 📝')">Pre Order</button>
      </div>
    </div>

    <!-- REVIEW -->
    <div class="section">
      <p class="section-label">Kasih review dong</p>
      <div class="star-row" id="star-row">
        <span class="star" data-i="1">★</span>
        <span class="star" data-i="2">★</span>
        <span class="star" data-i="3">★</span>
        <span class="star" data-i="4">★</span>
        <span class="star" data-i="5">★</span>
      </div>
      <input class="input-field" id="rev-name" placeholder="Nama kamu siapa?" />
      <textarea class="input-field" id="rev-text" placeholder="Gimana pengalamannya? ✍️"></textarea>
      <button class="btn-primary" onclick="submitReview()">Kirim Review 🚀</button>
      <div id="review-list"></div>
    </div>

  </div>

  <div class="toast" id="toast"></div>

  <script>
    const products = [
      { id: 1, name: "Fillet Nila",    price: 25000, icon: "🐟" },
      { id: 2, name: "Fillet Gurame",  price: 35000, icon: "🐠" },
      { id: 3, name: "Fillet Kembung", price: 20000, icon: "🐡" },
      { id: 4, name: "Fillet Kakap",   price: 40000, icon: "🦈" },
    ];
    const spices = ["Bumbu Bakar", "Bumbu Kuah Kuning", "Bumbu Marinasi", "Bumbu Pepes"];
    const cart = [];
    let starRating = 0;

    function formatPrice(p) { return "Rp " + p.toLocaleString("id-ID"); }

    function renderProducts() {
      document.getElementById("product-grid").innerHTML = products.map(p => `
        <div class="product-card" id="pcard-${p.id}">
          <span class="fish-icon">${p.icon}</span>
          <div class="product-name">${p.name}</div>
          <div class="product-price">${formatPrice(p.price)}</div>
          <div class="spice-row">
            ${spices.map(s => `<span class="spice-pill" onclick="selectSpice(${p.id},'${s}',this)">${s}</span>`).join("")}
          </div>
        </div>
      `).join("");
    }

    function selectSpice(pid, spice, el) {
      const card = document.getElementById("pcard-" + pid);
      card.querySelectorAll(".spice-pill").forEach(p => p.classList.remove("active"));
      el.classList.add("active");
      card.classList.add("selected");
      const product = products.find(p => p.id === pid);
      cart.push({ ...product, spice });
      renderCart();
      updateAI();
      showToast(product.name + " + " + spice + " masuk keranjang! 🎉");
    }

    function renderCart() {
      const list = document.getElementById("cart-list");
      if (cart.length === 0) {
        list.innerHTML = '<div class="cart-empty">Keranjang masih kosong bestie 🛒</div>';
        return;
      }
      const total = cart.reduce((s, i) => s + i.price, 0);
      list.innerHTML = cart.map(i => `
        <div class="cart-item">
          <div>
            <div class="cart-name">${i.icon} ${i.name}</div>
            <div class="cart-meta">${i.spice}</div>
          </div>
          <div class="cart-price">${formatPrice(i.price)}</div>
        </div>
      `).join("") + `
        <div class="cart-total">
          <div class="cart-total-label">Total</div>
          <div class="cart-total-value">${formatPrice(total)}</div>
        </div>
      `;
    }

    function updateAI() {
      const el = document.getElementById("ai-text");
      if (cart.length === 0) { el.innerHTML = "Pilih produk dulu yuk~ ✦"; return; }
      const count = {};
      cart.forEach(i => { count[i.spice] = (count[i.spice] || 0) + 1; });
      const top = Object.keys(count).reduce((a, b) => count[a] > count[b] ? a : b);
      el.innerHTML = `Kamu suka banget sama <span>${top}</span> nih! Recommended fr 🔥`;
    }

    document.getElementById("star-row").addEventListener("click", e => {
      if (!e.target.classList.contains("star")) return;
      starRating = parseInt(e.target.dataset.i);
      document.querySelectorAll(".star").forEach(s => {
        s.classList.toggle("lit", parseInt(s.dataset.i) <= starRating);
      });
    });

    function submitReview() {
      const name = document.getElementById("rev-name").value.trim();
      const text = document.getElementById("rev-text").value.trim();
      if (!name || !text) { showToast("Isi dulu nama & reviewnya ya! 🙏"); return; }
      const stars = "★".repeat(starRating) + "☆".repeat(5 - starRating);
      const card = document.createElement("div");
      card.className = "review-card";
      card.innerHTML = `
        <div class="review-header">
          <div class="review-name">${name}</div>
          <div class="review-stars">${stars}</div>
        </div>
        <div class="review-text">${text}</div>
      `;
      document.getElementById("review-list").prepend(card);
      document.getElementById("rev-name").value = "";
      document.getElementById("rev-text").value = "";
      starRating = 0;
      document.querySelectorAll(".star").forEach(s => s.classList.remove("lit"));
      showToast("Review terkirim, makasih bestie! 💖");
    }

    function showToast(msg) {
      const t = document.getElementById("toast");
      t.textContent = msg;
      t.classList.add("show");
      setTimeout(() => t.classList.remove("show"), 2500);
    }

    renderCart();
    renderProducts();
  </script>
</body>
</html>

<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Ma Boutique</title>
  <meta name="description" content="Boutique en ligne - produits, panier, commande" />
  <style>
    :root{
      --bg:#0b0c10; --card:#11131a; --muted:#9aa3b2; --text:#eef2ff;
      --accent:#7c5cff; --accent2:#22c55e; --danger:#ef4444; --border:#212433;
      --shadow: 0 12px 40px rgba(0,0,0,.35);
      --radius:18px;
    }
    *{box-sizing:border-box}
    body{margin:0;font-family:ui-sans-serif,system-ui,-apple-system,Segoe UI,Roboto,Arial;
      background: radial-gradient(900px 600px at 15% 10%, rgba(124,92,255,.25), transparent 60%),
                  radial-gradient(900px 600px at 85% 30%, rgba(34,197,94,.14), transparent 60%),
                  var(--bg);
      color:var(--text);
    }
    a{color:inherit;text-decoration:none}
    .wrap{max-width:1120px;margin:0 auto;padding:18px}
    header{
      position:sticky;top:0;z-index:50;
      backdrop-filter: blur(10px);
      background: rgba(11,12,16,.65);
      border-bottom:1px solid rgba(255,255,255,.06);
    }
    .topbar{display:flex;align-items:center;gap:12px;justify-content:space-between}
    .brand{display:flex;align-items:center;gap:10px}
    .logo{
      width:40px;height:40px;border-radius:12px;
      background: linear-gradient(135deg,var(--accent), #ff4fd8);
      box-shadow: 0 12px 30px rgba(124,92,255,.35);
    }
    .brand h1{font-size:16px;margin:0;letter-spacing:.2px}
    .brand small{display:block;color:var(--muted);font-size:12px;margin-top:2px}
    .actions{display:flex;align-items:center;gap:10px;flex-wrap:wrap;justify-content:flex-end}
    .pill{
      display:flex;align-items:center;gap:8px;
      padding:10px 12px;border-radius:999px;background:rgba(255,255,255,.04);
      border:1px solid rgba(255,255,255,.06);
    }
    input, select, textarea{
      width:100%;padding:12px 12px;border-radius:12px;
      border:1px solid rgba(255,255,255,.10);
      background: rgba(255,255,255,.04);
      color:var(--text); outline:none;
    }
    input::placeholder, textarea::placeholder{color:#7b8292}
    .search{min-width:260px}
    .btn{
      border:0;cursor:pointer;color:var(--text);
      background: linear-gradient(135deg,var(--accent), #ff4fd8);
      padding:12px 14px;border-radius:14px;font-weight:700;
      box-shadow: 0 14px 34px rgba(124,92,255,.22);
      transition: transform .08s ease;
      white-space:nowrap;
    }
    .btn:active{transform: scale(.98)}
    .btn.secondary{
      background: rgba(255,255,255,.06);
      border:1px solid rgba(255,255,255,.12);
      box-shadow:none;
      font-weight:650;
    }
    .btn.green{
      background: linear-gradient(135deg, var(--accent2), #16a34a);
    }
    .btn.danger{
      background: rgba(239,68,68,.15);
      border: 1px solid rgba(239,68,68,.35);
      box-shadow:none;
    }
    main{padding:18px 0 40px}
    .hero{
      display:grid;grid-template-columns: 1.15fr .85fr;
      gap:18px;align-items:stretch;
    }
    .panel{
      background: rgba(255,255,255,.03);
      border:1px solid rgba(255,255,255,.07);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding:18px;
    }
    .hero h2{margin:0 0 8px;font-size:26px}
    .hero p{margin:0;color:var(--muted);line-height:1.45}
    .badges{display:flex;gap:10px;flex-wrap:wrap;margin-top:14px}
    .badge{
      padding:8px 10px;border-radius:999px;
      border:1px solid rgba(255,255,255,.08);
      background: rgba(255,255,255,.03);
      color: #cbd5e1;
      font-size:12px;
    }
    .grid{
      margin-top:18px;
      display:grid;grid-template-columns: repeat(3, 1fr);
      gap:14px;
    }
    @media (max-width: 980px){ .grid{grid-template-columns: repeat(2, 1fr)} .hero{grid-template-columns:1fr} .search{min-width:180px}}
    @media (max-width: 560px){ .grid{grid-template-columns: 1fr} .actions{gap:8px} }
    .card{
      background: rgba(255,255,255,.03);
      border:1px solid rgba(255,255,255,.07);
      border-radius: var(--radius);
      overflow:hidden;
      box-shadow: var(--shadow);
      display:flex;flex-direction:column;
      min-height: 340px;
    }
    .thumb{
      height:170px;
      background:#0f1118;
      position:relative;
      display:flex;align-items:center;justify-content:center;
      border-bottom:1px solid rgba(255,255,255,.07);
    }
    .thumb img{width:100%;height:100%;object-fit:cover;display:block;filter:saturate(1.05)}
    .tag{
      position:absolute;left:12px;top:12px;
      padding:8px 10px;border-radius:999px;
      background: rgba(0,0,0,.45);
      border:1px solid rgba(255,255,255,.10);
      font-size:12px;color:#e5e7eb;
      backdrop-filter: blur(6px);
    }
    .content{padding:14px 14px 16px;display:flex;flex-direction:column;gap:10px;flex:1}
    .title{display:flex;align-items:flex-start;justify-content:space-between;gap:10px}
    .title h3{margin:0;font-size:16px;line-height:1.25}
    .price{font-weight:800}
    .desc{color:var(--muted);font-size:13px;line-height:1.4;flex:1}
    .row{display:flex;gap:10px;align-items:center;justify-content:space-between}
    .qty{display:flex;gap:6px;align-items:center}
    .mini{
      padding:8px 10px;border-radius:12px;background: rgba(255,255,255,.05);
      border:1px solid rgba(255,255,255,.10);cursor:pointer;
      user-select:none;
    }
    .mini:active{transform:scale(.98)}
    .foot{
      display:flex;gap:10px;align-items:center;justify-content:space-between;
      border-top:1px solid rgba(255,255,255,.07);
      padding-top:10px;
    }
    .muted{color:var(--muted)}
    .kpi{display:flex;gap:12px;flex-wrap:wrap;margin-top:10px}
    .kpi .box{
      flex:1;min-width:160px;
      background: rgba(255,255,255,.03);
      border:1px solid rgba(255,255,255,.07);
      border-radius: 16px;
      padding:12px;
    }
    .box b{display:block;font-size:18px}
    .box small{color:var(--muted)}
    /* Drawer panier */
    .drawerBack{
      position:fixed;inset:0;background: rgba(0,0,0,.55);
      display:none;align-items:stretch;justify-content:flex-end;z-index:100;
    }
    .drawer{
      width:min(440px, 92vw);
      background: #0f1118;
      border-left:1px solid rgba(255,255,255,.08);
      padding:16px;
      display:flex;flex-direction:column;gap:12px;
    }
    .drawer h3{margin:0;font-size:16px}
    .drawerTop{display:flex;align-items:center;justify-content:space-between;gap:10px}
    .x{cursor:pointer;padding:10px 12px;border-radius:14px;background: rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.10)}
    .cartList{display:flex;flex-direction:column;gap:10px;overflow:auto;max-height:46vh;padding-right:4px}
    .cartItem{
      display:grid;grid-template-columns: 62px 1fr auto;
      gap:10px;align-items:center;
      padding:10px;border-radius:16px;background: rgba(255,255,255,.03);
      border:1px solid rgba(255,255,255,.07);
    }
    .cartItem img{width:62px;height:62px;border-radius:14px;object-fit:cover;border:1px solid rgba(255,255,255,.08)}
    .cartItem h4{margin:0;font-size:13px}
    .cartItem small{color:var(--muted)}
    .cartItem .right{display:flex;flex-direction:column;gap:8px;align-items:flex-end}
    .line{height:1px;background: rgba(255,255,255,.08);margin:4px 0}
    .two{display:grid;grid-template-columns: 1fr 1fr;gap:10px}
    .totals{display:flex;flex-direction:column;gap:8px}
    .totals .r{display:flex;align-items:center;justify-content:space-between}
    .notice{font-size:12px;color:var(--muted);line-height:1.35}
    footer{padding:28px 0 40px;color:var(--muted);font-size:12px}
    .link{color:#c7d2fe;text-decoration:underline;text-underline-offset:3px}
    .toast{
      position:fixed;left:50%;bottom:18px;transform:translateX(-50%);
      padding:12px 14px;border-radius:14px;
      background: rgba(17,19,26,.9);
      border:1px solid rgba(255,255,255,.12);
      box-shadow: var(--shadow);
      display:none;z-index:200;
      max-width:min(560px, 92vw);
    }
    .tag2{
      padding:6px 9px;border-radius:999px;
      background: rgba(34,197,94,.14);
      border:1px solid rgba(34,197,94,.28);
      color:#bbf7d0;font-size:12px;
    }
  </style>
</head>
<body>
<header>
  <div class="wrap">
    <div class="topbar">
      <div class="brand">
        <div class="logo" aria-hidden="true"></div>
        <div>
          <h1 id="shopName">Ma Boutique</h1>
          <small id="shopTagline">Vente en ligne • Livraison / remise en main propre</small>
        </div>
      </div>

      <div class="actions">
        <div class="pill">
          <span class="muted">Catégorie</span>
          <select id="cat"></select>
        </div>
        <input id="q" class="search" placeholder="Rechercher un produit…" />
        <button class="btn secondary" id="openCartBtn">🛒 Panier <span id="cartCount">0</span></button>
      </div>
    </div>
  </div>
</header>

<main class="wrap">
  <section class="hero">
    <div class="panel">
      <h2 id="heroTitle">Nouveautés & best-sellers</h2>
      <p id="heroText">Choisis tes produits, ajoute au panier, puis remplis le formulaire de commande. Paiement : remise en main propre, virement ou paiement à la livraison (à personnaliser).</p>
      <div class="badges">
        <span class="badge">✅ Panier + code promo</span>
        <span class="badge">✅ Formulaire de commande</span>
        <span class="badge">✅ Mobile friendly</span>
        <span class="badge">⚡ 1 fichier (facile à publier)</span>
      </div>

      <div class="kpi">
        <div class="box">
          <b id="kpiProducts">0</b>
          <small>Produits disponibles</small>
        </div>
        <div class="box">
          <b id="kpiDelivery">48h</b>
          <small>Délai estimé (modifiable)</small>
        </div>
        <div class="box">
          <b id="kpiSupport">DM Insta</b>
          <small>Support client (modifiable)</small>
        </div>
      </div>
    </div>

    <div class="panel">
      <h3 style="margin:0 0 10px">Infos boutique</h3>
      <div class="two">
        <div>
          <label class="muted">Livraison</label>
          <select id="shippingMode">
            <option value="pickup">Remise en main propre</option>
            <option value="delivery">Livraison locale</option>
            <option value="ship">Envoi (Colissimo/…)</option>
          </select>
        </div>
        <div>
          <label class="muted">Devise</label>
          <select id="currency">
            <option value="EUR">EUR (€)</option>
            <option value="USD">USD ($)</option>
            <option value="GBP">GBP (£)</option>
          </select>
        </div>
      </div>
      <div style="margin-top:10px">
        <label class="muted">Code promo</label>
        <input id="promoInput" placeholder="Ex: WEN10" />
        <div style="display:flex;gap:10px;margin-top:10px;flex-wrap:wrap">
          <button class="btn secondary" id="applyPromo">Appliquer</button>
          <button class="btn secondary" id="clearPromo">Retirer</button>
        </div>
      </div>

      <div class="line"></div>
      <div class="notice">
        Astuce : tu peux publier ce site gratuitement sur Netlify / GitHub Pages.
        Pour le paiement en ligne, tu pourras ajouter Stripe plus tard.
      </div>
    </div>
  </section>

  <section>
    <div style="display:flex;align-items:center;justify-content:space-between;gap:10px;margin-top:18px;flex-wrap:wrap">
      <h3 style="margin:0">Catalogue</h3>
      <div class="pill">
        <span class="muted">Tri</span>
        <select id="sort">
          <option value="popular">Populaires</option>
          <option value="priceAsc">Prix croissant</option>
          <option value="priceDesc">Prix décroissant</option>
          <option value="new">Nouveautés</option>
        </select>
      </div>
    </div>

    <div id="grid" class="grid"></div>
  </section>
</main>

<!-- Drawer Panier -->
<div id="drawerBack" class="drawerBack" role="dialog" aria-modal="true" aria-label="Panier">
  <div class="drawer">
    <div class="drawerTop">
      <h3>🛒 Ton panier</h3>
      <div class="x" id="closeCartBtn">Fermer ✕</div>
    </div>

    <div id="cartList" class="cartList"></div>

    <div class="panel" style="padding:12px;margin:0">
      <div class="totals">
        <div class="r"><span class="muted">Sous-total</span><b id="subTotal">0€</b></div>
        <div class="r"><span class="muted">Réduction</span><b id="discount">-0€</b></div>
        <div class="r"><span class="muted">Livraison</span><b id="shipping">0€</b></div>
        <div class="line"></div>
        <div class="r" style="font-size:16px"><span>Total</span><b id="total">0€</b></div>
      </div>
      <div style="display:flex;gap:10px;margin-top:12px;flex-wrap:wrap">
        <button class="btn danger" id="clearCartBtn">Vider</button>
        <button class="btn green" id="checkoutBtn">Commander</button>
      </div>
      <div class="notice" style="margin-top:10px">
        Le bouton “Commander” ouvre un formulaire. Tu peux ensuite confirmer par DM / email.
      </div>
    </div>

    <div id="checkoutPanel" class="panel" style="padding:12px;margin:0;display:none">
      <h3 style="margin:0 0 10px">✅ Formulaire de commande</h3>
      <div class="two">
        <div>
          <label class="muted">Prénom</label>
          <input id="firstName" placeholder="Ex: Sami" />
        </div>
        <div>
          <label class="muted">Nom</label>
          <input id="lastName" placeholder="Ex: Durand" />
        </div>
      </div>
      <div style="margin-top:10px">
        <label class="muted">Email ou Instagram</label>
        <input id="contact" placeholder="Ex: @moninsta ou mail@exemple.com" />
      </div>
      <div style="margin-top:10px">
        <label class="muted">Adresse / point de rendez-vous</label>
        <textarea id="address" rows="3" placeholder="Ex: Métro … / Adresse si livraison"></textarea>
      </div>
      <div class="two" style="margin-top:10px">
        <div>
          <label class="muted">Mode de paiement (à confirmer)</label>
          <select id="payMode">
            <option>Remise en main propre</option>
            <option>Virement</option>
            <option>Paiement à la livraison</option>
          </select>
        </div>
        <div>
          <label class="muted">Note (optionnel)</label>
          <input id="note" placeholder="Ex: couleur, taille…" />
        </div>
      </div>

      <div style="display:flex;gap:10px;margin-top:12px;flex-wrap:wrap">
        <button class="btn secondary" id="backToCart">Retour panier</button>
        <button class="btn" id="sendOrder">Envoyer la commande</button>
      </div>
      <div class="notice" style="margin-top:10px">
        ⚠️ Ici, l’envoi est “simulé” (ça génère un résumé à copier-coller). Pour automatiser : Netlify Forms / Formspree / Google Forms.
      </div>
      <div id="orderResult" style="margin-top:10px;display:none">
        <div class="line"></div>
        <div class="tag2">Commande prête</div>
        <textarea id="orderText" rows="10" style="margin-top:10px"></textarea>
        <div style="display:flex;gap:10px;margin-top:10px;flex-wrap:wrap">
          <button class="btn secondary" id="copyOrder">Copier</button>
          <button class="btn secondary" id="closeAll">Fermer</button>
        </div>
      </div>
    </div>

    <footer>
      <div>© <span id="year"></span> <span id="footShop">Ma Boutique</span> • <span class="muted">Mentions légales & CGV à ajouter si tu vends régulièrement.</span></div>
    </footer>
  </div>
</div>

<div id="toast" class="toast"></div>

<script>
  /***********************
   * 1) CONFIG BOUTIQUE
   ***********************/
  const SHOP = {
    name: "Ma Boutique",
    tagline: "Vente en ligne • Livraison / remise en main propre",
    heroTitle: "Nouveautés & best-sellers",
    heroText: "Choisis tes produits, ajoute au panier, puis remplis le formulaire de commande. Paiement : remise en main propre, virement ou paiement à la livraison (à personnaliser).",
    support: "DM Insta",
    delivery: "48h",
  };

  // Codes promo : -10% etc
  const PROMOS = {
    "WEN10": { type: "percent", value: 10 },
    "BIENVENUE5": { type: "fixed", value: 5 }
  };

  // Frais de livraison (à adapter)
  const SHIPPING_FEES = {
    pickup: 0,
    delivery: 4.90,
    ship: 6.90
  };

  // Produits (modifie ici)
  const PRODUCTS = [
    {
      id: "p1",
      name: "T-shirt Oversize",
      price: 19.90,
      category: "Vêtements",
      popular: 9,
      isNew: true,
      stockNote: "Tailles S à XL",
      image: "https://images.unsplash.com/photo-1520975958225-726d6a5a1f82?auto=format&fit=crop&w=1200&q=70",
      desc: "Coupe oversize, tissu confortable. Parfait pour un style simple et propre."
    },
    {
      id: "p2",
      name: "Hoodie Premium",
      price: 34.90,
      category: "Vêtements",
      popular: 10,
      isNew: false,
      stockNote: "Noir / Gris",
      image: "https://images.unsplash.com/photo-1520975682038-77a3f7be3c11?auto=format&fit=crop&w=1200&q=70",
      desc: "Hoodie épais, look premium. Idéal pour l'hiver."
    },
    {
      id: "p3",
      name: "Coque téléphone",
      price: 12.90,
      category: "Accessoires",
      popular: 7,
      isNew: true,
      stockNote: "iPhone & Samsung",
      image: "https://images.unsplash.com/photo-1580913428735-bd3c269d6a82?auto=format&fit=crop&w=1200&q=70",
      desc: "Coque résistante, design minimal."
    },
    {
      id: "p4",
      name: "Bracelet",
      price: 9.90,
      category: "Accessoires",
      popular: 6,
      isNew: false,
      stockNote: "Réglable",
      image: "https://images.unsplash.com/photo-1522312346375-d1a52e2b99b3?auto=format&fit=crop&w=1200&q=70",
      desc: "Bracelet discret, parfait en cadeau."
    },
    {
      id: "p5",
      name: "Pack stickers",
      price: 4.90,
      category: "Stickers",
      popular: 8,
      isNew: false,
      stockNote: "10 stickers",
      image: "https://images.unsplash.com/photo-1526498460520-4c246339dccb?auto=format&fit=crop&w=1200&q=70",
      desc: "Stickers résistants pour ordi / téléphone."
    },
    {
      id: "p6",
      name: "Casquette",
      price: 14.90,
      category: "Accessoires",
      popular: 5,
      isNew: false,
      stockNote: "Taille unique",
      image: "https://images.unsplash.com/photo-1520975682038-68a8d3f8b80d?auto=format&fit=crop&w=1200&q=70",
      desc: "Casquette classique, look street."
    }
  ];

  /***********************
   * 2) STATE
   ***********************/
  const state = {
    q: "",
    category: "Toutes",
    sort: "popular",
    shippingMode: "pickup",
    currency: "EUR",
    promoCode: load("promo") || "",
    cart: load("cart") || {} // { productId: qty }
  };

  /***********************
   * 3) HELPERS
   ***********************/
  function save(key, value){ localStorage.setItem(key, JSON.stringify(value)); }
  function load(key){ try { return JSON.parse(localStorage.getItem(key)); } catch { return null; } }

  function money(amount){
    const cur = state.currency;
    const sym = cur === "EUR" ? "€" : cur === "USD" ? "$" : "£";
    // simple affichage (pas de conversion)
    return `${amount.toFixed(2)}${sym}`;
  }

  function toast(msg){
    const t = document.getElementById("toast");
    t.textContent = msg;
    t.style.display = "block";
    clearTimeout(window.__toast);
    window.__toast = setTimeout(()=> t.style.display="none", 2100);
  }

  function getProduct(id){ return PRODUCTS.find(p=>p.id===id); }

  function cartCount(){
    return Object.values(state.cart).reduce((a,b)=>a+b,0);
  }

  function subTotal(){
    let sum = 0;
    for(const [id,qty] of Object.entries(state.cart)){
      const p = getProduct(id);
      if(p) sum += p.price * qty;
    }
    return sum;
  }

  function promoDiscount(sub){
    const code = (state.promoCode || "").trim().toUpperCase();
    if(!code || !PROMOS[code]) return 0;
    const promo = PROMOS[code];
    if(promo.type === "percent") return sub * (promo.value/100);
    if(promo.type === "fixed") return Math.min(sub, promo.value);
    return 0;
  }

  function shippingFee(){
    return SHIPPING_FEES[state.shippingMode] ?? 0;
  }

  function total(){
    const sub = subTotal();
    const disc = promoDiscount(sub);
    return Math.max(0, sub - disc) + shippingFee();
  }

  function setQty(id, qty){
    qty = Math.max(0, Math.min(99, qty));
    if(qty === 0) delete state.cart[id];
    else state.cart[id] = qty;
    save("cart", state.cart);
    renderCart();
    renderBadges();
  }

  function addToCart(id, qty=1){
    const cur = state.cart[id] || 0;
    setQty(id, cur + qty);
    toast("Ajouté au panier ✅");
  }

  /***********************
   * 4) RENDER
   ***********************/
  function renderHeader(){
    document.getElementById("shopName").textContent = SHOP.name;
    document.getElementById("shopTagline").textContent = SHOP.tagline;
    document.getElementById("heroTitle").textContent = SHOP.heroTitle;
    document.getElementById("heroText").textContent = SHOP.heroText;
    document.getElementById("kpiDelivery").textContent = SHOP.delivery;
    document.getElementById("kpiSupport").textContent = SHOP.support;
    document.getElementById("footShop").textContent = SHOP.name;
    document.getElementById("year").textContent = new Date().getFullYear();
  }

  function renderFilters(){
    // categories
    const cats = ["Toutes", ...Array.from(new Set(PRODUCTS.map(p=>p.category)))];
    const catSel = document.getElementById("cat");
    catSel.innerHTML = cats.map(c=>`<option ${c===state.category?"selected":""}>${c}</option>`).join("");

    // promo input
    document.getElementById("promoInput").value = state.promoCode || "";

    document.getElementById("shippingMode").value = state.shippingMode;
    document.getElementById("currency").value = state.currency;
    document.getElementById("sort").value = state.sort;
    document.getElementById("q").value = state.q;

    document.getElementById("kpiProducts").textContent = PRODUCTS.length;
  }

  function filteredProducts(){
    let list = [...PRODUCTS];

    if(state.category !== "Toutes"){
      list = list.filter(p=>p.category === state.category);
    }
    if(state.q.trim()){
      const qq = state.q.trim().toLowerCase();
      list = list.filter(p =>
        p.name.toLowerCase().includes(qq) ||
        p.desc.toLowerCase().includes(qq) ||
        p.category.toLowerCase().includes(qq)
      );
    }

    switch(state.sort){
      case "priceAsc": list.sort((a,b)=>a.price-b.price); break;
      case "priceDesc": list.sort((a,b)=>b.price-a.price); break;
      case "new": list.sort((a,b)=>(b.isNew?1:0)-(a.isNew?1:0) || b.popular-a.popular); break;
      default: list.sort((a,b)=>b.popular-a.popular); // popular
    }
    return list;
  }

  function renderGrid(){
    const grid = document.getElementById("grid");
    const list = filteredProducts();

    if(list.length === 0){
      grid.innerHTML = `<div class="panel" style="grid-column:1/-1">
        Aucun produit trouvé. Essaie un autre mot-clé.
      </div>`;
      return;
    }

    grid.innerHTML = list.map(p => `
      <article class="card">
        <div class="thumb">
          <img src="${p.image}" alt="${escapeHtml(p.name)}">
          <div class="tag">${p.category}${p.isNew ? " • Nouveau" : ""}</div>
        </div>
        <div class="content">
          <div class="title">
            <h3>${escapeHtml(p.name)}</h3>
            <div class="price">${money(p.price)}</div>
          </div>
          <div class="desc">${escapeHtml(p.desc)}</div>
          <div class="row">
            <div class="muted" style="font-size:12px">${escapeHtml(p.stockNote || "")}</div>
            <div class="qty">
              <div class="mini" onclick="window.__dec('${p.id}')">−</div>
              <div class="mini" style="min-width:42px;text-align:center" id="qty-${p.id}">${state.cart[p.id]||0}</div>
              <div class="mini" onclick="window.__inc('${p.id}')">+</div>
            </div>
          </div>
          <div class="foot">
            <button class="btn secondary" onclick="window.__add('${p.id}')">Ajouter</button>
            <button class="btn" onclick="window.__buy('${p.id}')">Acheter</button>
          </div>
        </div>
      </article>
    `).join("");

    // update qty displays
    for(const p of list){
      const el = document.getElementById(`qty-${p.id}`);
      if(el) el.textContent = state.cart[p.id] || 0;
    }
  }

  function renderBadges(){
    document.getElementById("cartCount").textContent = cartCount();
  }

  function renderCart(){
    const listEl = document.getElementById("cartList");
    const entries = Object.entries(state.cart);

    if(entries.length === 0){
      listEl.innerHTML = `<div class="panel" style="margin:0;padding:12px">
        Ton panier est vide. Ajoute un produit 🙂
      </div>`;
    } else {
      listEl.innerHTML = entries.map(([id,qty])=>{
        const p = getProduct(id);
        if(!p) return "";
        return `
          <div class="cartItem">
            <img src="${p.image}" alt="${escapeHtml(p.name)}" />
            <div>
              <h4>${escapeHtml(p.name)}</h4>
              <small>${money(p.price)} • ${escapeHtml(p.category)}</small>
              <div class="muted" style="font-size:12px;margin-top:6px">${escapeHtml(p.stockNote||"")}</div>
            </div>
            <div class="right">
              <b>${money(p.price * qty)}</b>
              <div class="qty">
                <div class="mini" onclick="window.__set('${id}', ${qty-1})">−</div>
                <div class="mini" style="min-width:36px;text-align:center">${qty}</div>
                <div class="mini" onclick="window.__set('${id}', ${qty+1})">+</div>
              </div>
              <div class="mini" onclick="window.__set('${id}', 0)" title="Retirer">Suppr</div>
            </div>
          </div>
        `;
      }).join("");
    }

    const sub = subTotal();
    const disc = promoDiscount(sub);
    document.getElementById("subTotal").textContent = money(sub);
    document.getElementById("discount").textContent = `-${money(disc)}`;
    document.getElementById("shipping").textContent = money(shippingFee());
    document.getElementById("total").textContent = money(total());

    // sync checkout visibility
    const hasItems = entries.length > 0;
    document.getElementById("checkoutBtn").disabled = !hasItems;
  }

  function escapeHtml(str){
    return String(str).replace(/[&<>"']/g, s=>({ "&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#039;" }[s]));
  }

  /***********************
   * 5) UI ACTIONS
   ***********************/
  function openCart(){
    document.getElementById("drawerBack").style.display = "flex";
    document.getElementById("checkoutPanel").style.display = "none";
    renderCart();
  }
  function closeCart(){
    document.getElementById("drawerBack").style.display = "none";
  }

  function applyPromo(){
    const code = (document.getElementById("promoInput").value || "").trim().toUpperCase();
    if(!code){
      state.promoCode = "";
      save("promo", state.promoCode);
      toast("Code promo retiré");
      renderCart(); return;
    }
    if(!PROMOS[code]){
      toast("Code promo invalide ❌");
      return;
    }
    state.promoCode = code;
    save("promo", state.promoCode);
    toast("Code promo appliqué ✅");
    renderCart();
  }

  function clearPromo(){
    state.promoCode = "";
    save("promo", state.promoCode);
    document.getElementById("promoInput").value = "";
    toast("Code promo retiré");
    renderCart();
  }

  function startCheckout(){
    if(cartCount() === 0) return;
    document.getElementById("checkoutPanel").style.display = "block";
    // scroll inside drawer
    document.querySelector(".drawer").scrollTop = document.querySelector(".drawer").scrollHeight;
  }

  function backToCart(){
    document.getElementById("checkoutPanel").style.display = "none";
    document.getElementById("orderResult").style.display = "none";
  }

  function buildOrderText(){
    const fn = document.getElementById("firstName").value.trim();
    const ln = document.getElementById("lastName").value.trim();
    const contact = document.getElementById("contact").value.trim();
    const address = document.getElementById("address").value.trim();
    const payMode = document.getElementById("payMode").value;
    const note = document.getElementById("note").value.trim();

    const items = Object.entries(state.cart).map(([id,qty])=>{
      const p = getProduct(id);
      return `- ${p.name} x${qty} = ${money(p.price*qty)}`;
    }).join("\n");

    const sub = subTotal();
    const disc = promoDiscount(sub);
    const ship = shippingFee();
    const tot = total();

    return [
      `🧾 NOUVELLE COMMANDE - ${SHOP.name}`,
      ``,
      `Client: ${fn} ${ln}`.trim(),
      `Contact: ${contact || "(à compléter)"}`,
      `Livraison: ${state.shippingMode}`,
      `Adresse / RDV: ${address || "(à compléter)"}`,
      `Paiement: ${payMode}`,
      note ? `Note: ${note}` : null,
      ``,
      `Produits:`,
      items,
      ``,
      `Sous-total: ${money(sub)}`,
      `Réduction (${state.promoCode || "—"}): -${money(disc)}`,
      `Livraison: ${money(ship)}`,
      `TOTAL: ${money(tot)}`,
      ``,
      `✅ À faire: confirmer avec le client + donner instructions de paiement/livraison.`
    ].filter(Boolean).join("\n");
  }

  function sendOrder(){
    if(cartCount() === 0) return;

    const fn = document.getElementById("firstName").value.trim();
    const contact = document.getElementById("contact").value.trim();
    if(!fn || !contact){
      toast("Ajoute au moins ton prénom + un contact");
      return;
    }

    const txt = buildOrderText();
    document.getElementById("orderText").value = txt;
    document.getElementById("orderResult").style.display = "block";
    toast("Commande générée ✅");
  }

  function copyOrder(){
    const ta = document.getElementById("orderText");
    ta.select();
    ta.setSelectionRange(0, 999999);
    document.execCommand("copy");
    toast("Copié ✅");
  }

  function closeAll(){
    closeCart();
  }

  /***********************
   * 6) INIT + EVENTS
   ***********************/
  window.__add = (id)=> addToCart(id, 1);
  window.__buy = (id)=> { addToCart(id, 1); openCart(); startCheckout(); };
  window.__inc = (id)=> setQty(id, (state.cart[id]||0)+1);
  window.__dec = (id)=> setQty(id, (state.cart[id]||0)-1);
  window.__set = (id, q)=> setQty(id, q);

  function init(){
    // apply config
    document.title = SHOP.name;
    renderHeader();
    renderFilters();

    // initial render
    renderGrid();
    renderCart();
    renderBadges();

    // listeners
    document.getElementById("openCartBtn").addEventListener("click", openCart);
    document.getElementById("closeCartBtn").addEventListener("click", closeCart);
    document.getElementById("drawerBack").addEventListener("click", (e)=>{ if(e.target.id==="drawerBack") closeCart(); });

    document.getElementById("q").addEventListener("input", (e)=>{
      state.q = e.target.value;
      renderGrid();
    });

    document.getElementById("cat").addEventListener("change", (e)=>{
      state.category = e.target.value;
      renderGrid();
    });

    document.getElementById("sort").addEventListener("change", (e)=>{
      state.sort = e.target.value;
      renderGrid();
    });

    document.getElementById("shippingMode").addEventListener("change", (e)=>{
      state.shippingMode = e.target.value;
      renderCart();
    });

    document.getElementById("currency").addEventListener("change", (e)=>{
      state.currency = e.target.value;
      renderGrid(); renderCart();
    });

    document.getElementById("applyPromo").addEventListener("click", applyPromo);
    document.getElementById("clearPromo").addEventListener("click", clearPromo);

    document.getElementById("clearCartBtn").addEventListener("click", ()=>{
      state.cart = {};
      save("cart", state.cart);
      toast("Panier vidé");
      renderCart(); renderBadges(); renderGrid();
    });

    document.getElementById("checkoutBtn").addEventListener("click", startCheckout);
    document.getElementById("backToCart").addEventListener("click", backToCart);
    document.getElementById("sendOrder").addEventListener("click", sendOrder);
    document.getElementById("copyOrder").addEventListener("click", copyOrder);
    document.getElementById("closeAll").addEventListener("click", closeAll);

    // load promo from storage into input
    if(state.promoCode) document.getElementById("promoInput").value = state.promoCode;

    // keyboard escape
    window.addEventListener("keydown", (e)=>{ if(e.key==="Escape") closeCart(); });
  }

  init();
</script>
</body>
</html>

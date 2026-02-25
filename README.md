<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Recetario Gourmet Internacional</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">
<style>
  :root { --primary: #6a5acd; --secondary: #836fff; --bg: #f3f0ff; }
  body { margin:0; font-family:'Poppins',sans-serif; background: var(--bg); }
  header { background: linear-gradient(90deg, var(--primary), var(--secondary)); color: white; text-align: center; padding: 30px; }
  .user-auth { background: white; padding: 10px; text-align: right; box-shadow: 0 2px 5px rgba(0,0,0,0.1); font-size: 0.9rem; }
  .food-img { width: 100%; height: 180px; border-radius: 10px; margin-bottom: 15px; display: block; object-fit: cover; }
  .tabs { display:flex; justify-content:center; flex-wrap:wrap; background:white; padding:15px; position:sticky; top:0; z-index:100; box-shadow:0 2px 10px rgba(0,0,0,0.1); }
  .tab-btn { background:#dcd6f7; border:none; margin:5px; padding:10px 20px; cursor:pointer; border-radius:20px; font-weight:600; transition:0.3s; }
  .tab-btn.active { background:var(--primary); color:white; }
  .recipes-section { display:none; padding:40px; }
  .recipes-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(300px,1fr)); gap:25px; }
  .recipe-card { background:white; border-radius:15px; padding:20px; box-shadow:0 8px 20px rgba(0,0,0,.1); cursor:pointer; transition:0.3s; }
  .recipe-card:hover { transform:translateY(-5px); }
  .recipe-card h3 a { text-decoration:none; color:var(--primary); }
  .recipe-card h3 a:hover { text-decoration:underline; }
  .details { max-height:0; overflow:hidden; transition:max-height .6s ease; margin-top:10px; font-size:0.9rem; }
  .details h4 { color:var(--secondary); margin-bottom:5px; }
  .comment-section { background:white; padding:25px; border-radius:15px; max-width:900px; margin:40px auto; }
  .comment-input { width:100%; padding:10px; border-radius:8px; border:1px solid #ddd; margin-bottom:10px; font-family:inherit; box-sizing:border-box; }
  .comment-btn { background:var(--primary); color:white; border:none; padding:10px 20px; border-radius:5px; cursor:pointer; font-weight:600; }
  .comment-list { margin-top:20px; border-top:1px solid #eee; padding-top:10px; }
  .comment-item { background:#f9f9f9; padding:10px; border-radius:5px; margin-bottom:10px; border-left:4px solid var(--primary); }
  .modal { display:none; position:fixed; z-index:200; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.6); }
  .modal-content { background:white; width:300px; margin:100px auto; padding:30px; border-radius:15px; text-align:center; }
  .modal-content input { width:90%; padding:10px; margin:10px 0; border:1px solid #ddd; border-radius:5px; }
  footer { text-align:center; padding:20px; background:var(--primary); color:white; margin-top:40px; }
</style>
</head>
<body>

<div class="user-auth">
  <span id="userWelcome">Bienvenido, Invitado</span> |
  <button onclick="openModal()" id="authBtn" style="border:none;background:none;color:var(--primary);cursor:pointer;font-weight:600;">Iniciar Sesión</button>
</div>

<header>
  <h1>Recetario Gourmet Internacional</h1>
  <p>15 Sabores del Mundo en tu Pantalla</p>
</header>

<div class="tabs">
  <button class="tab-btn active" onclick="showSection(event,'america')">América</button>
  <button class="tab-btn" onclick="showSection(event,'europa')">Europa</button>
  <button class="tab-btn" onclick="showSection(event,'asia')">Asia</button>
  <button class="tab-btn" onclick="showSection(event,'africa')">África</button>
  <button class="tab-btn" onclick="showSection(event,'oceania')">Oceanía</button>
</div>

<!-- AMÉRICA -->
<section id="america" class="recipes-section" style="display:block;">
  <div class="recipes-grid">

    <!-- Ceviche -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="plateCev" cx="50%" cy="50%" r="50%"><stop offset="0%" stop-color="#fff"/><stop offset="100%" stop-color="#f0ede8"/></radialGradient>
          <radialGradient id="bgCev" cx="50%" cy="40%" r="60%"><stop offset="0%" stop-color="#1a9650"/><stop offset="100%" stop-color="#0d6b35"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgCev)" rx="10"/>
        <!-- wooden table texture lines -->
        <line x1="0" y1="30" x2="400" y2="30" stroke="#16834a" stroke-width="1" opacity="0.4"/>
        <line x1="0" y1="60" x2="400" y2="60" stroke="#16834a" stroke-width="1" opacity="0.4"/>
        <line x1="0" y1="90" x2="400" y2="90" stroke="#16834a" stroke-width="1" opacity="0.4"/>
        <!-- Bowl -->
        <ellipse cx="200" cy="155" rx="110" ry="20" fill="#c8b99a" opacity="0.5"/>
        <ellipse cx="200" cy="120" rx="110" ry="55" fill="url(#plateCev)" stroke="#d4c5a9" stroke-width="2"/>
        <!-- Leche de tigre base (liquid) -->
        <ellipse cx="200" cy="125" rx="95" ry="42" fill="#e8d5a0" opacity="0.9"/>
        <!-- Fish chunks -->
        <rect x="155" y="100" width="28" height="18" rx="5" fill="#fff" stroke="#e0c090" stroke-width="1"/>
        <rect x="190" y="108" width="24" height="16" rx="4" fill="#fefefe" stroke="#ddb870" stroke-width="1"/>
        <rect x="220" y="98" width="26" height="19" rx="5" fill="#fffdf5" stroke="#e2c280" stroke-width="1"/>
        <rect x="170" y="118" width="22" height="15" rx="4" fill="#fff8e8" stroke="#d4b060" stroke-width="1"/>
        <rect x="205" y="125" width="20" height="14" rx="4" fill="#ffffff" stroke="#ddc070" stroke-width="1"/>
        <!-- Aji amarillo slices (orange) -->
        <ellipse cx="165" cy="115" rx="10" ry="5" fill="#f5a623" opacity="0.9"/>
        <ellipse cx="240" cy="110" rx="9" ry="4" fill="#f5a623" opacity="0.9"/>
        <ellipse cx="195" cy="130" rx="8" ry="4" fill="#f5a623" opacity="0.85"/>
        <!-- Red onion strips -->
        <path d="M175 105 Q185 102 195 106" stroke="#c0392b" stroke-width="2.5" fill="none" stroke-linecap="round"/>
        <path d="M210 118 Q220 115 230 119" stroke="#c0392b" stroke-width="2" fill="none" stroke-linecap="round"/>
        <path d="M158 122 Q168 119 175 123" stroke="#c0392b" stroke-width="2" fill="none" stroke-linecap="round"/>
        <!-- Cilantro leaves -->
        <ellipse cx="150" cy="108" rx="7" ry="4" fill="#27ae60" transform="rotate(-20,150,108)"/>
        <ellipse cx="153" cy="104" rx="6" ry="3" fill="#2ecc71" transform="rotate(10,153,104)"/>
        <ellipse cx="245" cy="120" rx="7" ry="4" fill="#27ae60" transform="rotate(15,245,120)"/>
        <ellipse cx="242" cy="116" rx="5" ry="3" fill="#2ecc71" transform="rotate(-10,242,116)"/>
        <!-- Corn kernels -->
        <circle cx="232" cy="130" r="4" fill="#f1c40f"/>
        <circle cx="241" cy="128" r="4" fill="#f39c12"/>
        <circle cx="236" cy="136" r="4" fill="#f1c40f"/>
        <!-- Lemon wedge -->
        <path d="M155 133 Q145 128 140 138 Q150 145 160 140 Z" fill="#f9e04b"/>
        <path d="M148 133 L148 143" stroke="#c8b400" stroke-width="0.8"/>
        <path d="M144 135 L153 141" stroke="#c8b400" stroke-width="0.8"/>
        <!-- Label -->
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.25)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇵🇪 CEVICHE PERUANO</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+ceviche+peruano" target="_blank" onclick="event.stopPropagation()">Ceviche Peruano</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Pescado fresco</li><li>Limón</li><li>Ají amarillo</li></ul></div>
    </div>

    <!-- Tacos al Pastor -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="bgTaco" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#8B2500"/><stop offset="100%" stop-color="#5c1a00"/></linearGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgTaco)" rx="10"/>
        <!-- plate shadow -->
        <ellipse cx="200" cy="165" rx="130" ry="12" fill="rgba(0,0,0,0.3)"/>

        <!-- Taco 1 (left) -->
        <g transform="translate(80,40) rotate(-15)">
          <path d="M0 80 Q50 20 100 80 Z" fill="#f5deb3" stroke="#c8a060" stroke-width="1.5"/>
          <path d="M5 78 Q50 30 95 78" fill="none" stroke="#d4a050" stroke-width="1"/>
          <!-- meat -->
          <path d="M20 68 Q50 55 80 68" fill="#c0392b" stroke="#922b21" stroke-width="1"/>
          <path d="M25 65 Q50 52 75 65" fill="#e74c3c" opacity="0.7"/>
          <!-- pineapple -->
          <circle cx="40" cy="60" r="6" fill="#f39c12"/>
          <circle cx="55" cy="58" r="5" fill="#f1c40f"/>
          <!-- cilantro -->
          <ellipse cx="30" cy="55" rx="6" ry="3" fill="#27ae60" transform="rotate(-20,30,55)"/>
          <ellipse cx="65" cy="54" rx="6" ry="3" fill="#2ecc71" transform="rotate(15,65,54)"/>
          <!-- onion -->
          <path d="M35 70 Q50 65 65 70" stroke="white" stroke-width="1.5" fill="none" opacity="0.8"/>
        </g>

        <!-- Taco 2 (center) -->
        <g transform="translate(155,30)">
          <path d="M0 80 Q50 18 100 80 Z" fill="#f0d090" stroke="#c8a060" stroke-width="1.5"/>
          <path d="M5 78 Q50 28 95 78" fill="none" stroke="#d4a050" stroke-width="1"/>
          <!-- meat achiote -->
          <path d="M15 70 Q50 58 85 70" fill="#c0392b" stroke="#922b21" stroke-width="1"/>
          <path d="M20 67 Q50 55 80 67" fill="#e74c3c" opacity="0.7"/>
          <!-- pineapple chunks -->
          <circle cx="35" cy="62" r="7" fill="#f39c12"/>
          <circle cx="50" cy="58" r="6" fill="#f1c40f"/>
          <circle cx="65" cy="62" r="6" fill="#e67e22"/>
          <!-- green sauce drops -->
          <circle cx="30" cy="55" r="3" fill="#27ae60"/>
          <circle cx="70" cy="53" r="3" fill="#2ecc71"/>
          <!-- cilantro -->
          <ellipse cx="42" cy="52" rx="7" ry="3.5" fill="#27ae60" transform="rotate(-10,42,52)"/>
          <ellipse cx="60" cy="50" rx="6" ry="3" fill="#2ecc71" transform="rotate(10,60,50)"/>
        </g>

        <!-- Taco 3 (right) -->
        <g transform="translate(230,45) rotate(12)">
          <path d="M0 80 Q50 22 100 80 Z" fill="#f5deb3" stroke="#c8a060" stroke-width="1.5"/>
          <path d="M5 78 Q50 32 95 78" fill="none" stroke="#d4a050" stroke-width="1"/>
          <!-- meat -->
          <path d="M18 70 Q50 57 82 70" fill="#c0392b" stroke="#922b21" stroke-width="1"/>
          <!-- pineapple -->
          <circle cx="45" cy="60" r="6" fill="#f1c40f"/>
          <circle cx="60" cy="58" r="5" fill="#f39c12"/>
          <!-- cilantro -->
          <ellipse cx="28" cy="55" rx="6" ry="3" fill="#27ae60" transform="rotate(-20,28,55)"/>
          <ellipse cx="70" cy="53" rx="6" ry="3" fill="#2ecc71" transform="rotate(15,70,53)"/>
        </g>

        <!-- limes garnish -->
        <path d="M340 120 Q330 108 320 118 Q330 130 342 125 Z" fill="#78c41a"/>
        <path d="M348 118 Q338 106 328 116 Q338 128 350 123 Z" fill="#a0d820" opacity="0.8"/>
        <!-- salsa bowl -->
        <ellipse cx="345" cy="145" rx="22" ry="10" fill="#c0392b" stroke="#922b21" stroke-width="1.5"/>
        <ellipse cx="345" cy="142" rx="18" ry="7" fill="#e74c3c"/>

        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇲🇽 TACOS AL PASTOR</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+tacos+mexicanos" target="_blank" onclick="event.stopPropagation()">Tacos al Pastor</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Carne de cerdo</li><li>Achiote</li><li>Piña</li></ul></div>
    </div>

    <!-- Filete Mignon -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgFil" cx="50%" cy="40%" r="60%"><stop offset="0%" stop-color="#2c1810"/><stop offset="100%" stop-color="#1a0e08"/></radialGradient>
          <radialGradient id="steakGrad" cx="40%" cy="40%" r="60%"><stop offset="0%" stop-color="#8B2500"/><stop offset="60%" stop-color="#6B1A00"/><stop offset="100%" stop-color="#3d0f00"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgFil)" rx="10"/>
        <!-- plate -->
        <ellipse cx="200" cy="155" rx="130" ry="18" fill="rgba(255,255,255,0.05)"/>
        <ellipse cx="200" cy="130" rx="128" ry="42" fill="#f5f0e8" stroke="#e0d5c0" stroke-width="2"/>
        <ellipse cx="200" cy="130" rx="108" ry="34" fill="#f8f4ee"/>
        <!-- steak -->
        <ellipse cx="185" cy="128" rx="68" ry="45" fill="url(#steakGrad)" stroke="#2c0f00" stroke-width="2"/>
        <!-- grill marks -->
        <path d="M145 110 Q175 100 205 108" stroke="#1a0800" stroke-width="4" fill="none" stroke-linecap="round" opacity="0.8"/>
        <path d="M148 122 Q178 112 208 120" stroke="#1a0800" stroke-width="3.5" fill="none" stroke-linecap="round" opacity="0.7"/>
        <path d="M150 134 Q180 124 210 132" stroke="#1a0800" stroke-width="3.5" fill="none" stroke-linecap="round" opacity="0.7"/>
        <!-- bacon wrap -->
        <rect x="118" y="100" width="8" height="56" rx="3" fill="#c0392b" stroke="#922b21" stroke-width="1"/>
        <rect x="119" y="100" width="6" height="56" rx="2" fill="#e74c3c" opacity="0.5"/>
        <!-- medium-rare interior hint -->
        <ellipse cx="182" cy="128" rx="32" ry="22" fill="#c0392b" opacity="0.3"/>
        <ellipse cx="182" cy="128" rx="18" ry="12" fill="#e74c3c" opacity="0.2"/>
        <!-- butter melting on top -->
        <ellipse cx="190" cy="112" rx="22" ry="10" fill="#f1c40f" opacity="0.7"/>
        <path d="M180 112 Q195 118 210 112" stroke="#d4a800" stroke-width="1" fill="none" opacity="0.6"/>
        <!-- herbs on butter -->
        <ellipse cx="185" cy="110" rx="5" ry="2.5" fill="#27ae60" transform="rotate(-20,185,110)"/>
        <ellipse cx="197" cy="108" rx="5" ry="2.5" fill="#2ecc71" transform="rotate(15,197,108)"/>
        <!-- asparagus -->
        <rect x="265" y="95" width="6" height="55" rx="3" fill="#27ae60"/>
        <rect x="275" y="92" width="6" height="58" rx="3" fill="#2ecc71"/>
        <rect x="285" y="97" width="6" height="53" rx="3" fill="#27ae60"/>
        <!-- asparagus tips -->
        <ellipse cx="268" cy="93" rx="5" ry="7" fill="#1e8449"/>
        <ellipse cx="278" cy="90" rx="5" ry="7" fill="#239b56"/>
        <ellipse cx="288" cy="95" rx="5" ry="7" fill="#1e8449"/>
        <!-- red wine sauce pool -->
        <ellipse cx="185" cy="162" rx="55" ry="8" fill="#7b241c" opacity="0.7"/>
        <!-- sauce drizzle -->
        <path d="M155 155 Q170 160 185 155 Q200 150 215 158" stroke="#922b21" stroke-width="2" fill="none"/>

        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.35)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🥩 FILETE MIGNON</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+filete+mignon" target="_blank" onclick="event.stopPropagation()">Filete Mignon</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Solomillo</li><li>Tocineta</li><li>Vino tinto</li></ul></div>
    </div>

  </div>
  <div class="comment-section">
    <h3>Opiniones de América</h3>
    <textarea class="comment-input" id="commentTextAmerica" placeholder="Escribe aquí..."></textarea>
    <button class="comment-btn" onclick="addComment('America')">Publicar</button>
    <div class="comment-list" id="listAmerica"></div>
  </div>
</section>

<!-- EUROPA -->
<section id="europa" class="recipes-section">
  <div class="recipes-grid">

    <!-- Pizza -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgPiz" cx="50%" cy="40%" r="70%"><stop offset="0%" stop-color="#e8572a"/><stop offset="100%" stop-color="#b03010"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgPiz)" rx="10"/>
        <!-- Pizza circle -->
        <circle cx="200" cy="100" r="88" fill="#e8c060" stroke="#c8a040" stroke-width="2"/>
        <!-- Crust ring -->
        <circle cx="200" cy="100" r="88" fill="none" stroke="#d4944a" stroke-width="14"/>
        <!-- Sauce -->
        <circle cx="200" cy="100" r="73" fill="#c0392b"/>
        <circle cx="200" cy="100" r="70" fill="#e74c3c" opacity="0.5"/>
        <!-- Cheese -->
        <ellipse cx="185" cy="92" rx="30" ry="22" fill="#f9e4b7" opacity="0.95"/>
        <ellipse cx="215" cy="108" rx="25" ry="18" fill="#f5dca0" opacity="0.9"/>
        <ellipse cx="198" cy="118" rx="20" ry="15" fill="#f9e4b7" opacity="0.85"/>
        <ellipse cx="175" cy="110" rx="18" ry="12" fill="#f5dca0" opacity="0.9"/>
        <ellipse cx="220" cy="90" rx="15" ry="12" fill="#f9e4b7" opacity="0.85"/>
        <!-- Mozzarella bubbles (golden) -->
        <circle cx="190" cy="88" r="5" fill="#e8b840" opacity="0.8"/>
        <circle cx="208" cy="102" r="4" fill="#d4a030" opacity="0.7"/>
        <circle cx="178" cy="108" r="4" fill="#e8b840" opacity="0.75"/>
        <!-- Basil leaves -->
        <ellipse cx="170" cy="92" rx="10" ry="5" fill="#27ae60" transform="rotate(-30,170,92)"/>
        <ellipse cx="167" cy="88" rx="8" ry="4" fill="#2ecc71" transform="rotate(10,167,88)"/>
        <ellipse cx="228" cy="112" rx="10" ry="5" fill="#27ae60" transform="rotate(20,228,112)"/>
        <ellipse cx="232" cy="108" rx="8" ry="4" fill="#2ecc71" transform="rotate(-10,232,108)"/>
        <ellipse cx="205" cy="75" rx="9" ry="4.5" fill="#27ae60" transform="rotate(-15,205,75)"/>
        <!-- Tomato slices -->
        <circle cx="215" cy="80" r="9" fill="#e74c3c" stroke="#c0392b" stroke-width="1"/>
        <line x1="215" y1="71" x2="215" y2="89" stroke="#c0392b" stroke-width="0.8"/>
        <line x1="206" y1="80" x2="224" y2="80" stroke="#c0392b" stroke-width="0.8"/>
        <circle cx="182" cy="120" r="8" fill="#e74c3c" stroke="#c0392b" stroke-width="1"/>
        <line x1="182" y1="112" x2="182" y2="128" stroke="#c0392b" stroke-width="0.8"/>
        <!-- Pizza slice cut lines -->
        <line x1="200" y1="12" x2="200" y2="188" stroke="#c8a040" stroke-width="1.5" opacity="0.5"/>
        <line x1="124" y1="56" x2="276" y2="144" stroke="#c8a040" stroke-width="1.5" opacity="0.5"/>
        <line x1="276" y1="56" x2="124" y2="144" stroke="#c8a040" stroke-width="1.5" opacity="0.5"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇮🇹 PIZZA MARGHERITA</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+pizza+margherita" target="_blank" onclick="event.stopPropagation()">Pizza Italiana</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Harina 00</li><li>Mozzarella</li><li>Albahaca</li></ul></div>
    </div>

    <!-- Paella -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgPae" cx="50%" cy="30%" r="70%"><stop offset="0%" stop-color="#c47a05"/><stop offset="100%" stop-color="#7a4a00"/></radialGradient>
          <radialGradient id="riceGrad" cx="50%" cy="50%" r="50%"><stop offset="0%" stop-color="#f0d060"/><stop offset="100%" stop-color="#d4a820"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgPae)" rx="10"/>
        <!-- Pan shadow -->
        <ellipse cx="200" cy="162" rx="148" ry="16" fill="rgba(0,0,0,0.4)"/>
        <!-- Paella pan -->
        <ellipse cx="200" cy="115" rx="148" ry="55" fill="#8B6914" stroke="#6b4f0a" stroke-width="3"/>
        <!-- Pan handles -->
        <rect x="42" y="108" width="18" height="14" rx="4" fill="#6b4f0a" stroke="#4a3508" stroke-width="1.5"/>
        <rect x="340" y="108" width="18" height="14" rx="4" fill="#6b4f0a" stroke="#4a3508" stroke-width="1.5"/>
        <!-- Rice base -->
        <ellipse cx="200" cy="118" rx="136" ry="46" fill="url(#riceGrad)"/>
        <!-- Saffron color overlay -->
        <ellipse cx="200" cy="118" rx="136" ry="46" fill="#f0a800" opacity="0.3"/>
        <!-- Rice grain texture -->
        <ellipse cx="170" cy="110" rx="4" ry="2" fill="#e8c84a" transform="rotate(-20,170,110)"/>
        <ellipse cx="185" cy="106" rx="4" ry="2" fill="#dfc040" transform="rotate(10,185,106)"/>
        <ellipse cx="200" cy="104" rx="4" ry="2" fill="#e8c84a" transform="rotate(-5,200,104)"/>
        <ellipse cx="215" cy="107" rx="4" ry="2" fill="#dfc040" transform="rotate(20,215,107)"/>
        <ellipse cx="230" cy="112" rx="4" ry="2" fill="#e8c84a" transform="rotate(-15,230,112)"/>
        <ellipse cx="160" cy="118" rx="4" ry="2" fill="#dfc040" transform="rotate(5,160,118)"/>
        <ellipse cx="175" cy="122" rx="4" ry="2" fill="#e8c84a" transform="rotate(-10,175,122)"/>
        <ellipse cx="190" cy="120" rx="4" ry="2" fill="#dfc040" transform="rotate(15,190,120)"/>
        <ellipse cx="205" cy="118" rx="4" ry="2" fill="#e8c84a" transform="rotate(-20,205,118)"/>
        <ellipse cx="220" cy="122" rx="4" ry="2" fill="#dfc040" transform="rotate(5,220,122)"/>
        <ellipse cx="235" cy="118" rx="4" ry="2" fill="#e8c84a" transform="rotate(20,235,118)"/>
        <ellipse cx="165" cy="130" rx="4" ry="2" fill="#dfc040" transform="rotate(-10,165,130)"/>
        <ellipse cx="180" cy="135" rx="4" ry="2" fill="#e8c84a" transform="rotate(5,180,135)"/>
        <ellipse cx="195" cy="132" rx="4" ry="2" fill="#dfc040" transform="rotate(-15,195,132)"/>
        <ellipse cx="210" cy="134" rx="4" ry="2" fill="#e8c84a" transform="rotate(10,210,134)"/>
        <ellipse cx="225" cy="130" rx="4" ry="2" fill="#dfc040" transform="rotate(-5,225,130)"/>
        <!-- Shrimp (gambas) -->
        <path d="M155 100 Q148 92 155 85 Q165 82 168 90 Q165 100 158 102 Z" fill="#e8784a" stroke="#c05030" stroke-width="1"/>
        <path d="M156 97 Q150 91 155 85" stroke="#c05030" stroke-width="1" fill="none"/>
        <path d="M245 105 Q252 97 245 90 Q235 87 232 95 Q235 105 242 107 Z" fill="#e8784a" stroke="#c05030" stroke-width="1"/>
        <path d="M244 102 Q250 96 245 90" stroke="#c05030" stroke-width="1" fill="none"/>
        <path d="M195 96 Q188 88 195 81 Q205 78 208 86 Q205 96 198 98 Z" fill="#e8784a" stroke="#c05030" stroke-width="1"/>
        <!-- Mussels -->
        <ellipse cx="175" cy="112" rx="12" ry="7" fill="#2c3e50" stroke="#1a252f" stroke-width="1"/>
        <ellipse cx="175" cy="112" rx="9" ry="5" fill="#f5deb3" opacity="0.7"/>
        <ellipse cx="225" cy="108" rx="12" ry="7" fill="#2c3e50" stroke="#1a252f" stroke-width="1" transform="rotate(15,225,108)"/>
        <ellipse cx="225" cy="108" rx="9" ry="5" fill="#f5deb3" opacity="0.7" transform="rotate(15,225,108)"/>
        <ellipse cx="200" cy="130" rx="12" ry="7" fill="#2c3e50" stroke="#1a252f" stroke-width="1" transform="rotate(-10,200,130)"/>
        <ellipse cx="200" cy="130" rx="9" ry="5" fill="#f5deb3" opacity="0.7" transform="rotate(-10,200,130)"/>
        <!-- Peas -->
        <circle cx="162" cy="125" r="4" fill="#27ae60"/>
        <circle cx="170" cy="128" r="4" fill="#2ecc71"/>
        <circle cx="232" cy="120" r="4" fill="#27ae60"/>
        <circle cx="240" cy="124" r="4" fill="#2ecc71"/>
        <!-- Red pepper strips -->
        <path d="M140 115 Q155 108 165 118" stroke="#e74c3c" stroke-width="3" fill="none" stroke-linecap="round"/>
        <path d="M235 125 Q248 118 258 128" stroke="#e74c3c" stroke-width="3" fill="none" stroke-linecap="round"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇪🇸 PAELLA ESPAÑOLA</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+paella+valenciana" target="_blank" onclick="event.stopPropagation()">Paella Española</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Arroz Bomba</li><li>Azafrán</li><li>Mariscos</li></ul></div>
    </div>

    <!-- Croissant -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgCro" cx="50%" cy="30%" r="70%"><stop offset="0%" stop-color="#f5e6c8"/><stop offset="100%" stop-color="#c8a878"/></radialGradient>
          <linearGradient id="croiGrad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#e8a030"/><stop offset="50%" stop-color="#c87820"/><stop offset="100%" stop-color="#a05010"/></linearGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgCro)" rx="10"/>
        <!-- cloth/napkin -->
        <rect x="60" y="80" width="280" height="80" rx="5" fill="white" opacity="0.6"/>
        <line x1="60" y1="90" x2="340" y2="90" stroke="#e0d0c0" stroke-width="0.8" opacity="0.5"/>
        <line x1="60" y1="100" x2="340" y2="100" stroke="#e0d0c0" stroke-width="0.8" opacity="0.5"/>

        <!-- Main Croissant body -->
        <path d="M120 130 Q140 60 200 55 Q260 60 280 130 Q240 145 200 148 Q160 145 120 130 Z" fill="url(#croiGrad)" stroke="#8b4510" stroke-width="1.5"/>
        <!-- Left horn -->
        <path d="M120 130 Q90 110 80 90 Q100 82 120 100 Q125 115 130 130 Z" fill="url(#croiGrad)" stroke="#8b4510" stroke-width="1"/>
        <!-- Right horn -->
        <path d="M280 130 Q310 110 320 90 Q300 82 280 100 Q275 115 270 130 Z" fill="url(#croiGrad)" stroke="#8b4510" stroke-width="1"/>
        <!-- Layered dough lines (lamination) -->
        <path d="M140 120 Q200 108 260 120" stroke="#8b4510" stroke-width="1.2" fill="none" opacity="0.5"/>
        <path d="M138 112 Q200 100 262 112" stroke="#8b4510" stroke-width="1" fill="none" opacity="0.4"/>
        <path d="M142 128 Q200 118 258 128" stroke="#8b4510" stroke-width="1" fill="none" opacity="0.4"/>
        <!-- Top shine/glaze -->
        <path d="M160 80 Q200 70 240 80" stroke="#f8d060" stroke-width="3" fill="none" opacity="0.5" stroke-linecap="round"/>
        <path d="M165 90 Q200 82 235 90" stroke="#f8e080" stroke-width="2" fill="none" opacity="0.4" stroke-linecap="round"/>
        <!-- Flaky top texture -->
        <path d="M175 72 Q185 68 195 72" stroke="#d4920a" stroke-width="1.5" fill="none" opacity="0.6"/>
        <path d="M205 70 Q215 66 225 70" stroke="#d4920a" stroke-width="1.5" fill="none" opacity="0.6"/>
        <path d="M165 82 Q170 78 178 82" stroke="#c88010" stroke-width="1" fill="none" opacity="0.5"/>
        <!-- Coffee cup beside -->
        <rect x="310" y="95" width="40" height="48" rx="5" fill="white" stroke="#d0c0a0" stroke-width="2"/>
        <rect x="312" y="97" width="36" height="20" rx="3" fill="#3d1a00"/>
        <path d="M350 108 Q360 108 360 118 Q360 128 350 128" stroke="#d0c0a0" stroke-width="2" fill="none"/>
        <!-- Coffee steam -->
        <path d="M325 92 Q328 85 325 78" stroke="#c0b0a0" stroke-width="1.5" fill="none" stroke-linecap="round" opacity="0.6"/>
        <path d="M335 90 Q338 83 335 76" stroke="#c0b0a0" stroke-width="1.5" fill="none" stroke-linecap="round" opacity="0.6"/>
        <!-- Butter pat -->
        <rect x="60" y="108" width="40" height="20" rx="4" fill="#f8d030" stroke="#d4a800" stroke-width="1"/>
        <line x1="65" y1="115" x2="95" y2="115" stroke="#d4a800" stroke-width="0.8" opacity="0.5"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.2)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="#5a3010" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇫🇷 CROISSANT FRANCÉS</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+croissant" target="_blank" onclick="event.stopPropagation()">Croissant Francés</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Mantequilla</li><li>Harina</li><li>Levadura</li></ul></div>
    </div>

  </div>
  <div class="comment-section">
    <h3>Opiniones de Europa</h3>
    <textarea class="comment-input" id="commentTextEuropa" placeholder="Escribe aquí..."></textarea>
    <button class="comment-btn" onclick="addComment('Europa')">Publicar</button>
    <div class="comment-list" id="listEuropa"></div>
  </div>
</section>

<!-- ASIA -->
<section id="asia" class="recipes-section">
  <div class="recipes-grid">

    <!-- Sushi -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="bgSus" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#1a2a1a"/><stop offset="100%" stop-color="#0a1a0a"/></linearGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgSus)" rx="10"/>
        <!-- Wooden board -->
        <rect x="30" y="50" width="340" height="110" rx="8" fill="#8B6914" stroke="#6b4f0a" stroke-width="2"/>
        <line x1="30" y1="70" x2="370" y2="70" stroke="#7a5c10" stroke-width="1" opacity="0.5"/>
        <line x1="30" y1="90" x2="370" y2="90" stroke="#7a5c10" stroke-width="1" opacity="0.4"/>
        <line x1="30" y1="120" x2="370" y2="120" stroke="#7a5c10" stroke-width="1" opacity="0.4"/>
        <line x1="30" y1="145" x2="370" y2="145" stroke="#7a5c10" stroke-width="1" opacity="0.3"/>

        <!-- Maki roll 1 (salmon) -->
        <rect x="50" y="68" width="38" height="38" rx="4" fill="#1a1a1a" stroke="#0a0a0a" stroke-width="1"/>
        <circle cx="69" cy="87" r="14" fill="white" stroke="#e8e0d0" stroke-width="0.5"/>
        <circle cx="69" cy="87" r="11" fill="#e8784a"/><!-- salmon -->
        <circle cx="69" cy="87" r="4" fill="#f0a0706" opacity="0.6"/>
        <ellipse cx="62" cy="80" rx="3" ry="5" fill="#fff" opacity="0.4" transform="rotate(-20,62,80)"/>
        <!-- Maki 2 -->
        <rect x="98" y="68" width="38" height="38" rx="4" fill="#1a1a1a" stroke="#0a0a0a" stroke-width="1"/>
        <circle cx="117" cy="87" r="14" fill="white" stroke="#e8e0d0" stroke-width="0.5"/>
        <circle cx="117" cy="87" r="11" fill="#c0392b"/><!-- tuna -->
        <ellipse cx="110" cy="80" rx="3" ry="5" fill="#e74c3c" opacity="0.5" transform="rotate(-20,110,80)"/>
        <!-- Maki 3 -->
        <rect x="146" y="68" width="38" height="38" rx="4" fill="#1a1a1a" stroke="#0a0a0a" stroke-width="1"/>
        <circle cx="165" cy="87" r="14" fill="white" stroke="#e8e0d0" stroke-width="0.5"/>
        <circle cx="165" cy="87" r="11" fill="#f9e4b7"/>
        <circle cx="165" cy="87" r="6" fill="#f1c40f" opacity="0.8"/><!-- egg tamago -->

        <!-- Nigiri row -->
        <!-- Nigiri 1 salmon -->
        <ellipse cx="230" cy="100" rx="25" ry="14" fill="#f5f0e8" stroke="#e0d5c0" stroke-width="1"/><!-- rice -->
        <path d="M208 95 Q230 80 252 95" fill="#e8784a" stroke="#c05030" stroke-width="1"/><!-- salmon slice -->
        <path d="M212 93 Q230 84 248 93" fill="#f0a060" opacity="0.5"/>
        <!-- Nigiri 2 tuna -->
        <ellipse cx="290" cy="100" rx="25" ry="14" fill="#f5f0e8" stroke="#e0d5c0" stroke-width="1"/>
        <path d="M268 95 Q290 80 312 95" fill="#c0392b" stroke="#922b21" stroke-width="1"/>
        <path d="M272 93 Q290 84 308 93" fill="#e74c3c" opacity="0.5"/>
        <!-- Nigiri 3 shrimp -->
        <ellipse cx="350" cy="100" rx="18" ry="12" fill="#f5f0e8" stroke="#e0d5c0" stroke-width="1"/>
        <path d="M334 96 Q350 84 366 96" fill="#e8784a" stroke="#c05030" stroke-width="1"/>

        <!-- Wasabi -->
        <ellipse cx="60" cy="148" rx="16" ry="8" fill="#27ae60"/>
        <path d="M50 145 Q60 140 70 145" stroke="#1e8449" stroke-width="1" fill="none"/>
        <!-- Ginger -->
        <path d="M90 142 Q100 135 112 140 Q108 148 96 150 Z" fill="#f8b4a0"/>
        <path d="M95 143 Q102 138 110 141" stroke="#e09080" stroke-width="0.8" fill="none"/>
        <!-- Soy sauce dish -->
        <ellipse cx="330" cy="148" rx="30" ry="12" fill="#2c1a0a" stroke="#1a0e06" stroke-width="1.5"/>
        <ellipse cx="330" cy="146" rx="26" ry="9" fill="#3d2410" opacity="0.7"/>

        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.4)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇯🇵 SUSHI JAPONÉS</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+sushi" target="_blank" onclick="event.stopPropagation()">Sushi Japonés</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Arroz</li><li>Pescado</li><li>Alga Nori</li></ul></div>
    </div>

    <!-- Pad Thai -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgPad" cx="50%" cy="40%" r="70%"><stop offset="0%" stop-color="#c47820"/><stop offset="100%" stop-color="#7a4800"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgPad)" rx="10"/>
        <!-- Wok/plate -->
        <ellipse cx="200" cy="155" rx="145" ry="18" fill="rgba(0,0,0,0.3)"/>
        <ellipse cx="200" cy="120" rx="145" ry="52" fill="#2c1a00" stroke="#1a0e00" stroke-width="2"/>
        <ellipse cx="200" cy="118" rx="135" ry="44" fill="#e8a020"/>
        <!-- Noodles base -->
        <path d="M80 110 Q120 95 160 108 Q200 120 240 105 Q280 90 320 110" stroke="#f0d070" stroke-width="4" fill="none" stroke-linecap="round"/>
        <path d="M75 120 Q115 105 155 118 Q200 130 245 115 Q285 100 325 120" stroke="#e8c860" stroke-width="4" fill="none" stroke-linecap="round"/>
        <path d="M80 130 Q120 115 160 128 Q200 140 240 125 Q280 110 320 130" stroke="#f0d070" stroke-width="3.5" fill="none" stroke-linecap="round"/>
        <path d="M85 118 Q110 108 135 120 Q160 130 185 118 Q210 106 235 118 Q260 130 290 118" stroke="#d4a840" stroke-width="2.5" fill="none" stroke-linecap="round" opacity="0.7"/>
        <path d="M90 108 Q115 98 140 110" stroke="#f5e080" stroke-width="2" fill="none" stroke-linecap="round" opacity="0.6"/>
        <path d="M250 112 Q275 102 300 114" stroke="#f5e080" stroke-width="2" fill="none" stroke-linecap="round" opacity="0.6"/>
        <!-- Shrimp -->
        <path d="M135 105 Q128 95 135 86 Q147 83 150 92 Q147 103 140 106 Z" fill="#e8784a" stroke="#c05030" stroke-width="1"/>
        <path d="M136 102 Q130 93 135 86" stroke="#c05030" stroke-width="0.8" fill="none"/>
        <path d="M265 108 Q272 98 265 89 Q253 86 250 95 Q253 106 260 109 Z" fill="#e8784a" stroke="#c05030" stroke-width="1"/>
        <!-- Egg scramble -->
        <ellipse cx="195" cy="105" rx="20" ry="12" fill="#f8d030" opacity="0.8"/>
        <ellipse cx="200" cy="103" rx="14" ry="9" fill="#f9e060" opacity="0.7"/>
        <!-- Bean sprouts -->
        <path d="M155 130 Q158 122 163 128" stroke="white" stroke-width="1.5" fill="none" stroke-linecap="round"/>
        <path d="M220 125 Q223 117 228 123" stroke="white" stroke-width="1.5" fill="none" stroke-linecap="round"/>
        <path d="M240 132 Q243 124 248 130" stroke="white" stroke-width="1.5" fill="none" stroke-linecap="round"/>
        <!-- Green onion -->
        <path d="M168 100 Q172 90 170 80" stroke="#27ae60" stroke-width="2" fill="none" stroke-linecap="round"/>
        <path d="M175 98 Q178 88 177 78" stroke="#2ecc71" stroke-width="2" fill="none" stroke-linecap="round"/>
        <!-- Peanuts -->
        <ellipse cx="290" cy="130" rx="6" ry="4" fill="#c8a020" transform="rotate(-20,290,130)"/>
        <ellipse cx="300" cy="126" rx="6" ry="4" fill="#d4b030" transform="rotate(10,300,126)"/>
        <ellipse cx="295" cy="136" rx="6" ry="4" fill="#c8a020" transform="rotate(15,295,136)"/>
        <!-- Lime wedge -->
        <path d="M310 118 Q300 108 292 116 Q298 126 310 124 Z" fill="#a0d020"/>
        <path d="M302 114 Q305 120 300 122" stroke="#7ab010" stroke-width="0.8" fill="none"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇹🇭 PAD THAI</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+pad+thai" target="_blank" onclick="event.stopPropagation()">Pad Thai Tailandés</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Fideos de arroz</li><li>Camarones</li><li>Tamarindo</li></ul></div>
    </div>

    <!-- Tikka Masala -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgTik" cx="40%" cy="30%" r="70%"><stop offset="0%" stop-color="#c44820"/><stop offset="100%" stop-color="#7a2a00"/></radialGradient>
          <radialGradient id="curryGrad" cx="50%" cy="40%" r="60%"><stop offset="0%" stop-color="#e85820"/><stop offset="100%" stop-color="#c03810"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgTik)" rx="10"/>
        <!-- Karahi/pot -->
        <ellipse cx="200" cy="158" rx="138" ry="16" fill="rgba(0,0,0,0.4)"/>
        <path d="M65 130 Q65 165 200 168 Q335 165 335 130 Q320 100 200 98 Q80 100 65 130 Z" fill="#4a3020" stroke="#3a2010" stroke-width="2"/>
        <!-- Curry sauce -->
        <ellipse cx="200" cy="130" rx="118" ry="38" fill="url(#curryGrad)"/>
        <!-- Sauce surface texture -->
        <ellipse cx="175" cy="125" rx="40" ry="15" fill="#f07030" opacity="0.5"/>
        <ellipse cx="225" cy="135" rx="35" ry="12" fill="#d04010" opacity="0.4"/>
        <!-- Oil pools on surface -->
        <ellipse cx="160" cy="118" rx="15" ry="6" fill="#f0a020" opacity="0.5"/>
        <ellipse cx="240" cy="122" rx="12" ry="5" fill="#e89020" opacity="0.5"/>
        <!-- Chicken pieces -->
        <path d="M150 120 Q155 108 170 112 Q178 120 168 130 Q155 132 150 120 Z" fill="#d4704a" stroke="#b05030" stroke-width="1"/>
        <path d="M152 118 Q160 110 168 115" stroke="#c06040" stroke-width="0.8" fill="none"/>
        <path d="M185 112 Q190 100 205 104 Q213 112 203 122 Q190 124 185 112 Z" fill="#d4704a" stroke="#b05030" stroke-width="1"/>
        <path d="M220 118 Q225 106 240 110 Q248 118 238 128 Q225 130 220 118 Z" fill="#c86040" stroke="#a05030" stroke-width="1"/>
        <!-- Charred/tikka marks on chicken -->
        <path d="M155 115 Q162 111 168 114" stroke="#8B3010" stroke-width="2" fill="none" opacity="0.7"/>
        <path d="M190 107 Q198 103 204 107" stroke="#8B3010" stroke-width="2" fill="none" opacity="0.7"/>
        <!-- Cream swirl -->
        <path d="M190 128 Q200 122 210 128 Q205 134 195 134 Q190 131 190 128 Z" fill="white" opacity="0.7"/>
        <path d="M192 129 Q200 124 208 129" stroke="white" stroke-width="1" fill="none" opacity="0.5"/>
        <!-- Cilantro garnish -->
        <ellipse cx="165" cy="105" rx="7" ry="3.5" fill="#27ae60" transform="rotate(-20,165,105)"/>
        <ellipse cx="170" cy="101" rx="6" ry="3" fill="#2ecc71" transform="rotate(15,170,101)"/>
        <ellipse cx="235" cy="107" rx="7" ry="3.5" fill="#27ae60" transform="rotate(20,235,107)"/>
        <!-- Rice on the side -->
        <ellipse cx="335" cy="135" rx="35" ry="25" fill="#f5f0e0" stroke="#e0d5c0" stroke-width="1"/>
        <ellipse cx="335" cy="132" rx="28" ry="20" fill="#f8f4e8"/>
        <!-- Rice grains texture -->
        <ellipse cx="325" cy="128" rx="4" ry="2" fill="#f0e8d0" transform="rotate(-20,325,128)"/>
        <ellipse cx="335" cy="126" rx="4" ry="2" fill="#ece0c8" transform="rotate(10,335,126)"/>
        <ellipse cx="345" cy="129" rx="4" ry="2" fill="#f0e8d0" transform="rotate(-5,345,129)"/>
        <ellipse cx="330" cy="136" rx="4" ry="2" fill="#ece0c8" transform="rotate(15,330,136)"/>
        <ellipse cx="342" cy="137" rx="4" ry="2" fill="#f0e8d0" transform="rotate(-10,342,137)"/>
        <!-- Naan bread -->
        <ellipse cx="65" cy="140" rx="40" ry="22" fill="#f0d090" stroke="#d4a840" stroke-width="1.5"/>
        <path d="M40 135 Q65 125 90 135" stroke="#c8941a" stroke-width="1" fill="none"/>
        <path d="M45 142 Q65 132 85 142" stroke="#c8941a" stroke-width="0.8" fill="none"/>
        <!-- Naan char spots -->
        <circle cx="52" cy="138" r="3" fill="#8B4510" opacity="0.6"/>
        <circle cx="75" cy="132" r="2.5" fill="#8B4510" opacity="0.5"/>
        <circle cx="82" cy="140" r="2" fill="#8B4510" opacity="0.5"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇮🇳 POLLO TIKKA MASALA</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+tikka+masala" target="_blank" onclick="event.stopPropagation()">Pollo Tikka Masala</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Pollo</li><li>Yogur</li><li>Especias</li></ul></div>
    </div>

  </div>
  <div class="comment-section">
    <h3>Opiniones de Asia</h3>
    <textarea class="comment-input" id="commentTextAsia" placeholder="Escribe aquí..."></textarea>
    <button class="comment-btn" onclick="addComment('Asia')">Publicar</button>
    <div class="comment-list" id="listAsia"></div>
  </div>
</section>

<!-- ÁFRICA -->
<section id="africa" class="recipes-section">
  <div class="recipes-grid">

    <!-- Cuscus -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgCus" cx="50%" cy="30%" r="70%"><stop offset="0%" stop-color="#c47820"/><stop offset="100%" stop-color="#8B4500"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgCus)" rx="10"/>
        <!-- tagine plate -->
        <ellipse cx="200" cy="155" rx="140" ry="18" fill="rgba(0,0,0,0.3)"/>
        <ellipse cx="200" cy="130" rx="140" ry="44" fill="#c47828" stroke="#a05a10" stroke-width="2"/>
        <ellipse cx="200" cy="125" rx="128" ry="36" fill="#e8c878"/>
        <!-- Couscous mound -->
        <ellipse cx="200" cy="118" rx="90" ry="30" fill="#f5dea0"/>
        <ellipse cx="200" cy="112" rx="70" ry="22" fill="#f8e8b0"/>
        <!-- Couscous texture dots -->
        <circle cx="178" cy="112" r="2" fill="#e8d090"/><circle cx="185" cy="108" r="2" fill="#d8c080"/>
        <circle cx="192" cy="115" r="2" fill="#e8d090"/><circle cx="200" cy="109" r="2" fill="#d8c080"/>
        <circle cx="208" cy="114" r="2" fill="#e8d090"/><circle cx="215" cy="108" r="2" fill="#d8c080"/>
        <circle cx="222" cy="113" r="2" fill="#e8d090"/><circle cx="174" cy="118" r="2" fill="#d8c080"/>
        <circle cx="182" cy="121" r="2" fill="#e8d090"/><circle cx="190" cy="120" r="2" fill="#d8c080"/>
        <circle cx="200" cy="118" r="2" fill="#e8d090"/><circle cx="210" cy="120" r="2" fill="#d8c080"/>
        <circle cx="218" cy="117" r="2" fill="#e8d090"/><circle cx="226" cy="120" r="2" fill="#d8c080"/>
        <!-- Veggies on top -->
        <circle cx="180" cy="103" r="10" fill="#e74c3c"/><!-- tomato -->
        <circle cx="180" cy="103" r="7" fill="#c0392b" opacity="0.5"/>
        <ellipse cx="205" cy="100" rx="12" ry="8" fill="#e67e22"/><!-- carrot -->
        <ellipse cx="205" cy="98" rx="8" ry="5" fill="#f39c12" opacity="0.6"/>
        <ellipse cx="225" cy="105" rx="8" ry="6" fill="#27ae60"/><!-- zucchini -->
        <path d="M168 100 Q175 95 182 98" stroke="#1e8449" stroke-width="1.5" fill="none"/>
        <!-- chickpeas -->
        <circle cx="156" cy="118" r="6" fill="#d4a830"/><circle cx="244" cy="118" r="6" fill="#d4a830"/>
        <circle cx="162" cy="128" r="6" fill="#c89820"/><circle cx="238" cy="128" r="6" fill="#c89820"/>
        <!-- Broth pool -->
        <ellipse cx="200" cy="140" rx="100" ry="12" fill="#c07820" opacity="0.5"/>
        <!-- herbs -->
        <ellipse cx="188" cy="97" rx="6" ry="3" fill="#27ae60" transform="rotate(-15,188,97)"/>
        <ellipse cx="220" cy="96" rx="5" ry="2.5" fill="#2ecc71" transform="rotate(15,220,96)"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇲🇦 CUSCÚS MARROQUÍ</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+cuscus+marroqui" target="_blank" onclick="event.stopPropagation()">Cuscús Marroquí</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Sémola</li><li>Verduras</li><li>Especias</li></ul></div>
    </div>

    <!-- Jollof Rice -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgJol" cx="50%" cy="30%" r="70%"><stop offset="0%" stop-color="#c03010"/><stop offset="100%" stop-color="#6a1808"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgJol)" rx="10"/>
        <ellipse cx="200" cy="155" rx="145" ry="16" fill="rgba(0,0,0,0.3)"/>
        <!-- Pot/pan -->
        <ellipse cx="200" cy="130" rx="145" ry="46" fill="#3a2010" stroke="#2a1008" stroke-width="2"/>
        <ellipse cx="200" cy="122" rx="132" ry="36" fill="#e84820"/>
        <!-- Rice layer -->
        <ellipse cx="200" cy="118" rx="120" ry="30" fill="#d44018"/>
        <ellipse cx="200" cy="115" rx="106" ry="25" fill="#e85025"/>
        <!-- Rice grains (orange-red stained) -->
        <ellipse cx="168" cy="112" rx="4" ry="2" fill="#f07030" transform="rotate(-20,168,112)"/>
        <ellipse cx="178" cy="108" rx="4" ry="2" fill="#e86020" transform="rotate(10,178,108)"/>
        <ellipse cx="188" cy="113" rx="4" ry="2" fill="#f07030" transform="rotate(-5,188,113)"/>
        <ellipse cx="198" cy="109" rx="4" ry="2" fill="#e86020" transform="rotate(20,198,109)"/>
        <ellipse cx="208" cy="112" rx="4" ry="2" fill="#f07030" transform="rotate(-15,208,112)"/>
        <ellipse cx="218" cy="108" rx="4" ry="2" fill="#e86020" transform="rotate(5,218,108)"/>
        <ellipse cx="228" cy="113" rx="4" ry="2" fill="#f07030" transform="rotate(-20,228,113)"/>
        <ellipse cx="162" cy="120" rx="4" ry="2" fill="#e86020" transform="rotate(10,162,120)"/>
        <ellipse cx="172" cy="124" rx="4" ry="2" fill="#f07030" transform="rotate(-10,172,124)"/>
        <ellipse cx="182" cy="121" rx="4" ry="2" fill="#e86020" transform="rotate(15,182,121)"/>
        <ellipse cx="192" cy="124" rx="4" ry="2" fill="#f07030" transform="rotate(-5,192,124)"/>
        <ellipse cx="202" cy="121" rx="4" ry="2" fill="#e86020" transform="rotate(20,202,121)"/>
        <ellipse cx="212" cy="124" rx="4" ry="2" fill="#f07030" transform="rotate(-15,212,124)"/>
        <ellipse cx="222" cy="121" rx="4" ry="2" fill="#e86020" transform="rotate(5,222,121)"/>
        <ellipse cx="232" cy="124" rx="4" ry="2" fill="#f07030" transform="rotate(-20,232,124)"/>
        <!-- Tomato chunks -->
        <circle cx="170" cy="103" r="9" fill="#e74c3c" stroke="#c0392b" stroke-width="1"/>
        <circle cx="230" cy="105" r="8" fill="#e74c3c" stroke="#c0392b" stroke-width="1"/>
        <!-- Bell pepper -->
        <path d="M195 100 Q202 93 210 100 Q206 108 198 107 Z" fill="#e74c3c"/>
        <path d="M152 110 Q158 103 165 109 Q162 117 154 116 Z" fill="#27ae60"/>
        <!-- Chicken piece -->
        <path d="M246 106 Q252 96 265 100 Q270 110 258 118 Q246 117 246 106 Z" fill="#d4704a" stroke="#b05030" stroke-width="1"/>
        <path d="M250 103 Q258 98 264 102" stroke="#8B3010" stroke-width="1.5" fill="none"/>
        <!-- Steam -->
        <path d="M185 93 Q188 85 185 77" stroke="white" stroke-width="1.5" fill="none" stroke-linecap="round" opacity="0.5"/>
        <path d="M200 90 Q203 82 200 74" stroke="white" stroke-width="1.5" fill="none" stroke-linecap="round" opacity="0.5"/>
        <path d="M215 93 Q218 85 215 77" stroke="white" stroke-width="1.5" fill="none" stroke-linecap="round" opacity="0.5"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🌍 ARROZ JOLLOF</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+jollof+rice" target="_blank" onclick="event.stopPropagation()">Arroz Jollof</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Arroz</li><li>Tomate</li><li>Pimientos</li></ul></div>
    </div>

    <!-- Tagine -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgTag" cx="50%" cy="30%" r="70%"><stop offset="0%" stop-color="#8B5e0a"/><stop offset="100%" stop-color="#4a2e00"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgTag)" rx="10"/>
        <!-- Tagine lid (conical) -->
        <polygon points="200,15 310,90 90,90" fill="#c47820" stroke="#a05a10" stroke-width="2"/>
        <polygon points="200,20 305,88 95,88" fill="#d4884a" opacity="0.5"/>
        <!-- Lid handle knob -->
        <circle cx="200" cy="18" r="8" fill="#8B4510" stroke="#6b3008" stroke-width="1.5"/>
        <!-- Tagine base dish -->
        <ellipse cx="200" cy="140" rx="148" ry="48" fill="#b87020" stroke="#8B5010" stroke-width="2.5"/>
        <ellipse cx="200" cy="132" rx="135" ry="38" fill="#e89a30"/>
        <!-- Broth -->
        <ellipse cx="200" cy="132" rx="120" ry="28" fill="#c47820" opacity="0.8"/>
        <!-- Chicken pieces in broth -->
        <path d="M145 125 Q152 113 167 117 Q174 127 162 137 Q148 136 145 125 Z" fill="#d4704a" stroke="#b05030" stroke-width="1"/>
        <path d="M147 123 Q155 116 165 119" stroke="#8B3010" stroke-width="1.5" fill="none"/>
        <path d="M185 118 Q192 106 207 110 Q214 120 202 130 Q188 129 185 118 Z" fill="#d4704a" stroke="#b05030" stroke-width="1"/>
        <path d="M225 122 Q232 110 247 114 Q254 124 242 134 Q228 133 225 122 Z" fill="#c86040" stroke="#a05030" stroke-width="1"/>
        <!-- Preserved lemon slices -->
        <circle cx="162" cy="140" r="10" fill="#f9e04b" stroke="#d4b800" stroke-width="1"/>
        <line x1="162" y1="130" x2="162" y2="150" stroke="#c8a800" stroke-width="0.8"/>
        <line x1="152" y1="140" x2="172" y2="140" stroke="#c8a800" stroke-width="0.8"/>
        <circle cx="240" cy="138" r="9" fill="#f9e04b" stroke="#d4b800" stroke-width="1"/>
        <line x1="240" y1="129" x2="240" y2="147" stroke="#c8a800" stroke-width="0.8"/>
        <!-- Olives -->
        <ellipse cx="178" cy="132" rx="7" ry="5" fill="#2c3e50"/>
        <ellipse cx="178" cy="131" rx="4" ry="3" fill="#4a6070" opacity="0.5"/>
        <ellipse cx="222" cy="130" rx="7" ry="5" fill="#2c3e50"/>
        <ellipse cx="255" cy="138" rx="7" ry="5" fill="#8B6914"/><!-- green olive -->
        <!-- Herbs (cilantro/parsley) -->
        <ellipse cx="200" cy="120" rx="8" ry="4" fill="#27ae60" transform="rotate(-10,200,120)"/>
        <ellipse cx="205" cy="116" rx="6" ry="3" fill="#2ecc71" transform="rotate(15,205,116)"/>
        <ellipse cx="195" cy="116" rx="6" ry="3" fill="#27ae60" transform="rotate(-20,195,116)"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇲🇦 TAGINE DE POLLO</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+tagine" target="_blank" onclick="event.stopPropagation()">Tagine de Pollo</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Pollo</li><li>Limón en conserva</li><li>Aceitunas</li></ul></div>
    </div>

  </div>
  <div class="comment-section">
    <h3>Opiniones de África</h3>
    <textarea class="comment-input" id="commentTextAfrica" placeholder="Escribe aquí..."></textarea>
    <button class="comment-btn" onclick="addComment('Africa')">Publicar</button>
    <div class="comment-list" id="listAfrica"></div>
  </div>
</section>

<!-- OCEANÍA -->
<section id="oceania" class="recipes-section">
  <div class="recipes-grid">

    <!-- Pavlova -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgPav" cx="50%" cy="30%" r="70%"><stop offset="0%" stop-color="#f0e0f8"/><stop offset="100%" stop-color="#c8a8e0"/></radialGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgPav)" rx="10"/>
        <!-- Cake plate -->
        <ellipse cx="200" cy="158" rx="130" ry="14" fill="rgba(255,255,255,0.4)"/>
        <ellipse cx="200" cy="148" rx="128" ry="16" fill="white" stroke="#e0d0f0" stroke-width="1.5"/>
        <!-- Pavlova meringue base -->
        <ellipse cx="200" cy="130" rx="105" ry="40" fill="white" stroke="#f0e8f8" stroke-width="1"/>
        <ellipse cx="200" cy="125" rx="88" ry="32" fill="#faf8ff"/>
        <!-- Meringue peaks/texture -->
        <path d="M112 128 Q120 112 130 118 Q138 108 148 116 Q158 105 168 114 Q178 103 188 112 Q198 102 208 112 Q218 103 228 113 Q238 105 248 115 Q258 108 268 118 Q278 112 288 128" stroke="white" stroke-width="2" fill="none" stroke-linecap="round"/>
        <path d="M115 132 Q125 118 135 124 Q143 114 153 122 Q163 112 173 120 Q183 110 193 118" stroke="#f5f0ff" stroke-width="1.5" fill="none" stroke-linecap="round"/>
        <!-- Whipped cream on top -->
        <ellipse cx="200" cy="112" rx="65" ry="22" fill="#fffdf8" stroke="#f0e8e0" stroke-width="0.5"/>
        <ellipse cx="200" cy="108" rx="50" ry="16" fill="white"/>
        <!-- Strawberries -->
        <path d="M168 102 Q172 90 180 95 Q183 103 176 108 Z" fill="#e74c3c"/>
        <path d="M170 102 Q174 95 178 98" stroke="#c0392b" stroke-width="0.5" fill="none"/>
        <circle cx="172" cy="90" r="3" fill="#27ae60"/><!-- strawberry top -->
        <path d="M188 98 Q192 86 200 91 Q203 99 196 104 Z" fill="#c0392b"/>
        <circle cx="192" cy="86" r="3" fill="#27ae60"/>
        <path d="M208 100 Q212 88 220 93 Q223 101 216 106 Z" fill="#e74c3c"/>
        <circle cx="212" cy="88" r="3" fill="#27ae60"/>
        <!-- Blueberries -->
        <circle cx="180" cy="108" r="5" fill="#6c3483"/><circle cx="190" cy="112" r="5" fill="#7d3c98"/>
        <circle cx="200" cy="108" r="5" fill="#6c3483"/><circle cx="210" cy="112" r="5" fill="#7d3c98"/>
        <circle cx="220" cy="108" r="5" fill="#6c3483"/>
        <!-- Kiwi slices -->
        <circle cx="155" cy="115" r="12" fill="#a0d050" stroke="#78a030" stroke-width="1"/>
        <circle cx="155" cy="115" r="8" fill="#c8e870"/>
        <circle cx="155" cy="115" r="3" fill="#f8f4e0"/>
        <circle cx="152" cy="110" r="1.5" fill="#78a030"/><circle cx="158" cy="109" r="1.5" fill="#78a030"/>
        <circle cx="160" cy="115" r="1.5" fill="#78a030"/><circle cx="157" cy="120" r="1.5" fill="#78a030"/>
        <circle cx="151" cy="119" r="1.5" fill="#78a030"/>
        <!-- Passion fruit -->
        <circle cx="245" cy="112" r="12" fill="#f39c12" stroke="#d68910" stroke-width="1"/>
        <circle cx="245" cy="112" r="8" fill="#f9e04b"/>
        <circle cx="245" cy="112" r="4" fill="#f39c12" opacity="0.5"/>
        <!-- Drizzle of passion fruit -->
        <path d="M230 122 Q245 128 260 122" stroke="#f39c12" stroke-width="1.5" fill="none" opacity="0.6"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(180,120,220,0.4)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇳🇿 PAVLOVA</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+pavlova" target="_blank" onclick="event.stopPropagation()">Pavlova Neozelandesa</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Claras de huevo</li><li>Azúcar</li><li>Frutos rojos</li></ul></div>
    </div>

    <!-- Meat Pie -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="bgMeat" cx="50%" cy="40%" r="70%"><stop offset="0%" stop-color="#5a3010"/><stop offset="100%" stop-color="#2c1508"/></radialGradient>
          <linearGradient id="pastryGrad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#e8b040"/><stop offset="100%" stop-color="#c07820"/></linearGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgMeat)" rx="10"/>
        <!-- Pie box/container -->
        <rect x="90" y="50" width="220" height="115" rx="5" fill="#c8a020" stroke="#a07810" stroke-width="2"/>
        <!-- Pie walls -->
        <rect x="95" y="120" width="210" height="40" rx="3" fill="#d4b030"/>
        <!-- Pie top crust -->
        <rect x="88" y="48" width="224" height="75" rx="5" fill="url(#pastryGrad)" stroke="#8B5e00" stroke-width="2"/>
        <!-- Pastry top texture (golden) -->
        <rect x="90" y="50" width="220" height="72" rx="4" fill="#d4a030" opacity="0.3"/>
        <!-- Egg wash shine -->
        <path d="M95 58 Q200 50 305 58" stroke="#f8e060" stroke-width="2" fill="none" opacity="0.5"/>
        <path d="M95 68 Q200 60 305 68" stroke="#f0d040" stroke-width="1.5" fill="none" opacity="0.4"/>
        <!-- Pastry scored lines -->
        <line x1="130" y1="50" x2="130" y2="122" stroke="#a07810" stroke-width="1" opacity="0.5"/>
        <line x1="200" y1="48" x2="200" y2="122" stroke="#a07810" stroke-width="1" opacity="0.5"/>
        <line x1="270" y1="50" x2="270" y2="122" stroke="#a07810" stroke-width="1" opacity="0.5"/>
        <line x1="88" y1="85" x2="312" y2="85" stroke="#a07810" stroke-width="1" opacity="0.5"/>
        <!-- Steam holes -->
        <circle cx="165" cy="70" r="5" fill="#8B5e00"/>
        <circle cx="200" cy="68" r="5" fill="#8B5e00"/>
        <circle cx="235" cy="70" r="5" fill="#8B5e00"/>
        <!-- Steam from holes -->
        <path d="M165 62 Q168 54 165 46" stroke="white" stroke-width="1.2" fill="none" stroke-linecap="round" opacity="0.6"/>
        <path d="M200 60 Q203 52 200 44" stroke="white" stroke-width="1.2" fill="none" stroke-linecap="round" opacity="0.6"/>
        <path d="M235 62 Q238 54 235 46" stroke="white" stroke-width="1.2" fill="none" stroke-linecap="round" opacity="0.6"/>
        <!-- Filling visible at bottom -->
        <rect x="95" y="115" width="210" height="8" rx="2" fill="#5a2a08"/>
        <!-- Gravy drips on side -->
        <path d="M130 122 Q128 132 126 140" stroke="#3d1a00" stroke-width="3" fill="none" stroke-linecap="round"/>
        <path d="M200 122 Q198 130 197 136" stroke="#3d1a00" stroke-width="2" fill="none" stroke-linecap="round"/>
        <path d="M265 122 Q268 132 270 138" stroke="#3d1a00" stroke-width="2.5" fill="none" stroke-linecap="round"/>
        <!-- Tomato sauce side dip -->
        <ellipse cx="340" cy="140" rx="30" ry="20" fill="#e74c3c" stroke="#c0392b" stroke-width="1.5"/>
        <ellipse cx="340" cy="137" rx="24" ry="14" fill="#c0392b" opacity="0.5"/>
        <!-- Chips/fries beside -->
        <rect x="55" y="90" width="8" height="55" rx="3" fill="#f5c842"/>
        <rect x="67" y="85" width="8" height="60" rx="3" fill="#f0b830"/>
        <rect x="79" y="88" width="8" height="57" rx="3" fill="#f5c842"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇦🇺 MEAT PIE AUSTRALIANO</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+meat+pie+australiano" target="_blank" onclick="event.stopPropagation()">Meat Pie Australiano</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Hojaldre</li><li>Carne picada</li><li>Salsa Gravy</li></ul></div>
    </div>

    <!-- Lamingtons -->
    <div class="recipe-card" onclick="toggleDetails(this)">
      <svg class="food-img" viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="bgLam" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#5a2a10"/><stop offset="100%" stop-color="#2a1008"/></linearGradient>
        </defs>
        <rect width="400" height="180" fill="url(#bgLam)" rx="10"/>
        <!-- Plate/board -->
        <rect x="30" y="55" width="340" height="110" rx="8" fill="#f5f0e8" stroke="#e0d5c0" stroke-width="1.5"/>

        <!-- Lamington 1 -->
        <g transform="translate(55,65)">
          <rect width="80" height="80" rx="6" fill="#3d1a08" stroke="#2a1005" stroke-width="1"/><!-- chocolate coat -->
          <rect x="3" y="3" width="74" height="74" rx="4" fill="#f8f4ee"/><!-- inside sponge -->
          <!-- Coconut flakes -->
          <rect x="0" y="0" width="80" height="4" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="0" y="76" width="80" height="4" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="0" y="0" width="4" height="80" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="76" y="0" width="4" height="80" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <!-- Individual coconut shreds -->
          <rect x="5" y="2" width="10" height="2" rx="1" fill="white" transform="rotate(-10,10,3)"/>
          <rect x="20" y="1" width="8" height="2" rx="1" fill="white" transform="rotate(5,24,2)"/>
          <rect x="35" y="2" width="11" height="2" rx="1" fill="white" transform="rotate(-8,40,3)"/>
          <rect x="52" y="1" width="9" height="2" rx="1" fill="white" transform="rotate(12,56,2)"/>
          <rect x="65" y="2" width="10" height="2" rx="1" fill="white" transform="rotate(-5,70,3)"/>
          <!-- Jam layer visible inside -->
          <rect x="6" y="35" width="68" height="10" rx="2" fill="#e74c3c" opacity="0.8"/>
          <!-- Cream layer -->
          <rect x="6" y="20" width="68" height="14" rx="2" fill="white" opacity="0.9"/>
          <!-- Sponge top layer -->
          <rect x="6" y="6" width="68" height="13" rx="2" fill="#f5deb3" opacity="0.8"/>
          <!-- Sponge bottom -->
          <rect x="6" y="47" width="68" height="24" rx="2" fill="#f5deb3" opacity="0.8"/>
        </g>

        <!-- Lamington 2 (raspberry variant) -->
        <g transform="translate(160,65)">
          <rect width="80" height="80" rx="6" fill="#3d1a08" stroke="#2a1005" stroke-width="1"/>
          <rect x="3" y="3" width="74" height="74" rx="4" fill="#f8f4ee"/>
          <!-- Coconut coat -->
          <rect x="0" y="0" width="80" height="4" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="0" y="76" width="80" height="4" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="0" y="0" width="4" height="80" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="76" y="0" width="4" height="80" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="8" y="1" width="9" height="2" rx="1" fill="white" transform="rotate(8,12,2)"/>
          <rect x="25" y="2" width="11" height="2" rx="1" fill="white" transform="rotate(-12,30,3)"/>
          <rect x="42" y="1" width="8" height="2" rx="1" fill="white" transform="rotate(6,46,2)"/>
          <rect x="58" y="2" width="12" height="2" rx="1" fill="white" transform="rotate(-8,64,3)"/>
          <rect x="6" y="38" width="68" height="10" rx="2" fill="#c0392b" opacity="0.8"/>
          <rect x="6" y="20" width="68" height="17" rx="2" fill="white" opacity="0.9"/>
          <rect x="6" y="6" width="68" height="13" rx="2" fill="#f5deb3" opacity="0.8"/>
          <rect x="6" y="50" width="68" height="22" rx="2" fill="#f5deb3" opacity="0.8"/>
        </g>

        <!-- Lamington 3 (cut/showing interior) -->
        <g transform="translate(265,65)">
          <rect width="80" height="80" rx="6" fill="#3d1a08" stroke="#2a1005" stroke-width="1"/>
          <rect x="3" y="3" width="74" height="74" rx="4" fill="#f8f4ee"/>
          <rect x="0" y="0" width="80" height="4" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="0" y="76" width="80" height="4" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="0" y="0" width="4" height="80" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="76" y="0" width="4" height="80" rx="2" fill="#f5f5f5" opacity="0.8"/>
          <rect x="12" y="1" width="10" height="2" rx="1" fill="white" transform="rotate(-9,17,2)"/>
          <rect x="30" y="2" width="8" height="2" rx="1" fill="white" transform="rotate(7,34,3)"/>
          <rect x="48" y="1" width="11" height="2" rx="1" fill="white" transform="rotate(-4,53,2)"/>
          <rect x="63" y="2" width="9" height="2" rx="1" fill="white" transform="rotate(10,68,3)"/>
          <rect x="6" y="36" width="68" height="10" rx="2" fill="#e74c3c" opacity="0.8"/>
          <rect x="6" y="20" width="68" height="15" rx="2" fill="white" opacity="0.9"/>
          <rect x="6" y="6" width="68" height="13" rx="2" fill="#f5deb3" opacity="0.8"/>
          <rect x="6" y="48" width="68" height="24" rx="2" fill="#f5deb3" opacity="0.8"/>
        </g>

        <!-- Coconut flakes scattered on board -->
        <rect x="45" y="150" width="12" height="2" rx="1" fill="#e0d8c8" transform="rotate(-15,51,151)"/>
        <rect x="155" y="152" width="10" height="2" rx="1" fill="#d8d0c0" transform="rotate(10,160,153)"/>
        <rect x="260" y="150" width="11" height="2" rx="1" fill="#e0d8c8" transform="rotate(-8,265,151)"/>
        <rect x="350" y="148" width="10" height="2" rx="1" fill="#d8d0c0" transform="rotate(15,355,149)"/>
        <rect x="0" y="0" width="400" height="25" fill="rgba(0,0,0,0.3)" rx="10"/>
        <text x="200" y="17" text-anchor="middle" fill="white" font-size="11" font-family="Poppins,sans-serif" font-weight="600" letter-spacing="1">🇦🇺 LAMINGTONS</text>
      </svg>
      <h3><a href="https://www.google.com/search?q=receta+lamingtons" target="_blank" onclick="event.stopPropagation()">Lamingtons</a></h3>
      <div class="details"><h4>Ingredientes:</h4><ul><li>Bizcocho</li><li>Chocolate</li><li>Coco</li></ul></div>
    </div>

  </div>
  <div class="comment-section">
    <h3>Opiniones de Oceanía</h3>
    <textarea class="comment-input" id="commentTextOceania" placeholder="Escribe aquí..."></textarea>
    <button class="comment-btn" onclick="addComment('Oceania')">Publicar</button>
    <div class="comment-list" id="listOceania"></div>
  </div>
</section>

<div id="loginModal" class="modal">
  <div class="modal-content">
    <h3>Acceso Gourmet</h3>
    <input type="email" id="emailInput" placeholder="Email">
    <input type="password" id="passInput" placeholder="Contraseña">
    <button class="comment-btn" style="width:100%" onclick="login()">Entrar</button>
    <p onclick="closeModal()" style="cursor:pointer; font-size:0.8rem; margin-top:10px;">Cerrar</p>
  </div>
</div>

<footer>© 2026 Recetario Gourmet Internacional</footer>

<script>
  let currentUser = "Invitado";
  function showSection(event, id) {
    document.querySelectorAll('.recipes-section').forEach(s => s.style.display = 'none');
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(id).style.display = 'block';
    event.target.classList.add('active');
  }
  function toggleDetails(card) {
    let d = card.querySelector('.details');
    if (d) d.style.maxHeight = d.style.maxHeight ? null : d.scrollHeight + "px";
  }
  function openModal() { document.getElementById('loginModal').style.display = 'block'; }
  function closeModal() { document.getElementById('loginModal').style.display = 'none'; }
  function login() {
    let email = document.getElementById('emailInput').value;
    if (email.includes('@')) {
      currentUser = email.split('@')[0];
      document.getElementById('userWelcome').innerText = "Hola, " + currentUser;
      document.getElementById('authBtn').style.display = 'none';
      closeModal();
    }
  }
  function addComment(section) {
    let input = document.getElementById('commentText' + section);
    let list = document.getElementById('list' + section);
    if (input.value.trim() === "") return;
    let div = document.createElement('div');
    div.className = 'comment-item';
    div.innerHTML = `<strong>${currentUser}:</strong> ${input.value}`;
    list.prepend(div);
    input.value = "";
  }
</script>
</body>
</html>

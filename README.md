# GymTrack.
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>GymTrack — Suivez vos séances en 2 clics</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300&display=swap" rel="stylesheet"/>
<style>
:root{
  --blk:#080610;
  --pur:#7F77DD;
  --pur2:#EEEDFE;
  --grn:#B8F53D;
  --wht:#f0eeff;
  --muted:#5a5480;
  --brd:#1e1a35;
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{background:var(--blk);color:var(--wht);font-family:'DM Sans',sans-serif;overflow-x:hidden}

/* BACKGROUND */
.bg-mesh{position:fixed;inset:0;z-index:0;pointer-events:none;overflow:hidden}
.bg-mesh::before{content:'';position:absolute;width:900px;height:900px;border-radius:50%;background:radial-gradient(circle,rgba(127,119,221,.18) 0%,transparent 70%);top:-300px;right:-200px;animation:drift1 12s ease-in-out infinite alternate}
.bg-mesh::after{content:'';position:absolute;width:700px;height:700px;border-radius:50%;background:radial-gradient(circle,rgba(184,245,61,.06) 0%,transparent 70%);bottom:-200px;left:-100px;animation:drift2 14s ease-in-out infinite alternate}
@keyframes drift1{to{transform:translate(60px,80px)}}
@keyframes drift2{to{transform:translate(-40px,-60px)}}

/* LAYOUT */
.wrap{position:relative;z-index:1;max-width:1100px;margin:0 auto;padding:0 24px}

/* NAV */
nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:18px 24px;display:flex;align-items:center;justify-content:space-between;background:rgba(8,6,16,.7);backdrop-filter:blur(20px);border-bottom:0.5px solid var(--brd)}
.nav-brand{display:flex;align-items:center;gap:10px;text-decoration:none}
.nav-icon{width:36px;height:36px;background:var(--pur);border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:18px}
.nav-name{font-family:'Bebas Neue',sans-serif;font-size:24px;letter-spacing:2px;color:var(--wht)}
.nav-cta{padding:10px 22px;background:var(--pur);color:#fff;border:none;border-radius:99px;font-size:14px;font-weight:600;cursor:pointer;text-decoration:none;transition:all .2s}
.nav-cta:hover{background:#9b95f0;transform:translateY(-1px)}

/* HERO */
.hero{min-height:100vh;display:flex;align-items:center;padding:100px 24px 60px;position:relative}
.hero-inner{max-width:1100px;margin:0 auto;width:100%;display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:center}
.hero-tag{display:inline-flex;align-items:center;gap:8px;background:rgba(127,119,221,.15);border:0.5px solid rgba(127,119,221,.4);border-radius:99px;padding:6px 14px;font-size:12px;color:var(--pur2);letter-spacing:.08em;text-transform:uppercase;margin-bottom:24px}
.hero-tag span{width:6px;height:6px;border-radius:50%;background:var(--grn);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.5;transform:scale(1.4)}}
.hero-title{font-family:'Bebas Neue',sans-serif;font-size:82px;line-height:.92;letter-spacing:-1px;margin-bottom:20px}
.hero-title .acc{color:var(--pur);display:block}
.hero-title .acc2{color:var(--grn);display:block}
.hero-sub{font-size:18px;color:var(--muted);font-weight:300;line-height:1.65;margin-bottom:36px;max-width:420px}
.hero-sub strong{color:var(--wht);font-weight:500}
.hero-btns{display:flex;gap:12px;flex-wrap:wrap}
.btn-primary{display:inline-flex;align-items:center;gap:10px;padding:16px 32px;background:var(--pur);color:#fff;border-radius:99px;font-size:16px;font-weight:700;text-decoration:none;transition:all .2s;box-shadow:0 8px 32px rgba(127,119,221,.35)}
.btn-primary:hover{background:#9b95f0;transform:translateY(-2px);box-shadow:0 12px 40px rgba(127,119,221,.45)}
.btn-primary .price{background:rgba(255,255,255,.2);padding:4px 10px;border-radius:99px;font-size:13px}
.btn-secondary{display:inline-flex;align-items:center;gap:8px;padding:16px 24px;border:0.5px solid var(--brd);border-radius:99px;font-size:15px;color:var(--muted);text-decoration:none;transition:all .2s}
.btn-secondary:hover{border-color:var(--pur);color:var(--wht)}

/* VIDEO */
.hero-video-wrap{position:relative}
.hero-video-frame{border-radius:20px;overflow:hidden;border:1px solid var(--brd);box-shadow:0 32px 80px rgba(0,0,0,.6);position:relative;background:#0d0a1a;aspect-ratio:9/16;max-height:580px;margin:0 auto}
.hero-video-frame iframe{width:100%;height:100%;border:none}
.hero-video-glow{position:absolute;inset:-30px;border-radius:30px;background:radial-gradient(ellipse at center,rgba(127,119,221,.12) 0%,transparent 70%);pointer-events:none;z-index:-1}

/* FEATURES */
.features{padding:100px 0}
.section-label{font-size:11px;color:var(--pur);text-transform:uppercase;letter-spacing:.12em;font-weight:600;margin-bottom:12px}
.section-title{font-family:'Bebas Neue',sans-serif;font-size:56px;line-height:1;margin-bottom:16px}
.section-sub{font-size:16px;color:var(--muted);font-weight:300;max-width:480px;line-height:1.65}
.feat-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:56px}
.feat{background:rgba(255,255,255,.03);border:0.5px solid var(--brd);border-radius:16px;padding:28px 24px;transition:all .25s;position:relative;overflow:hidden}
.feat::before{content:'';position:absolute;inset:0;background:radial-gradient(ellipse at 50% 0%,rgba(127,119,221,.08) 0%,transparent 60%);opacity:0;transition:opacity .3s}
.feat:hover{border-color:rgba(127,119,221,.35);transform:translateY(-4px)}
.feat:hover::before{opacity:1}
.feat-ico{font-size:32px;margin-bottom:16px}
.feat-title{font-size:16px;font-weight:700;margin-bottom:8px;color:var(--wht)}
.feat-desc{font-size:14px;color:var(--muted);line-height:1.6}
.feat.highlight{background:linear-gradient(135deg,rgba(127,119,221,.12),rgba(127,119,221,.04));border-color:rgba(127,119,221,.3);grid-column:span 2}

/* PRIX */
.pricing{padding:80px 0 100px}
.price-card{max-width:520px;margin:56px auto 0;background:rgba(255,255,255,.04);border:1px solid var(--brd);border-radius:24px;padding:48px 40px;text-align:center;position:relative;overflow:hidden}
.price-card::before{content:'';position:absolute;top:-60px;left:50%;transform:translateX(-50%);width:300px;height:300px;border-radius:50%;background:radial-gradient(circle,rgba(127,119,221,.12) 0%,transparent 70%)}
.price-badge{display:inline-block;background:var(--grn);color:#0a0a0a;font-size:12px;font-weight:700;padding:4px 14px;border-radius:99px;margin-bottom:20px;letter-spacing:.05em}
.price-val{font-family:'Bebas Neue',sans-serif;font-size:96px;color:var(--pur);line-height:1}
.price-period{font-size:16px;color:var(--muted);margin-bottom:32px}
.price-perks{list-style:none;text-align:left;margin-bottom:36px;display:flex;flex-direction:column;gap:12px}
.price-perks li{display:flex;align-items:center;gap:12px;font-size:15px;color:var(--wht)}
.price-perks li::before{content:'✓';width:22px;height:22px;border-radius:50%;background:rgba(184,245,61,.15);color:var(--grn);display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;flex-shrink:0}
.price-perks li.special::before{content:'★';background:rgba(127,119,221,.2);color:var(--pur2)}
.btn-pay{display:block;width:100%;padding:18px;background:var(--pur);color:#fff;border-radius:14px;font-size:18px;font-weight:700;text-decoration:none;transition:all .2s;box-shadow:0 8px 32px rgba(127,119,221,.35);margin-bottom:14px}
.btn-pay:hover{background:#9b95f0;transform:translateY(-2px);box-shadow:0 14px 40px rgba(127,119,221,.5)}
.price-note{font-size:13px;color:var(--muted)}

/* FOOTER */
footer{padding:40px 24px;border-top:0.5px solid var(--brd);display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:16px}
.footer-brand{font-family:'Bebas Neue',sans-serif;font-size:22px;letter-spacing:2px;color:var(--pur)}
.footer-note{font-size:13px;color:var(--muted)}
.footer-contact{display:flex;gap:20px}
.footer-contact a{font-size:13px;color:var(--muted);text-decoration:none;transition:color .2s}
.footer-contact a:hover{color:var(--pur2)}

/* ANIMATIONS */
.reveal{opacity:0;transform:translateY(30px);transition:opacity .7s ease,transform .7s ease}
.reveal.visible{opacity:1;transform:none}

/* RESPONSIVE */
@media(max-width:768px){
  .hero-inner{grid-template-columns:1fr;gap:40px;text-align:center}
  .hero-title{font-size:56px}
  .hero-sub{margin:0 auto 36px}
  .hero-btns{justify-content:center}
  .hero-video-frame{max-height:420px}
  .feat-grid{grid-template-columns:1fr}
  .feat.highlight{grid-column:span 1}
  .section-title{font-size:42px}
  footer{flex-direction:column;align-items:flex-start}
}
</style>
</head>
<body>

<div class="bg-mesh"></div>

<!-- NAV -->
<nav>
  <a class="nav-brand" href="#">
    <div class="nav-icon">💪</div>
    <span class="nav-name">GymTrack</span>
  </a>
  <a class="nav-cta" href="https://buy.stripe.com/7sY00k2xo22bdJy3Xb1kA06" target="_blank">Acheter — 10€</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-inner wrap">
    <div class="hero-content">
      <div class="hero-tag"><span></span>Disponible maintenant</div>
      <h1 class="hero-title">
        GYM
        <span class="acc">TRACK</span>
        <span class="acc2" style="font-size:48px;letter-spacing:0">Ton coach dans la poche.</span>
      </h1>
      <p class="hero-sub">
        Suis tes séances de sport en <strong>2 clics, sans prise de tête.</strong><br>
        Musculation, cardio, hydratation, routine, progression… tout en un.
      </p>
      <div class="hero-btns">
        <a class="btn-primary" href="https://buy.stripe.com/7sY00k2xo22bdJy3Xb1kA06" target="_blank">
          🚀 Obtenir l'app <span class="price">10€ · Accès à vie</span>
        </a>
        <a class="btn-secondary" href="#features">Voir les fonctionnalités ↓</a>
      </div>
    </div>
    <div class="hero-video-wrap reveal">
      <div class="hero-video-glow"></div>
      <div class="hero-video-frame">
        <iframe 
          src="https://www.youtube.com/embed/wdEOxOAicPE?autoplay=0&rel=0&modestbranding=1&playsinline=1" 
          title="GymTrack — Présentation"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen>
        </iframe>
      </div>
    </div>
  </div>
</section>

<!-- FEATURES -->
<section class="features" id="features">
  <div class="wrap">
    <div class="reveal">
      <div class="section-label">Fonctionnalités</div>
      <h2 class="section-title">Tout ce dont<br>tu as besoin.</h2>
      <p class="section-sub">Une seule app, conçue pour les gens sérieux qui veulent progresser sans se compliquer la vie.</p>
    </div>
    <div class="feat-grid">
      <div class="feat reveal">
        <div class="feat-ico">🏋️</div>
        <div class="feat-title">Programmes & Séances</div>
        <div class="feat-desc">Crée tes programmes, note tes séries, reps et poids pour chaque exercice. La séance reste active même en changeant d'onglet.</div>
      </div>
      <div class="feat reveal">
        <div class="feat-ico">📈</div>
        <div class="feat-title">Graphique de progression</div>
        <div class="feat-desc">Visualise l'évolution de ton poids et de ta distance séance par séance. Record, dernier résultat, évolution totale.</div>
      </div>
      <div class="feat reveal">
        <div class="feat-ico">🏃</div>
        <div class="feat-title">Cardio intégré</div>
        <div class="feat-desc">Course, vélo, natation, rameur… Sauvegarde durée, distance, vitesse et calories pour chaque session cardio.</div>
      </div>
      <div class="feat highlight reveal">
        <div class="feat-ico">⏱</div>
        <div class="feat-title">Chrono de repos intelligent</div>
        <div class="feat-desc">Un bouton flottant accessible directement depuis ta séance. Présets 1:00 à 2:30 ou durée personnalisée. S'arrête tout seul, sans bruit. Tu ne perds jamais le fil de ta séance.</div>
      </div>
      <div class="feat reveal">
        <div class="feat-ico">💧</div>
        <div class="feat-title">Suivi hydratation</div>
        <div class="feat-desc">Ajoute ou retire 0,5 L en un tap. Objectif personnalisable. Reset automatique chaque nuit à minuit.</div>
      </div>
      <div class="feat reveal">
        <div class="feat-ico">✅</div>
        <div class="feat-title">Routine quotidienne</div>
        <div class="feat-desc">Ta checklist du matin personnalisable. Remise à zéro chaque jour automatiquement.</div>
      </div>
      <div class="feat reveal">
        <div class="feat-ico">⚔️</div>
        <div class="feat-title">Quêtes sur 30 jours</div>
        <div class="feat-desc">Tableau de bord pour tracker tes objectifs jour par jour sur tout un mois. Titres modifiables.</div>
      </div>
      <div class="feat reveal">
        <div class="feat-ico">📓</div>
        <div class="feat-title">Journal personnel</div>
        <div class="feat-desc">Note tes ressentis, objectifs et réflexions. Chaque entrée est datée, modifiable et conservée indéfiniment.</div>
      </div>
      <div class="feat reveal">
        <div class="feat-ico">📋</div>
        <div class="feat-title">Historique complet</div>
        <div class="feat-desc">Retrouve toutes tes séances avec le détail des reps, poids et données cardio pour chaque exercice.</div>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing" id="pricing">
  <div class="wrap">
    <div class="reveal" style="text-align:center">
      <div class="section-label">Tarif</div>
      <h2 class="section-title">Simple et honnête.</h2>
    </div>
    <div class="price-card reveal">
      <div class="price-badge">🎯 Offre de lancement</div>
      <div class="price-val">10€</div>
      <div class="price-period">Paiement unique · Accès à vie</div>
      <ul class="price-perks">
        <li>Toutes les fonctionnalités incluses</li>
        <li>Fonctionne sur iOS & Android</li>
        <li>Données stockées localement sur ton téléphone</li>
        <li>Mises à jour incluses à vie</li>
        <li class="special">Personnalisation sur demande — tu me dis ce que tu veux, je modifie l'app pour toi</li>
      </ul>
      <a class="btn-pay" href="https://buy.stripe.com/7sY00k2xo22bdJy3Xb1kA06" target="_blank">
        💳 Payer 10€ et obtenir l'app
      </a>
      <p class="price-note">Après paiement, contacte-moi sur Instagram <strong style="color:var(--pur2)">@rmn_lns</strong> ou au <strong style="color:var(--pur2)">06 38 05 12 28</strong> pour recevoir ton lien.</p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-brand">GymTrack</div>
  <div class="footer-note">© 2025 GymTrack · Fait avec 💪</div>
  <div class="footer-contact">
    <a href="https://instagram.com/rmn_lns" target="_blank">📸 @rmn_lns</a>
    <a href="tel:0638051228">📱 06 38 05 12 28</a>
  </div>
</footer>

<script>
// Reveal on scroll
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('visible');obs.unobserve(e.target);}});
},{threshold:.12});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));
</script>
</body>
</html>

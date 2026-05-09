<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RecenStat-CI · Prototype interfaces</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,600;0,700;1,600&family=DM+Mono:wght@400;500&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
<style>
:root{--ink:#1A1A18;--ink2:#2E2E2A;--parch:#FAF8F3;--parch2:#F2EFE8;--stone:#E6E2D8;--stone2:#C8C3B5;--dust:#8C8677;--orange:#C95A1A;--orange-lt:#F5E6D8;--em:#1A6B4A;--em-lt:#D4EDE3;--em-md:#A8D5C0;--em-dk:#124D36;--serif:'Playfair Display',Georgia,serif;--sans:'Lato',sans-serif;--mono:'DM Mono',monospace}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:var(--sans);background:var(--parch);color:var(--ink)}
.tribar{height:4px;background:linear-gradient(90deg,var(--orange) 0 33.3%,var(--parch2) 33.3% 66.6%,var(--em) 66.6% 100%);position:sticky;top:0;z-index:200}
nav{background:var(--ink);position:sticky;top:4px;z-index:199;padding:0 7vw}
.nav-inner{display:flex;align-items:center;justify-content:space-between;height:54px}
.nav-logo{font-family:var(--serif);font-size:1.15rem;color:var(--parch)}
.nav-logo em{color:var(--orange-lt);font-style:italic}
.nav-links{display:flex;gap:1.8rem;list-style:none}
.nav-links a{font-size:.8rem;color:var(--stone2);text-decoration:none;letter-spacing:.03em;transition:color .15s}
.nav-links a:hover{color:var(--parch)}
.nav-cta{font-family:var(--mono);font-size:.68rem;color:var(--em-md);text-decoration:none;border:1px solid var(--em);padding:.3rem .8rem;border-radius:2px;transition:background .15s}
.nav-cta:hover{background:var(--em);color:var(--parch)}
.hero{background:var(--ink);padding:5.5rem 7vw 4.5rem;position:relative;overflow:hidden}
.hero-deco{position:absolute;right:4vw;top:50%;transform:translateY(-50%);font-family:var(--serif);font-size:clamp(10rem,18vw,18rem);line-height:1;color:transparent;-webkit-text-stroke:1px rgba(255,255,255,.04);user-select:none;pointer-events:none}
.hero-content{position:relative;z-index:1;max-width:680px}
.hero-eyebrow{font-family:var(--mono);font-size:.68rem;letter-spacing:.2em;text-transform:uppercase;color:var(--em-md);display:flex;align-items:center;gap:.6rem;margin-bottom:1.2rem}
.hero-eyebrow::after{content:'';flex:1;max-width:32px;height:1px;background:var(--em)}
h1{font-family:var(--serif);font-size:clamp(2.8rem,6vw,5rem);line-height:1.04;color:var(--parch);margin-bottom:1rem}
h1 em{color:var(--orange-lt);font-style:italic}
.hero-sub{font-size:1rem;font-weight:300;color:var(--stone2);line-height:1.8;max-width:520px;margin-bottom:2rem}
.hero-pills{display:flex;flex-wrap:wrap;gap:.45rem;margin-bottom:2.4rem}
.pill{font-family:var(--mono);font-size:.66rem;padding:.25rem .65rem;border:1px solid rgba(255,255,255,.12);color:var(--dust)}
.hero-btns{display:flex;gap:.8rem;flex-wrap:wrap}
.btn{display:inline-flex;align-items:center;gap:.5rem;padding:.75rem 1.5rem;font-family:var(--sans);font-size:.86rem;font-weight:700;letter-spacing:.04em;text-decoration:none;border-radius:3px;transition:filter .18s,transform .12s;cursor:pointer;border:none}
.btn:hover{filter:brightness(.9);transform:translateY(-1px)}
.btn-em{background:var(--em);color:#fff}
.btn-out{background:transparent;border:1.5px solid rgba(255,255,255,.2);color:var(--stone2)}
.btn-out:hover{border-color:rgba(255,255,255,.5);color:var(--parch);filter:none}
section{padding:5rem 7vw}
.sec-eyebrow{font-family:var(--mono);font-size:.67rem;letter-spacing:.2em;text-transform:uppercase;color:var(--orange);margin-bottom:.6rem}
h2{font-family:var(--serif);font-size:clamp(1.8rem,3vw,2.6rem);color:var(--ink);margin-bottom:.6rem;line-height:1.12}
.sec-lead{font-size:.95rem;color:var(--dust);font-weight:300;line-height:1.75;max-width:580px;margin-bottom:3rem}
.screens-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:1.5rem}
.screens-grid.mobile-grid{grid-template-columns:repeat(auto-fill,minmax(220px,1fr))}
.screen-card{background:var(--parch);border:1px solid var(--stone);border-radius:6px;overflow:hidden;cursor:pointer;transition:box-shadow .2s,transform .18s,border-color .18s;box-shadow:0 1px 4px rgba(0,0,0,.06)}
.screen-card:hover{box-shadow:0 8px 32px rgba(0,0,0,.12);transform:translateY(-3px);border-color:var(--stone2)}
.screen-card:hover .card-thumb img{transform:scale(1.02)}
.card-thumb{overflow:hidden;background:var(--stone);border-bottom:1px solid var(--stone);aspect-ratio:16/9}
.screens-grid.mobile-grid .card-thumb{aspect-ratio:9/16}
.card-thumb img{width:100%;height:100%;object-fit:cover;object-position:top;transition:transform .3s;display:block}
.card-info{padding:.9rem 1rem}
.card-num{font-family:var(--mono);font-size:.62rem;color:var(--stone2);margin-bottom:.25rem;letter-spacing:.06em}
.card-name{font-size:.88rem;font-weight:700;color:var(--ink);margin-bottom:.2rem}
.card-desc{font-size:.76rem;color:var(--dust);font-weight:300;line-height:1.55}
.card-tag{display:inline-flex;margin-top:.55rem;font-family:var(--mono);font-size:.6rem;padding:.18rem .52rem;border-radius:2px}
.tag-admin{background:var(--orange-lt);color:var(--orange)}
.tag-mobile{background:var(--em-lt);color:var(--em-dk)}
.tag-modal{background:var(--stone);color:var(--dust)}
.sep{height:1px;background:var(--stone);margin:0 7vw}
.lightbox{position:fixed;inset:0;background:rgba(15,15,12,.92);z-index:500;display:none;align-items:center;justify-content:center;padding:2rem}
.lightbox.open{display:flex}
.lb-inner{position:relative;max-width:1200px;width:100%;animation:lbIn .22s ease}
@keyframes lbIn{from{opacity:0;transform:scale(.95) translateY(12px)}to{opacity:1;transform:scale(1) translateY(0)}}
.lb-img{width:100%;border-radius:4px;box-shadow:0 24px 80px rgba(0,0,0,.6);display:block}
.lb-close{position:absolute;top:-2.5rem;right:0;background:none;border:none;color:rgba(255,255,255,.6);font-size:1.5rem;cursor:pointer;padding:.3rem .6rem;transition:color .15s}
.lb-close:hover{color:#fff}
.lb-nav{position:absolute;top:50%;transform:translateY(-50%);background:rgba(0,0,0,.5);border:none;color:#fff;font-size:1.5rem;width:44px;height:44px;border-radius:50%;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:background .15s}
.lb-nav:hover{background:rgba(0,0,0,.8)}
.lb-prev{left:-56px}.lb-next{right:-56px}
.lb-caption{text-align:center;margin-top:1rem;font-size:.82rem;color:rgba(255,255,255,.5);font-family:var(--mono)}
footer{background:var(--ink);padding:2.5rem 7vw;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:1rem}
.footer-logo{font-family:var(--serif);font-size:1.3rem;color:var(--parch)}
.footer-logo em{color:var(--orange-lt);font-style:italic}
.footer-meta{font-family:var(--mono);font-size:.65rem;color:var(--dust);text-align:right;line-height:1.9}
.footer-meta a{color:var(--em-md);text-decoration:none}
.footer-meta a:hover{color:var(--parch)}
.footer-tribar{width:100%;height:3px;margin-top:1.5rem;background:linear-gradient(90deg,var(--orange) 0 33.3%,var(--parch2) 33.3% 66.6%,var(--em) 66.6% 100%)}
@media(max-width:700px){nav .nav-links{display:none}.lb-prev{left:-10px}.lb-next{right:-10px}}
</style>
</head>
<body>
<div class="tribar"></div>
<nav><div class="nav-inner">
  <span class="nav-logo">Recen<em>Stat</em>-CI</span>
  <ul class="nav-links">
    <li><a href="#admin">Administrateur</a></li>
    <li><a href="#mobile">Enquêteur</a></li>
  </ul>
  <a href="recenstat_prototype.html" target="_blank" class="nav-cta">→ Prototype interactif</a>
</div></nav>

<div class="hero">
  <div class="hero-deco">P</div>
  <div class="hero-content">
    <div class="hero-eyebrow">Prototype UI · ENSEA ISE 2B</div>
    <h1>Interfaces<br><em>RecenStat-CI</em></h1>
    <p class="hero-sub">Captures de toutes les interfaces de l'application — tableau de bord administrateur, statistiques, supervision des collectes, et interface mobile enquêteur.</p>
    <div class="hero-pills">
      <span class="pill">15 interfaces</span>
      <span class="pill">2 profils</span>
      <span class="pill">Mobile-first</span>
      <span class="pill">Palette ivoirienne</span>
    </div>
    <div class="hero-btns">
      <a href="recenstat_prototype.html" target="_blank" class="btn btn-em">→ Prototype interactif</a>
      <a href="https://www.drawdb.app/editor?shareId=5804f3a57d57e5bdc9c9735251b2ca00" target="_blank" class="btn btn-out">Diagramme DrawDB</a>
    </div>
  </div>
</div>

<section id="admin">
  <div class="sec-eyebrow">Interface administrateur &amp; superviseur</div>
  <h2>Tableau de bord et gestion</h2>
  <p class="sec-lead">L'interface administrateur couvre la supervision des collectes, les statistiques sociodémographiques, la gestion des utilisateurs et le découpage territorial.</p>
  <div class="screens-grid">
    <div class="screen-card" onclick="openLb(0)"><div class="card-thumb"><img src="01_login.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">01 / 15</div><div class="card-name">Page de connexion</div><div class="card-desc">Accès par rôle — Administrateur ou Enquêteur. Barre tricolore.</div><span class="card-tag tag-admin">Commun</span></div></div>
    <div class="screen-card" onclick="openLb(1)"><div class="card-thumb"><img src="02_admin_dashboard.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">02 / 15</div><div class="card-name">Tableau de bord global</div><div class="card-desc">KPIs temps réel, taux de couverture par ZD, activité récente.</div><span class="card-tag tag-admin">Administrateur</span></div></div>
    <div class="screen-card" onclick="openLb(2)"><div class="card-thumb"><img src="03_admin_stats.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">03 / 15</div><div class="card-name">Statistiques sociodémographiques</div><div class="card-desc">Pyramide des âges, répartition des activités, scolarisation par ZD.</div><span class="card-tag tag-admin">Administrateur</span></div></div>
    <div class="screen-card" onclick="openLb(3)"><div class="card-thumb"><img src="04_admin_supervision.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">04 / 15</div><div class="card-name">Contrôle des collectes</div><div class="card-desc">Fiches soumises — Valider ou Renvoyer avec observations.</div><span class="card-tag tag-admin">Superviseur</span></div></div>
    <div class="screen-card" onclick="openLb(4)"><div class="card-thumb"><img src="05_admin_users.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">05 / 15</div><div class="card-name">Gestion des utilisateurs</div><div class="card-desc">Comptes, rôles, ZD affectée, toggle actif/inactif.</div><span class="card-tag tag-admin">Administrateur</span></div></div>
    <div class="screen-card" onclick="openLb(5)"><div class="card-thumb"><img src="06_admin_affectations.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">06 / 15</div><div class="card-name">Affectations ZD</div><div class="card-desc">Répartition des enquêteurs sur les ZD avec barres de progression.</div><span class="card-tag tag-admin">Administrateur</span></div></div>
    <div class="screen-card" onclick="openLb(6)"><div class="card-thumb"><img src="07_admin_territoire.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">07 / 15</div><div class="card-name">Territoire</div><div class="card-desc">Arbre du découpage administratif cliquable avec détail ZD.</div><span class="card-tag tag-admin">Administrateur</span></div></div>
    <div class="screen-card" onclick="openLb(7)"><div class="card-thumb"><img src="08_admin_export.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">08 / 15</div><div class="card-name">Exportation</div><div class="card-desc">Export CSV, Excel et rapport PDF. Historique des exports.</div><span class="card-tag tag-admin">Administrateur</span></div></div>
    <div class="screen-card" onclick="openLb(8)"><div class="card-thumb"><img src="09_modal_valider.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">09 / 15</div><div class="card-name">Modale — Validation</div><div class="card-desc">Confirmation avant validation définitive et irréversible.</div><span class="card-tag tag-modal">Modale</span></div></div>
    <div class="screen-card" onclick="openLb(9)"><div class="card-thumb"><img src="10_modal_renvoyer.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">10 / 15</div><div class="card-name">Modale — Renvoi en correction</div><div class="card-desc">Observations transmises à l'enquêteur pour correction.</div><span class="card-tag tag-modal">Modale</span></div></div>
  </div>
</section>

<div class="sep"></div>

<section id="mobile" style="background:var(--parch2)">
  <div class="sec-eyebrow">Interface enquêteur · Mobile</div>
  <h2>Collecte terrain</h2>
  <p class="sec-lead">Conçue pour smartphone depuis le terrain. Navigation simple, formulaires à grandes zones tactiles, code ménage généré automatiquement.</p>
  <div class="screens-grid mobile-grid">
    <div class="screen-card" onclick="openLb(10)"><div class="card-thumb"><img src="11_mobile_accueil.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">11 / 15</div><div class="card-name">Accueil enquêteur</div><div class="card-desc">ZD affectées avec progression. Activité du jour.</div><span class="card-tag tag-mobile">Enquêteur</span></div></div>
    <div class="screen-card" onclick="openLb(11)"><div class="card-thumb"><img src="12_mobile_zd_list.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">12 / 15</div><div class="card-name">Liste des ménages</div><div class="card-desc">Badges de statut. Recherche et bouton FAB.</div><span class="card-tag tag-mobile">Enquêteur</span></div></div>
    <div class="screen-card" onclick="openLb(12)"><div class="card-thumb"><img src="13_mobile_fiche.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">13 / 15</div><div class="card-name">Fiche ménage</div><div class="card-desc">Membres avec âge calculé. Historique des passages.</div><span class="card-tag tag-mobile">Enquêteur</span></div></div>
    <div class="screen-card" onclick="openLb(13)"><div class="card-thumb"><img src="14_mobile_form_logement.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">14 / 15</div><div class="card-name">Formulaire — Logement</div><div class="card-desc">Sélecteurs tactiles pour matériaux, eau et toilettes.</div><span class="card-tag tag-mobile">Enquêteur</span></div></div>
    <div class="screen-card" onclick="openLb(14)"><div class="card-thumb"><img src="15_mobile_form_individu.png" alt="" loading="lazy"></div><div class="card-info"><div class="card-num">15 / 15</div><div class="card-name">Formulaire — Individu</div><div class="card-desc">Date de naissance, instruction, activité. Code ménage auto-généré.</div><span class="card-tag tag-mobile">Enquêteur</span></div></div>
  </div>
</section>

<footer>
  <div>
    <div class="footer-logo">Recen<em>Stat</em>-CI</div>
    <div style="font-family:var(--mono);font-size:.62rem;color:var(--dust);margin-top:.3rem">Prototype UI · ENSEA Abidjan · ISE 2B · 2024–2025</div>
    <div class="footer-tribar"></div>
  </div>
  <div class="footer-meta">
    <div>Prototype → <a href="recenstat_prototype.html" target="_blank">interactif</a></div>
    <div>Diagramme → <a href="https://www.drawdb.app/editor?shareId=5804f3a57d57e5bdc9c9735251b2ca00" target="_blank">DrawDB</a></div>
    <div>MCD → <a href="index.html">page modélisation</a></div>
  </div>
</footer>

<div class="lightbox" id="lb" onclick="if(event.target===this)closeLb()">
  <div class="lb-inner">
    <button class="lb-close" onclick="closeLb()">✕</button>
    <button class="lb-nav lb-prev" onclick="lbNav(-1)">‹</button>
    <button class="lb-nav lb-next" onclick="lbNav(1)">›</button>
    <img class="lb-img" id="lb-img" src="" alt="">
    <div class="lb-caption" id="lb-cap"></div>
  </div>
</div>

<script>
const S=[
  {src:"01_login.png",name:"01 · Connexion"},
  {src:"02_admin_dashboard.png",name:"02 · Tableau de bord"},
  {src:"03_admin_stats.png",name:"03 · Statistiques sociodémographiques"},
  {src:"04_admin_supervision.png",name:"04 · Contrôle des collectes"},
  {src:"05_admin_users.png",name:"05 · Utilisateurs"},
  {src:"06_admin_affectations.png",name:"06 · Affectations ZD"},
  {src:"07_admin_territoire.png",name:"07 · Territoire"},
  {src:"08_admin_export.png",name:"08 · Exportation"},
  {src:"09_modal_valider.png",name:"09 · Modale validation"},
  {src:"10_modal_renvoyer.png",name:"10 · Modale renvoi"},
  {src:"11_mobile_accueil.png",name:"11 · Accueil enquêteur"},
  {src:"12_mobile_zd_list.png",name:"12 · Liste ménages"},
  {src:"13_mobile_fiche.png",name:"13 · Fiche ménage"},
  {src:"14_mobile_form_logement.png",name:"14 · Formulaire logement"},
  {src:"15_mobile_form_individu.png",name:"15 · Formulaire individu"},
];
let cur=0;
function openLb(i){cur=i;document.getElementById("lb-img").src=S[i].src;document.getElementById("lb-cap").textContent=S[i].name+" · "+(i+1)+" / "+S.length;document.getElementById("lb").classList.add("open");document.body.style.overflow="hidden"}
function closeLb(){document.getElementById("lb").classList.remove("open");document.body.style.overflow=""}
function lbNav(d){cur=(cur+d+S.length)%S.length;document.getElementById("lb-img").src=S[cur].src;document.getElementById("lb-cap").textContent=S[cur].name+" · "+(cur+1)+" / "+S.length}
document.addEventListener("keydown",e=>{if(!document.getElementById("lb").classList.contains("open"))return;if(e.key==="ArrowRight")lbNav(1);if(e.key==="ArrowLeft")lbNav(-1);if(e.key==="Escape")closeLb()});
</script>
</body>
</html>

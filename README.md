<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>MacNGo VTC – Chauffeur Privé Premium</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="MacNGo VTC – Service chauffeur privé haut de gamme. Réservez en ligne rapidement et facilement.">

<link rel="icon" type="image/svg+xml" href="macngo-logo.svg">

<style>
body{margin:0;font-family:Arial,sans-serif;background:#0b0b0b;color:#fff;line-height:1.5;transition:background .3s}
a{text-decoration:none;color:inherit}
header{background:#000;padding:25px 0;text-align:center;border-bottom:2px solid gold;transition:all .3s}
header img{width:220px;margin-bottom:6px;filter:drop-shadow(0 0 10px rgba(255,215,0,.7));transition:all .3s}
header img:hover{transform:scale(1.05) rotate(-1deg);}
header .info{color:#fff;font-size:14px;margin-top:4px;opacity:.85;transition:opacity .3s}
header .info:hover{opacity:1}
.container{width:90%;max-width:620px;margin:20px auto;background:#141414;padding:30px;border-radius:12px;box-shadow:0 0 25px rgba(255,215,0,.15);transition:all .3s}
h2{text-align:center;color:gold;margin:10px 0 20px;font-size:24px;letter-spacing:1px;text-shadow:0 0 8px rgba(255,215,0,.4);animation:fadeInDown .6s ease-out;display:flex;align-items:center;justify-content:center;gap:10px}
input,textarea{width:100%;padding:12px;margin-top:10px;border-radius:6px;border:none;background:#222;color:#fff;font-size:16px;transition:all .3s;opacity:0;animation:fadeInUp .6s ease-out forwards}
input:focus,textarea:focus{outline:2px solid gold;transform:scale(1.02)}
input:nth-child(1),textarea:nth-child(1){animation-delay:.2s}
input:nth-child(2){animation-delay:.3s}
input:nth-child(3){animation-delay:.4s}
input:nth-child(4){animation-delay:.5s}
input:nth-child(5){animation-delay:.6s}
input:nth-child(6){animation-delay:.7s}
input:nth-child(7){animation-delay:.8s}
textarea:nth-child(8){animation-delay:.9s}
button{width:100%;padding:14px;margin-top:15px;background:gold;color:#000;font-size:18px;border:none;border-radius:8px;cursor:pointer;font-weight:bold;transition:all .3s;text-shadow:0 0 4px rgba(0,0,0,.5);display:flex;align-items:center;justify-content:center;gap:8px}
button:hover{filter:brightness(1.15);transform:scale(1.03);box-shadow:0 0 15px gold}
.call-btn{background:#00ff62;color:#000;margin-top:10px;font-size:20px;display:flex;align-items:center;justify-content:center;gap:8px}
.price-box{background:#000;border:1px solid gold;padding:15px;margin-top:15px;border-radius:10px;display:none;font-size:18px;text-align:center;animation:fadeIn .6s ease-out}
@keyframes fadeInUp{0%{opacity:0;transform:translateY(20px)}100%{opacity:1;transform:translateY(0)}}
@keyframes fadeInDown{0%{opacity:0;transform:translateY(-20px)}100%{opacity:1;transform:translateY(0)}}
@keyframes fadeIn{0%{opacity:0}100%{opacity:1}}
@media(max-width:480px){header img{width:180px}.container{padding:20px}h2{font-size:20px}input,textarea,button{font-size:16px;padding:10px}.call-btn{font-size:18px}}
</style>
</head>

<body>

<header>
  <img src="macngo-logo.svg" alt="Logo MacNGo">
  <div class="info">MacNGo VTC – Numéro VTC : 05725012701</div>
</header>

<div class="container">
  <h2>
    <!-- Icon voiture -->
    <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="gold" stroke="gold" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l2-4h14l2 4v6h-2a2 2 0 0 1-4 0h-4a2 2 0 0 1-4 0H3v-6z"/><circle cx="6.5" cy="18.5" r="2.5"/><circle cx="17.5" cy="18.5" r="2.5"/></svg>
    Réservation Chauffeur Premium
  </h2>

  <form id="bookingForm">
    <input type="text" id="client" placeholder="Nom complet" required>
    <input type="text" id="phone" placeholder="Numéro de téléphone" required>
    <input type="text" id="pickup" placeholder="Adresse de départ" required>
    <input type="text" id="dropoff" placeholder="Adresse de destination" required>
    <input type="number" id="distance" placeholder="Distance estimée en km" required>
    <input type="number" id="waiting" placeholder="Minutes d’attente (si applicable)">
    <input type="datetime-local" id="datetime" required>
    <textarea id="notes" placeholder="Informations supplémentaires (optionnel)"></textarea>

    <button type="button" onclick="calculatePrice()">
      <!-- Icon calcul -->
      <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="none" stroke="black" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12" y2="16"/></svg>
      Calculer le prix
    </button>

    <div id="priceBox" class="price-box"></div>

    <button type="button" onclick="sendWhatsApp()">
      <!-- Icon WhatsApp -->
      <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="black" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21.05 11.38a9 9 0 1 0-15.99 5.38L3 21l4.38-1.15a9 9 0 0 0 13.67-8.47z"/><path d="M16.5 12a1.5 1.5 0 0 1-1.5 1.5H12v-3h3a1.5 1.5 0 0 1 1.5 1.5z"/></svg>
      Envoyer WhatsApp
    </button>

    <a href="tel:+335725012701">
      <button type="button" class="call-btn">
        <!-- Icon téléphone -->
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="none" stroke="black" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.86 19.86 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6A19.86 19.86 0 0 1 2.08 4.18 2 2 0 0 1 4 2h3a2 2 0 0 1 2 1.72c.12.81.35 1.61.67 2.38a2 2 0 0 1-.45 2.11L8.09 8.91a16 16 0 0 0 6 6l1.68-1.14a2 2 0 0 1 2.11-.45c.77.32 1.57.55 2.38.67A2 2 0 0 1 22 16.92z"/></svg>
        Appeler maintenant
      </button>
    </a>
  </form>
</div>

<script>
const baseFare = 5;
const pricePerKm = 1.70;
const waitPerMin = 0.30;

function calculatePrice(){
  const distance=parseFloat(document.getElementById("distance").value)
  const waiting=parseFloat(document.getElementById("waiting").value)||0
  let price=baseFare+(distance*pricePerKm)+(waiting*waitPerMin)
  const box=document.getElementById("priceBox")
  box.style.display="block"
  box.innerHTML="<b>Prix estimé :</b> "+price.toFixed(2)+" € (Premium)"
}

function sendWhatsApp(){
  const client=document.getElementById("client").value
  const phone=document.getElementById("phone").value
  const pickup=document.getElementById("pickup").value
  const dropoff=document.getElementById("dropoff").value
  const distance=document.getElementById("distance").value
  const waiting=document.getElementById("waiting").value
  const datetime=document.getElementById("datetime").value
  const notes=document.getElementById("notes").value

  const message="🚖 *Réservation – MacNGo Premium* %0A%0A"+
  "*Client :* "+client+"%0A"+
  "*Téléphone :* "+phone+"%0A"+
  "*Départ :* "+pickup+"%0A"+
  "*Destination :* "+dropoff+"%0A"+
  "*Distance :* "+distance+" km%0A"+
  "*Attente :* "+waiting+" min%0A"+
  "*Date/Heure :* "+datetime+"%0A"+
  "*Infos :* "+notes+"%0A%0A"+
  "Merci d’avoir choisi *MacNGo Premium* ✨"

  const whatsappNumber="33753617563"
  window.open(`https://wa.me/${whatsappNumber}?text=${message}`,"_blank")
}
</script>

</body>
</html>


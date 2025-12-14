<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Confitures artisanales — Commande</title>
  <style>
    body{font-family:Arial,Helvetica,sans-serif;margin:0;background:#f7f7f7;color:#222}
    header{padding:22px 16px;background:#fff;border-bottom:1px solid #e7e7e7}
    .wrap{max-width:980px;margin:0 auto}
    h1{margin:0 0 6px;font-size:22px}
    .sub{margin:0;color:#555}
    main{padding:18px 16px}
    .grid{display:grid;grid-template-columns:1fr;gap:14px}
    @media(min-width:900px){.grid{grid-template-columns:1.2fr .8fr}}
    .card{background:#fff;border:1px solid #e7e7e7;border-radius:14px;padding:16px;box-shadow:0 1px 6px rgba(0,0,0,.04)}
    label{display:block;font-weight:600;margin:10px 0 6px}
    input,select,textarea{width:100%;padding:10px;border:1px solid #dcdcdc;border-radius:10px;font-size:14px}
    textarea{min-height:86px}
    .row{display:grid;grid-template-columns:1fr;gap:10px}
    @media(min-width:650px){.row{grid-template-columns:1fr 1fr}}
    .btn{display:inline-block;width:100%;padding:12px 14px;border:0;border-radius:12px;font-weight:700;font-size:15px;cursor:pointer}
    .btn-primary{background:#111;color:#fff}
    .btn-secondary{background:#fff;color:#111;border:1px solid #dcdcdc}
    .muted{color:#666;font-size:13px;line-height:1.35}
    .price{font-size:18px;font-weight:800}
    .pill{display:inline-block;background:#f0f0f0;border-radius:999px;padding:6px 10px;font-size:12px;margin:6px 6px 0 0}
    .split{display:flex;gap:10px;flex-wrap:wrap}
    .hr{height:1px;background:#eee;margin:14px 0}
    .qr{width:180px;height:180px;border:1px solid #e7e7e7;border-radius:12px;display:flex;align-items:center;justify-content:center;background:#fafafa;overflow:hidden}
    .qr img{width:100%;height:100%;object-fit:contain}
    footer{padding:18px 16px;color:#666;font-size:12px}
  </style>
</head>

<body>
<header>
  <div class="wrap">
    <h1>Confitures artisanales solidaires</h1>
    <p class="sub">Une initiative de soutien en faveur des personnes en situation de vulnérabilité au sein de notre communauté.</p>
  </div>
</header>

<main class="wrap">
  <div class="grid">
    <!-- PRODUIT + COMMANDE -->
    <section class="card">
      <h2 style="margin:0 0 8px;font-size:18px;">Commander</h2>
      <p class="muted" style="margin-top:0">
        Choisissez vos saveurs, la quantité, puis cliquez sur <b>Commander</b>.  
        Vous recevrez une confirmation et les modalités de récupération/livraison.
      </p>

      <div class="split">
        <span class="pill">30 g</span>
        <span class="pill">Confiture artisanale</span>
        <span class="pill">Fait maison</span>
      </div>

      <div class="hr"></div>

      <div class="row">
        <div>
          <label for="saveur">Saveur</label>
          <select id="saveur">
            <option value="Ananas">Ananas</option>
            <option value="Papaye">Papaye</option>
            <option value="Kaki">Kaki</option>
            <option value="Pamplemousse">Pamplemousse</option>
          </select>
        </div>
        <div>
          <label for="qty">Quantité</label>
          <input id="qty" type="number" min="1" value="1" />
        </div>
      </div>

      <div class="row">
        <div>
          <label for="prix">Prix unitaire (CAD) — modifiable</label>
          <input id="prix" type="number" min="0" step="0.01" value="3.00" />
          <p class="muted" style="margin:6px 0 0">Mets ici ton prix réel (ex. 3.00, 4.00, etc.).</p>
        </div>
        <div>
          <label>Total</label>
          <div class="price" id="total">$0.00</div>
          <p class="muted" style="margin:6px 0 0">Total = quantité × prix unitaire.</p>
        </div>
      </div>

      <div class="hr"></div>

      <h3 style="margin:0 0 8px;font-size:16px;">Coordonnées</h3>
      <div class="row">
        <div>
          <label for="nom">Nom</label>
          <input id="nom" placeholder="Votre nom" />
        </div>
        <div>
          <label for="tel">Téléphone</label>
          <input id="tel" placeholder="Ex. 514-555-1234" />
        </div>
      </div>

      <label for="note">Note (facultatif)</label>
      <textarea id="note" placeholder="Ex. Livraison / ramassage, préférences, etc."></textarea>

      <div class="row" style="margin-top:12px">
        <button class="btn btn-primary" id="btnCommander">Commander (WhatsApp)</button>
        <button class="btn btn-secondary" id="btnEmail">Commander (Email)</button>
      </div>

      <p class="muted" style="margin:10px 0 0">
        * Les boutons ci-dessus envoient une commande préremplie.  
        Tu peux changer le numéro WhatsApp et l’email dans le code.
      </p>
    </section>

    <!-- PAIEMENT -->
    <aside class="card">
      <h2 style="margin:0 0 8px;font-size:18px;">Paiement</h2>
      <p class="muted" style="margin-top:0">
        Paiement accepté par <b>Interac e-Transfer</b> (banques canadiennes).
      </p>

      <div class="hr"></div>

      <p style="margin:0"><b>Adresse de paiement :</b><br><span id="payEmail">matoune@fastmail.fm</span></p>

      <div class="hr"></div>

      <p class="muted" style="margin:0 0 10px">
        Veuillez indiquer :<br>
        📝 <b>Motif</b> : Confiture artisanale<br>
        🔐 <b>Question</b> : Donation<br>
        🔑 <b>Réponse</b> : Merci
      </p>

      <div class="row">
        <div class="qr">
          <!-- Remplace le src par le lien de ton QR code paiement (image) -->
          <img src="qr_paiement_interac.png" alt="QR code paiement Interac" />
        </div>
        <div class="muted">
          <p style="margin-top:0">
            Scannez le QR code pour ouvrir l’email de paiement, puis envoyez le virement Interac.
          </p>
          <button class="btn btn-secondary" id="btnOuvrirEmail">Ouvrir l’email de paiement</button>
        </div>
      </div>

      <div class="hr"></div>

      <h3 style="margin:0 0 8px;font-size:16px;">QR code commande</h3>
      <div class="qr">
        <!-- Remplace le src par le lien de ton QR code commande (image) -->
        <img src="qr_commande.png" alt="QR code commande" />
      </div>
      <p class="muted" style="margin:10px 0 0">Scannez pour ouvrir cette page de commande.</p>
    </aside>
  </div>
</main>

<footer class="wrap">
  <div class="card" style="background:#fff">
    <b>Note :</b> Cette page est conçue pour être simple, claire et professionnelle.  
    Si tu veux, je peux te la transformer en vraie boutique (paiement Stripe/Square, inventaire, reçus, etc.).
  </div>
</footer>

<script>
  // ====== CONFIG (à personnaliser) ======
  const PAY_EMAIL = "matoune@fastmail.fm";
  const WHATSAPP_NUMBER = "15145551234"; // format international sans + (ex: 15145551234)
  const ORDER_EMAIL = "matoune@fastmail.fm";

  // =====================================
  const elSaveur = document.getElementById("saveur");
  const elQty = document.getElementById("qty");
  const elPrix = document.getElementById("prix");
  const elTotal = document.getElementById("total");
  const elNom = document.getElementById("nom");
  const elTel = document.getElementById("tel");
  const elNote = document.getElementById("note");
  document.getElementById("payEmail").textContent = PAY_EMAIL;

  function calcTotal(){
    const q = Math.max(1, Number(elQty.value || 1));
    const p = Math.max(0, Number(elPrix.value || 0));
    const t = q * p;
    elTotal.textContent = t.toLocaleString("fr-CA",{style:"currency",currency:"CAD"});
    return t;
  }
  elQty.addEventListener("input", calcTotal);
  elPrix.addEventListener("input", calcTotal);
  calcTotal();

  function buildMessage(){
    const t = calcTotal();
    const lines = [
      "Bonjour,",
      "Je souhaite commander des confitures artisanales.",
      "",
      `Saveur : ${elSaveur.value}`,
      `Quantité : ${elQty.value}`,
      `Prix unitaire : ${Number(elPrix.value).toFixed(2)} CAD`,
      `Total estimé : ${t.toFixed(2)} CAD`,
      "",
      `Nom : ${elNom.value || "-"}`,
      `Téléphone : ${elTel.value || "-"}`,
      `Note : ${elNote.value || "-"}`,
      "",
      "Merci !"
    ];
    return lines.join("\n");
  }

  document.getElementById("btnCommander").addEventListener("click", ()=>{
    const msg = encodeURIComponent(buildMessage());
    const url = `https://wa.me/${WHATSAPP_NUMBER}?text=${msg}`;
    window.open(url, "_blank");
  });

  document.getElementById("btnEmail").addEventListener("click", ()=>{
    const subject = encodeURIComponent("Commande — Confiture artisanale");
    const body = encodeURIComponent(buildMessage());
    window.location.href = `mailto:${ORDER_EMAIL}?subject=${subject}&body=${body}`;
  });

  document.getElementById("btnOuvrirEmail").addEventListener("click", ()=>{
    window.location.href = `mailto:${PAY_EMAIL}`;
  });
</script>
</body>
</html>

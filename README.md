# Shinobie-party
Shinobi Private Party – House Tour &amp; Dinner Join Shinobi for an exclusive evening! Enjoy a private house tour, meet Shinobi up close, and savor an intimate dinner with select guests. Only a few spots available—$5000 per 

<!-- Save this as shinobi-party.html or index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Shinobi Private Party</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background: linear-gradient(to bottom right, #111, #1a1a1a);
      color: #fff;
      text-align: center;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #e91e63;
      padding: 30px;
      font-size: 2em;
      font-weight: bold;
    }
    section {
      margin: 40px auto;
      max-width: 600px;
      background-color: #222;
      padding: 30px;
      border-radius: 15px;
    }
    input[type=number] {
      padding: 10px;
      font-size: 16px;
      width: 60px;
      margin-left: 10px;
    }
    button {
      margin-top: 20px;
      padding: 12px 25px;
      font-size: 18px;
      background-color: #e91e63;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      color: #fff;
    }
    button:hover {
      background-color: #d81b60;
    }
    #qr {
      margin-top: 25px;
    }
    p {
      font-size: 1.2em;
    }
  </style>
</head>
<body>

<header>Shinobi Private Party</header>

<section>
  <h2>Get Your Exclusive Ticket</h2>
  <p>Date: 20 Feb 2026 | Location: Secret Venue</p>
  <p>Join Shinobi for an exclusive house tour and intimate dinner with select guests.</p>

  <label for="tickets">Number of tickets:</label>
  <input type="number" id="tickets" min="1" max="10" value="1">

  <button onclick="generatePayment()">Pay with Bitcoin</button>

  <div id="qr"></div>
</section>

<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<script>
function generatePayment() {
    const tickets = parseInt(document.getElementById('tickets').value);
    const priceUSD = 5000; // $5000 per ticket
    const totalUSD = tickets * priceUSD;

    // Example BTC conversion (update manually to current BTC rate)
    const btcRate = 25000; // $25,000 per BTC (example)
    const totalBTC = (totalUSD / btcRate).toFixed(6);

    // Bitcoin address
    const btcAddress = 'your-bitcoin-address-here';
    const bitcoinURI = `bitcoin:${btcAddress}?amount=${totalBTC}`;

    // Clear previous QR code
    document.getElementById('qr').innerHTML = '';
    // Generate QR code
    new QRCode(document.getElementById('qr'), {
        text: bitcoinURI,
        width: 200,
        height: 200
    });

    // Show payment info
    document.getElementById('qr').innerHTML += `
      <p>Total: $${totalUSD} → ${totalBTC} BTC</p>
      <p>Send BTC to:<br>${btcAddress}</p>
    `;
}
</script>

</body>
</html>

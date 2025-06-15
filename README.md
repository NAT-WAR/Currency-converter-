<!DOCTYPE html>
<html>
<head>
  <title>Currency Converter</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 50px;
      text-align: center;
    }
    input, select {
      padding: 10px;
      margin: 10px;
      font-size: 16px;
    }
    #result {
      margin-top: 20px;
      font-size: 20px;
    }
  </style>
</head>
<body>

  <h1>Currency Converter</h1>

  <input type="number" id="amount" placeholder="Enter amount" />
  
  <select id="from">
    <option value="USD">USD</option>
    <option value="INR">INR</option>
    <option value="EUR">EUR</option>
  </select>

  <span>to</span>

  <select id="to">
    <option value="INR">INR</option>
    <option value="USD">USD</option>
    <option value="EUR">EUR</option>
  </select>

  <br>
  <button onclick="convertCurrency()">Convert</button>

  <div id="result"></div>

  <script>
    const exchangeRates = {
      USD: { INR: 83.2, EUR: 0.92 },
      INR: { USD: 0.012, EUR: 0.011 },
      EUR: { USD: 1.09, INR: 90.5 }
    };

    function convertCurrency() {
      const amount = parseFloat(document.getElementById("amount").value);
      const fromCurrency = document.getElementById("from").value;
      const toCurrency = document.getElementById("to").value;

      if (isNaN(amount) || amount <= 0) {
        document.getElementById("result").innerText = "Please enter a valid amount.";
        return;
      }

      if (fromCurrency === toCurrency) {
        document.getElementById("result").innerText = `Same currency selected. Result: ${amount}`;
        return;
      }

      const rate = exchangeRates[fromCurrency][toCurrency];
      const converted = amount * rate;

      document.getElementById("result").innerText = 
        `${amount} ${fromCurrency} = ${converted.toFixed(2)} ${toCurrency}`;
    }
  </script>

</body>
</html>
# Currency-converter-

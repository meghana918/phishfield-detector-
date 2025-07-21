<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>PhishX - Phishing Link Detector</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f5f5f5;
      text-align: center;
      padding: 50px;
    }
    input, button {
      padding: 10px;
      margin: 10px;
      width: 300px;
    }
    #result {
      font-size: 20px;
      font-weight: bold;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <h1>🔐 PhishX - URL Threat Detector</h1>

  <input type="text" id="urlInput" placeholder="Enter URL to check" />
  <br>
  <button onclick="checkURL()">Check URL</button>

  <div id="result"></div>

  <script>
    function checkURL() {
      const url = document.getElementById("urlInput").value;
      const result = document.getElementById("result");

      // Basic phishing patterns (can expand)
      const phishingPatterns = ["free", "login", "secure", "bank", "verify", "@", "bit.ly", "tinyurl", "giveaway"];

      let riskScore = 0;
      phishingPatterns.forEach(pattern => {
        if (url.toLowerCase().includes(pattern)) {
          riskScore += 1;
        }
      });

      if (!url.startsWith("http")) {
        result.innerText = "❌ Invalid URL format.";
        result.style.color = "gray";
      } else if (riskScore >= 3) {
        result.innerText = "⚠️ This URL looks **Phishing**!";
        result.style.color = "red";
      } else if (riskScore === 1 || riskScore === 2) {
        result.innerText = "⚠️ This URL is **Suspicious**.";
        result.style.color = "orange";
      } else {
        result.innerText = "✅ This URL looks **Safe**.";
        result.style.color = "green";
      }
    }
  </script>

</body>
</html># phishfield-detector-

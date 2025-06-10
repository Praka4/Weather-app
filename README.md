<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Simple Weather App</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: linear-gradient(to right, #56ccf2, #2f80ed);
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    .weather-container {
      background: rgba(0, 0, 0, 0.4);
      padding: 30px;
      border-radius: 12px;
      text-align: center;
      width: 90%;
      max-width: 400px;
    }

    input[type="text"] {
      padding: 10px;
      width: 70%;
      border: none;
      border-radius: 8px;
      margin-bottom: 10px;
    }

    button {
      padding: 10px 15px;
      background: #1e90ff;
      border: none;
      border-radius: 8px;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background: #005ecb;
    }

    .result {
      margin-top: 20px;
    }

    @media (max-width: 480px) {
      input[type="text"], button {
        width: 100%;
        margin-bottom: 10px;
      }
    }
  </style>
</head>
<body>

  <div class="weather-container">
    <h2>Weather App (No API Key)</h2>
    <input type="text" id="city" placeholder="Enter city (e.g., Chennai)" />
    <button onclick="getWeather()">Get Weather</button>
    <div class="result" id="result"></div>
  </div>

  <script>
    async function getWeather() {
      const city = document.getElementById('city').value.trim();
      const resultDiv = document.getElementById('result');

      if (!city) {
        resultDiv.innerHTML = "<p>Please enter a city name.</p>";
        return;
      }

      const url = `https://wttr.in/${city}?format=%C+%t+%h+%w`;

      try {
        const response = await fetch(url);
        const text = await response.text();

        resultDiv.innerHTML = `<p>🌤️ ${city}<br>${text}</p>`;
      } catch (error) {
        resultDiv.innerHTML = `<p>Error fetching weather. Try again.</p>`;
      }
    }
  </script>

</body>
</html>

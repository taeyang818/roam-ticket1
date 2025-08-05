# roam-ticket1
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Roam Transit Ticket</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
      background: white;
    }

    .circle {
      margin: 20px auto;
      width: 120px;
      height: 120px;
      border: 10px solid black;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      animation: breathe 2s ease-in-out infinite;
    }

    @keyframes breathe {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.15); }
    }

    .time {
      font-size: 36px;
      font-weight: bold;
      margin-top: 10px;
    }

    .ride {
      background: red;
      color: white;
      display: inline-block;
      padding: 10px 20px;
      border-radius: 20px;
      font-size: 20px;
      margin: 20px 0;
    }

    .info {
      font-size: 16px;
      margin-bottom: 20px;
      line-height: 1.4;
    }

    .expires {
      font-size: 14px;
      color: #555;
    }
  </style>
</head>
<body>

  <h2>Roam Transit<br><small>Show operator your ticket</small></h2>
  <div class="circle">
    <span style="font-size: 18px;">Roam</span>
  </div>
  <div class="time" id="currentTime">--:--:--</div>
  <div class="ride">1 Ride Regional</div>
  <div class="info">
    Adult Banff/Canmore<br>
    Regional 1 Ride<br>
    Bow Valley Regional Transit Services Commission
  </div>
  <div class="expires" id="expireTime">Expires --</div>

  <script>
    function updateTime() {
      const now = new Date();
      const expire = new Date(now.getTime() + 40 * 60 * 1000);

      const formatTime = date =>
        date.toLocaleTimeString('en-US', { hour: 'numeric', minute: '2-digit', second: '2-digit' });

      const formatExpire = date =>
        `Expires ${date.toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' })} at ${date.toLocaleTimeString('en-US', { hour: 'numeric', minute: '2-digit' })}`;

      document.getElementById('currentTime').textContent = formatTime(now);
      document.getElementById('expireTime').textContent = formatExpire(expire);
    }

    updateTime();
    setInterval(updateTime, 1000);
  </script>

</body>
</html>

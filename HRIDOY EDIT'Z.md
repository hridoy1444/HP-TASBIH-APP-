<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>তাসবিহ অ্যাপ</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      text-align: center;
      background-color: #f3f4f6;
      color: #111827;
      transition: all 0.3s ease;
    }

    .dark-mode {
      background-color: #111827;
      color: #f3f4f6;
    }

    h1 {
      font-size: 32px;
      margin-bottom: 20px;
    }

    .tasbih-button {
      padding: 10px 20px;
      font-size: 18px;
      margin: 10px;
      cursor: pointer;
    }

    .counter {
      font-size: 22px;
      margin-top: 20px;
    }

    .reset {
      margin-top: 30px;
      background-color: red;
      color: white;
    }

    .signature {
      margin-top: 50px;
      font-family: 'Pacifico', cursive;
      font-size: 24px;
      font-weight: bold;
      color: #3b82f6;
      border-top: 2px dashed #ccc;
      padding-top: 15px;
      text-shadow: 1px 1px 2px #888;
    }

    .switch-container {
      margin-bottom: 20px;
    }
  </style>
</head>
<body>

  <h1>তাসবিহ অ্যাপ</h1>

  <div class="switch-container">
    <label>
      <input type="checkbox" id="modeSwitch" />
      ডার্ক মোড
    </label>
  </div>

  <div class="counter" id="subhanallahCounter">সুবহান আল্লাহ: 0</div>
  <button class="tasbih-button" onclick="increment('subhanallah')">সুবহান আল্লাহ বলো</button>

  <div class="counter" id="alhamdulillahCounter">আলহামদুলিল্লাহ: 0</div>
  <button class="tasbih-button" onclick="increment('alhamdulillah')">আলহামদুলিল্লাহ বলো</button>

  <div class="counter" id="allahuakbarCounter">আল্লাহু আকবার: 0</div>
  <button class="tasbih-button" onclick="increment('allahuakbar')">আল্লাহু আকবার বলো</button>

  <br />
  <button class="tasbih-button reset" onclick="resetAll()">সব রিসেট করো</button>

  <div class="signature">HRIDOY EDIT'Z</div>

  <!-- Sound -->
  <audio id="ding" src="https://www.soundjay.com/button/beep-07.wav" preload="auto"></audio>

  <script>
    let counts = {
      subhanallah: 0,
      alhamdulillah: 0,
      allahuakbar: 0
    };

    function increment(type) {
      if (counts[type] < 33) {
        counts[type]++;
        updateCounter(type);
        vibrate();
        playSound();
      }
    }

    function updateCounter(type) {
      const label =
        type === 'subhanallah' ? 'সুবহান আল্লাহ' :
        type === 'alhamdulillah' ? 'আলহামদুলিল্লাহ' :
        'আল্লাহু আকবার';
      document.getElementById(type + 'Counter').textContent = `${label}: ${counts[type]}`;
    }

    function resetAll() {
      counts = { subhanallah: 0, alhamdulillah: 0, allahuakbar: 0 };
      updateCounter('subhanallah');
      updateCounter('alhamdulillah');
      updateCounter('allahuakbar');
      vibrate();
      playSound();
    }

    function vibrate() {
      if (navigator.vibrate) {
        navigator.vibrate(100);
      }
    }

    function playSound() {
      const audio = document.getElementById('ding');
      audio.currentTime = 0;
      audio.play();
    }

    document.getElementById('modeSwitch').addEventListener('change', function () {
      document.body.classList.toggle('dark-mode', this.checked);
    });
  </script>

</body>
</html>

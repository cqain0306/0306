
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>今天要去哪間酒吧偶遇帥哥？</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  padding: 25px 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Microsoft JhengHei", sans-serif;
  color: white;
  background:
    radial-gradient(circle at 20% 20%, #52206f, transparent 40%),
    radial-gradient(circle at 80% 80%, #8b245c, transparent 40%),
    #100b1c;
}

.container {
  width: 100%;
  max-width: 480px;
  padding: 30px 25px;
  text-align: center;
  border: 1px solid #b65cbd;
  border-radius: 24px;
  background: rgba(25, 15, 39, 0.95);
  box-shadow: 0 0 30px rgba(204, 75, 255, 0.25);
}

.emoji {
  font-size: 55px;
  margin-bottom: 10px;
}

h1 {
  font-size: 27px;
  line-height: 1.5;
  color: #ff9fe8;
  text-shadow: 0 0 15px #f04cba;
  margin: 5px 0 10px;
}

.subtitle {
  color: #d4b5df;
  font-size: 15px;
  margin-bottom: 25px;
}

.label {
  display: block;
  text-align: left;
  margin-bottom: 10px;
  color: #f7b7ed;
  font-size: 15px;
  font-weight: bold;
}

textarea {
  width: 100%;
  height: 160px;
  padding: 15px;
  border: 1px solid #a65bb7;
  border-radius: 12px;
  outline: none;
  resize: vertical;
  background: #21152f;
  color: white;
  font-size: 16px;
  line-height: 2;
}

textarea:focus {
  border-color: #ff79d2;
  box-shadow: 0 0 12px rgba(255, 100, 220, 0.3);
}

button {
  width: 100%;
  margin-top: 20px;
  padding: 16px;
  border: none;
  border-radius: 14px;
  background: linear-gradient(135deg, #ec4899, #9333ea);
  color: white;
  font-size: 21px;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 0 0 20px rgba(236, 72, 153, 0.35);
  transition: 0.2s;
}

button:hover {
  transform: translateY(-3px);
  filter: brightness(1.15);
}

button:active {
  transform: scale(0.97);
}

.result-box {
  margin-top: 25px;
  padding: 25px 15px;
  min-height: 160px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: 1px dashed #f47ad8;
  border-radius: 16px;
  background: linear-gradient(135deg, #32183f, #27142f);
}

.result-title {
  color: #f5b9e9;
  font-size: 16px;
  margin-bottom: 15px;
}

#result {
  color: #ff8de0;
  font-size: 29px;
  font-weight: bold;
  text-shadow: 0 0 15px #ff40bf;
  overflow-wrap: anywhere;
}

#message {
  margin-top: 12px;
  color: #ffe0f5;
  font-size: 14px;
}

.footer {
  margin-top: 22px;
  color: #b99bbf;
  font-size: 13px;
  line-height: 1.8;
}

.decoration {
  color: #ff8bd8;
  margin-top: 12px;
  font-size: 20px;
}
</style>
</head>

<body>

<div class="container">

  <div class="emoji">🍸</div>

  <h1>今天要去哪間酒吧<br>偶遇帥哥？</h1>

  <div class="subtitle">
    今晚的桃花運，就交給命運決定吧！💕
  </div>

  <label class="label" for="options">
    📍 今晚候選酒吧（每行一間）
  </label>

  <textarea id="options">BAR SPEAKEASY 季
Old Vibe bar
Nika Bar
Room by Le Kief</textarea>

  <button onclick="pickBar()">
    ✨ 幫我選！
  </button>

  <div class="result-box">
    <div class="result-title">
      💗 今晚的命定酒吧是...
    </div>

    <div id="result">等待揭曉</div>

    <div id="message">
      說不定今晚就有浪漫邂逅！
    </div>
  </div>

  <div class="decoration">
    ✦ 💜 ✦ 🍷 ✦ 💜 ✦
  </div>

  <div class="footer">
    每間有效酒吧都有相同的中選機率<br>
    今晚去哪裡，就看這一抽！
  </div>

</div>

<script>
function pickBar() {

  const input = document.getElementById("options").value;
  const result = document.getElementById("result");
  const message = document.getElementById("message");

  // 去除空白行及完全相同的重複選項
  const bars = [...new Set(
    input
      .split(/\r?\n/)
      .map(item => item.trim())
      .filter(item => item.length > 0)
  )];

  // 清單為空
  if (bars.length === 0) {
    result.textContent = "—";
    message.textContent = "請先輸入至少一個選項";
    return;
  }

  // 隨機抽選，每個有效選項機率相同
  const randomIndex = Math.floor(
    Math.random() * bars.length
  );

  const selectedBar = bars[randomIndex];

  // 顯示抽籤結果
  result.textContent = selectedBar;
  message.textContent = "💕 今晚的命定地點！出發吧！";
}
</script>

</body>
</html>


<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>2選1選哪個？抽籤器</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      font-family: "Microsoft JhengHei", sans-serif;
      background: linear-gradient(135deg, #dbeafe, #fce7f3);
    }

    .container {
      width: 100%;
      max-width: 480px;
      padding: 30px;
      background: white;
      border-radius: 20px;
      box-shadow: 0 8px 30px rgba(0,0,0,0.12);
      text-align: center;
    }

    h1 {
      color: #333;
      font-size: 28px;
      margin-bottom: 10px;
    }

    .description {
      color: #777;
      margin-bottom: 25px;
    }

    textarea {
      width: 100%;
      height: 150px;
      padding: 15px;
      border: 2px solid #ddd;
      border-radius: 12px;
      font-size: 18px;
      line-height: 1.8;
      resize: vertical;
      outline: none;
    }

    textarea:focus {
      border-color: #818cf8;
    }

    button {
      width: 100%;
      margin-top: 20px;
      padding: 16px;
      border: none;
      border-radius: 12px;
      background: linear-gradient(135deg, #6366f1, #a855f7);
      color: white;
      font-size: 20px;
      font-weight: bold;
      cursor: pointer;
      transition: 0.2s;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(99,102,241,0.3);
    }

    button:active {
      transform: scale(0.98);
    }

    .result-box {
      margin-top: 25px;
      padding: 25px 15px;
      background: #f5f3ff;
      border: 2px dashed #a78bfa;
      border-radius: 15px;
      min-height: 130px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    .result-title {
      color: #777;
      font-size: 16px;
      margin-bottom: 10px;
    }

    #result {
      color: #7c3aed;
      font-size: 36px;
      font-weight: bold;
      word-break: break-word;
    }

    #message {
      margin-top: 12px;
      color: #dc2626;
      font-size: 15px;
    }

    .footer {
      margin-top: 20px;
      color: #999;
      font-size: 13px;
    }
  </style>
</head>

<body>

  <div class="container">

    <h1>🎲 2選1選哪個？</h1>

    <p class="description">
      選擇困難嗎？讓命運幫你決定！
    </p>

    <textarea id="options">1
2</textarea>

    <button onclick="pickOption()">
      🎯 幫我選！
    </button>

    <div class="result-box">
      <div class="result-title">✨ 抽籤結果</div>
      <div id="result">等待抽選</div>
      <div id="message"></div>
    </div>

    <div class="footer">
      每個有效選項都有相同的中籤機率
    </div>

  </div>

  <script>
    function pickOption() {

      const input = document.getElementById("options").value;

      const result = document.getElementById("result");
      const message = document.getElementById("message");

      // 每行一個選項，去除空白行及完全相同的重複選項
      const options = [...new Set(
        input
          .split(/\r?\n/)
          .map(item => item.trim())
          .filter(item => item.length > 0)
      )];

      // 檢查是否有有效選項
      if (options.length === 0) {
        result.textContent = "—";
        message.textContent = "請先輸入至少一個選項";
        return;
      }

      // 均等機率隨機抽選
      const randomIndex = Math.floor(
        Math.random() * options.length
      );

      const selected = options[randomIndex];

      // 顯示結果
      result.textContent = selected;
      message.textContent = "🎉 就決定是你了！";
    }
  </script>

</body>
</html>

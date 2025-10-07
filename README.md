# pocketfix
<!DOCTYPE html>  <html lang="ar">  
<head>  
  <meta charset="UTF-8" />  
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />  
  <title>PocketFix - جيب التصليح</title>  
  <style>  
    body {  
      margin: 0;  
      font-family: 'Cairo', sans-serif;  
      background-color: #000;  
      color: #ffd700;  
      text-align: center;  
    }  
    header {  
      background-color: #111;  
      color: #ffd700;  
      padding: 15px;  
      font-size: 24px;  
      font-weight: bold;  
    }  
    nav {  
      display: flex;  
      justify-content: space-around;  
      background-color: #222;  
      padding: 10px;  
      position: fixed;  
      bottom: 0;  
      width: 100%;  
      border-top: 2px solid #b00;  
    }  
    nav button {  
      background: none;  
      border: none;  
      color: #ffd700;  
      font-size: 16px;  
    }  
    .page {  
      display: none;  
      padding: 20px;  
      min-height: 80vh;  
    }  
    .active {  
      display: block;  
    }  
    button.main {  
      background-color: #b00;  
      color: #fff;  
      padding: 15px 30px;  
      border: none;  
      border-radius: 10px;  
      font-size: 18px;  
      margin-top: 30px;  
    }  
    .card {  
      background-color: #111;  
      border: 1px solid #b00;  
      border-radius: 12px;  
      margin: 10px;  
      padding: 15px;  
    }  
  </style>  
</head>  
<body>  
  <header>🔧 PocketFix - جيب التصليح</header>    <div id="home" class="page active">  
    <h2>أهلاً بك 👋</h2>  
    <p>استخدم الكاميرا لتشخيص الأعطال بسرعة!</p>  
    <button class="main" onclick="showPage('diagnose')">ابدأ الآن</button>  
  </div>    <div id="diagnose" class="page">  
    <h2>تشخيص العطل 🔍</h2>  
    <p>التقط صورة للجهاز المتعطل.</p>  
    <button class="main" onclick="alert('جارٍ التحليل بالذكاء الاصطناعي...')">📸 التقط صورة</button>  
    <button class="main" onclick="showPage('result')">عرض النتائج</button>  
  </div>    <div id="result" class="page">  
    <h2>نتائج التشخيص ⚙️</h2>  
    <div class="card">  
      <p>العطل: سلك مقطوع</p>  
      <p>الاقتراح: يمكن إصلاحه في المنزل.</p>  
      <button class="main" onclick="showPage('technicians')">إرسال فني</button>  
    </div>  
  </div>    <div id="technicians" class="page">  
    <h2>الفنيون القريبون 🧰</h2>  
    <div class="card">  
      <p>👨‍🔧 أحمد – 2 كم</p>  
      <button class="main">طلبه الآن</button>  
    </div>  
    <div class="card">  
      <p>👩‍🔧 سلمى – 3 كم</p>  
      <button class="main">طلبها الآن</button>  
    </div>  
  </div>    <div id="settings" class="page">  
    <h2>⚙️ الإعدادات</h2>  
    <p>الوضع الليلي: مفعل 🌙</p>  
    <p>اللغة: العربية 🇸🇦</p>  
  </div>    <nav>  
    <button onclick="showPage('home')">🏠 الرئيسية</button>  
    <button onclick="showPage('diagnose')">🔍 التشخيص</button>  
    <button onclick="showPage('technicians')">🧰 الفنيون</button>  
    <button onclick="showPage('settings')">⚙️ الإعدادات</button>  
  </nav>    <script>  
    function showPage(pageId) {  
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));  
      document.getElementById(pageId).classList.add('active');  
    }  
  </script>  </body>  
</html>
import express from "express";
import path from "path";
import { fileURLToPath } from "url";

const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);

const app = express();
const PORT = process.env.PORT || 3000;

// يعرّف مجلد public كصفحات الموقع
app.use(express.static(path.join(__dirname, "public")));

// مثال على API بسيط
app.get("/api/test", (req, res) => {
  res.json({ message: "✅ السيرفر شغال بنجاح على Render!" });
});

app.listen(PORT, () => {
  console.log(`🚀 السيرفر يعمل على المنفذ ${PORT}`);
});
{
  "name": "pocketfix",
  "version": "1.0.0",
  "description": "PocketFix server using Node.js",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.19.2"
  }
}

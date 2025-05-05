<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>ตรวจสอบการลงทะเบียน</title>
</head>
<body>
  <h2>กรุณากรอกอีเมลที่ลงทะเบียนไว้</h2>
  <input type="email" id="email" placeholder="your@email.com">
  <button onclick="checkEmail()">เข้าสู่ระบบ</button>

  <p id="result"></p>

  <script>
    async function checkEmail() {
      const email = document.getElementById("email").value;
      const result = document.getElementById("result");

      const response = await fetch("https://script.google.com/macros/s/WEB_APP_URL/exec?email=" + encodeURIComponent(email));
      const data = await response.json();

      if (data.registered) {
        result.innerText = "เข้าสู่ระบบสำเร็จ กำลังเปลี่ยนหน้า...";
        window.location.href = "main.html"; // หน้าเพจจริง
      } else {
        result.innerText = "อีเมลนี้ยังไม่ได้ลงทะเบียน";
      }
    }
  </script>
</body>
</html>

# Ibraham

<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>دخل تخدم</title>
  <style>
    /* ========== ألوان وتصميم عام ========== */
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: linear-gradient(120deg, #FFD700, #1E90FF); /* أصفر وأزرق */
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    /* ========== صفحة تسجيل الدخول ========== */
    #login-container {
      background: rgba(255, 255, 255, 0.9);
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.3);
      text-align: center;
      width: 300px;
    }

    #login-container h1 {
      margin-bottom: 20px;
      color: #1E90FF;
    }

    #login-container input {
      width: 90%;
      padding: 10px;
      margin: 10px 0;
      border-radius: 8px;
      border: 1px solid #ccc;
      font-size: 16px;
    }

    #login-container button {
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      background-color: #1E90FF;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    #login-container button:hover {
      background-color: #104E8B;
    }

    /* ========== واجهة بعد التسجيل ========== */
    #dashboard {
      display: none;
      flex-direction: column;
      align-items: center;
      background: rgba(255,255,255,0.9);
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.3);
      width: 400px;
    }

    #dashboard h2 {
      color: #FFD700;
      margin-bottom: 20px;
    }

    #addWorkBtn {
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      background-color: #1E90FF;
      color: white;
      font-size: 16px;
      cursor: pointer;
      margin-bottom: 20px;
    }

    #addWorkBtn:hover {
      background-color: #104E8B;
    }

    #work-list {
      width: 100%;
    }

    .work-item {
      background: #FFD700;
      color: #1E90FF;
      padding: 10px;
      margin: 5px 0;
      border-radius: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .work-item span {
      font-weight: bold;
    }
  </style>
</head>
<body>

  <!-- ===== صفحة تسجيل الدخول ===== -->
  <div id="login-container">
    <h1>دخل تخدم</h1>
    <input type="email" id="email" placeholder="ادخل الايميل">
    <input type="password" id="password" placeholder="ادخل الباسورد">
    <button onclick="login()">تسجيل</button>
  </div>

  <!-- ===== الواجهة بعد التسجيل ===== -->
  <div id="dashboard">
    <h2>مرحبا بك في لوحة الأعمال</h2>
    <button id="addWorkBtn" onclick="addWork()">أضف عمل</button>
    <div id="work-list"></div>
  </div>

  <script>
    // ===== تسجيل الدخول بسيط =====
    function login() {
      const email = document.getElementById('email').value;
      const password = document.getElementById('password').value;
      if(email && password){
        document.getElementById('login-container').style.display = 'none';
        document.getElementById('dashboard').style.display = 'flex';
      } else {
        alert('الرجاء إدخال الايميل والباسورد');
      }
    }

    // ===== إضافة عمل =====
    let workCount = 0;
    const maxWork = 5; // أقصى عدد أعمال يمكن إضافتها

    function addWork() {
      if(workCount >= maxWork){
        alert('لقد وصلت للحد الأقصى من الأعمال');
        return;
      }
      const workName = prompt('ادخل اسم العمل:');
      if(workName){
        workCount++;
        const workList = document.getElementById('work-list');
        const div = document.createElement('div');
        div.className = 'work-item';
        div.innerHTML = `<span>${workName}</span> <span>${workCount}</span>`;
        workList.appendChild(div);
      }
    }
  </script>

</body>
</html>

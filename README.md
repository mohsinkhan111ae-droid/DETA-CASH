<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Data Selling - Login</title>
  <style>
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #6a11cb, #2575fc);
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .card {
      background: rgba(255, 255, 255, 0.08);
      backdrop-filter: blur(12px);
      border-radius: 18px;
      padding: 40px;
      width: 380px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
      text-align: center;
      color: white;
      animation: fadeIn 0.9s ease-in-out;
    }

    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(-18px);}
      to {opacity: 1; transform: translateY(0);}
    }

    h2 { margin-bottom: 18px; font-size: 26px; }
    input {
      width: 100%;
      padding: 12px;
      margin: 8px 0;
      border: none;
      border-radius: 10px;
      outline: none;
      font-size: 15px;
      background: rgba(255,255,255,0.12);
      color: white;
    }
    input::placeholder { color: rgba(255,255,255,0.8); }

    button {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border: none;
      border-radius: 10px;
      background: linear-gradient(90deg,#ff4b2b,#ff416c);
      color: white;
      font-size: 16px;
      cursor: pointer;
      transition: transform .15s, box-shadow .15s;
    }
    button:hover { transform: translateY(-3px); box-shadow: 0 8px 20px rgba(0,0,0,0.25); }
    .signup-btn { background: linear-gradient(90deg,#2575fc,#6a11cb); }

    .msg { margin-top: 10px; font-size: 14px; min-height: 18px; }
  </style>
</head>
<body>
  <div class="card">
    <h2>🔥 Welcome Back</h2>
    <input type="email" id="email" placeholder="Enter email" required />
    <input type="password" id="password" placeholder="Enter password" required />
    <button onclick="login()">Login</button>
    <button class="signup-btn" onclick="signup()">Create account</button>
    <p class="msg" id="msg"></p>
  </div>

  <!-- Firebase SDK -->
  <script src="https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.12.0/firebase-auth.js"></script>

  <script>
    // ✅ Your Firebase config (API key already added)
    const firebaseConfig = {
      apiKey: "AIzaSyA6FHAm5gZTtglI8ZVD1i6YNcKvyt81kIg",
      authDomain: "data-selling-c24c9.firebaseapp.com",
      projectId: "data-selling-c24c9",
      storageBucket: "data-selling-c24c9.appspot.com",
      messagingSenderId: "140056644897",
      appId: "1:140056644897:web:REPLACE_WITH_YOUR_APPID"
    };

    // Initialize
    const app = firebase.initializeApp(firebaseConfig);
    const auth = firebase.auth();

    function showMsg(text, color='red') {
      const el = document.getElementById('msg');
      el.style.color = color;
      el.innerText = text;
    }

    function login() {
      const email = document.getElementById('email').value;
      const password = document.getElementById('password').value;
      showMsg('Loading...', 'yellow');
      auth.signInWithEmailAndPassword(email, password)
        .then(() => showMsg('✅ Login successful', 'lightgreen'))
        .catch(err => showMsg(err.message || 'Error'));
    }

    function signup() {
      const email = document.getElementById('email').value;
      const password = document.getElementById('password').value;
      showMsg('Creating account...', 'yellow');
      auth.createUserWithEmailAndPassword(email, password)
        .then(() => showMsg('🎉 Account created', 'lightgreen'))
        .catch(err => showMsg(err.message || 'Error'));
    }
  </script>
</body>
</html>

# umuhoza-charlotte<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Online Learning Platform</title>
  <style>
    body { font-family: Arial; margin:0; background:#f4f4f4; }
    header { background:#2c3e50; color:white; padding:15px; text-align:center; }
    nav { display:flex; justify-content:center; background:#34495e; }
    nav button { background:none; border:none; color:white; padding:14px 20px; cursor:pointer; }
    nav button:hover { background:#1abc9c; }
    section { padding:20px; display:none; }
    .active { display:block; }
    .card { background:white; padding:15px; margin:10px 0; border-radius:8px; box-shadow:0 0 5px rgba(0,0,0,0.1); }
    input, button { padding:10px; margin:5px 0; width:100%; }
    button.submit { background:#1abc9c; color:white; border:none; }
    .hidden { display:none; }
  </style>
</head>
<body><header>
  <h1>My Online School</h1>
  <p>Learn Anytime, Anywhere</p>
</header><div id="authSection" class="card">
  <h2>Login / Register</h2>
  <input type="text" id="username" placeholder="Username">
  <input type="password" id="password" placeholder="Password">
  <button onclick="register()">Register</button>
  <button onclick="login()">Login</button>
  <p id="authMsg"></p>
</div><div id="app" class="hidden">
  <nav>
    <button onclick="showSection('home')">Home</button>
    <button onclick="showSection('lessons')">Lessons</button>
    <button onclick="showSection('videos')">Videos</button>
    <button onclick="showSection('quiz')">Quiz</button>
    <button onclick="logout()">Logout</button>
  </nav>  <section id="home" class="active">
    <h2>Welcome</h2>
    <p>Welcome to the learning platform.</p>
  </section>  <section id="lessons">
    <h2>Lessons</h2><div class="card">
  <h3>HTML Basics</h3>
  <p>HTML is used to structure web pages.</p>
</div>

<div class="card">
  <h3>CSS Basics</h3>
  <p>CSS is used for styling.</p>
</div>

<div class="card">
  <h3>JavaScript Basics</h3>
  <p>JavaScript adds interactivity.</p>
</div>

  </section>  <section id="videos">
    <h2>Video Lessons</h2><div class="card">
  <h3>HTML Video</h3>
  <iframe width="100%" height="200" src="https://www.youtube.com/embed/pQN-pnXPaVg" frameborder="0" allowfullscreen></iframe>
</div>

<div class="card">
  <h3>CSS Video</h3>
  <iframe width="100%" height="200" src="https://www.youtube.com/embed/yfoY53QXEnI" frameborder="0" allowfullscreen></iframe>
</div>

  </section>  <section id="quiz">
    <h2>Quiz</h2><div class="card">
  <p>What does HTML stand for?</p>
  <input type="text" id="q1">
</div>

<button class="submit" onclick="checkQuiz()">Submit</button>
<p id="result"></p>

  </section>
</div><script>
  function register() {
    let user = document.getElementById('username').value;
    let pass = document.getElementById('password').value;

    localStorage.setItem(user, pass);
    document.getElementById('authMsg').innerText = "Registered successfully";
  }

  function login() {
    let user = document.getElementById('username').value;
    let pass = document.getElementById('password').value;

    let storedPass = localStorage.getItem(user);

    if (storedPass === pass) {
      document.getElementById('authSection').classList.add('hidden');
      document.getElementById('app').classList.remove('hidden');
    } else {
      document.getElementById
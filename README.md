Index.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Interactive JavaScript Project</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <h1>Welcome to My Interactive Page</h1>

  <!-- Light/Dark Mode Toggle -->
  <button id="themeToggle">Toggle Theme</button>

  <!-- Counter Game -->
  <div>
    <p>Score: <span id="counter">0</span></p>
    <button id="incrementBtn">Increase</button>
  </div>

  <!-- Collapsible FAQ -->
  <div class="faq">
    <h3 class="faq-question">What is JavaScript?</h3>
    <p class="faq-answer hidden">JavaScript is a programming language for the web.</p>
  </div>

  <!-- Form Section -->
  <form id="signupForm">
    <label>Name: <input type="text" id="name" /></label><br />
    <label>Email: <input type="email" id="email" /></label><br />
    <label>Password: <input type="password" id="password" /></label><br />
    <button type="submit">Sign Up</button>
    <p id="formMessage"></p>
  </form>

  <script src="script.js"></script>
</body>
</html>

Script.js

// 🌗 Light/Dark Mode Toggle
document.getElementById('themeToggle').addEventListener('click', () => {
  document.body.classList.toggle('dark-mode');
});

// 🎮 Counter Game
let count = 0;
document.getElementById('incrementBtn').addEventListener('click', () => {
  count++;
  document.getElementById('counter').textContent = count;
});

// 📚 Collapsible FAQ
document.querySelector('.faq-question').addEventListener('click', () => {
  document.querySelector('.faq-answer').classList.toggle('hidden');
});

// 📋✅ Form Validation
document.getElementById('signupForm').addEventListener('submit', function (e) {
  e.preventDefault(); // Prevent form submission

  const name = document.getElementById('name').value.trim();
  const email = document.getElementById('email').value.trim();
  const password = document.getElementById('password').value.trim();
  const message = document.getElementById('formMessage');

  // Simple regex for email and password validation
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  const passwordRegex = /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{6,}$/;

  if (!name) {
    message.textContent = 'Name is required.';
  } else if (!emailRegex.test(email)) {
    message.textContent = 'Please enter a valid email.';
  } else if (!passwordRegex.test(password)) {
    message.textContent = 'Password must be at least 6 characters and include a number.';
  } else {
    message.textContent = 'Form submitted successfully!';
    message.style.color = 'green';
  }
});

style.css

body.dark-mode {
  background-color: #121212;
  color: #f0f0f0;
}

.hidden {
  display: none;
}

.faq {
  margin-top: 20px;
  cursor: pointer;
}

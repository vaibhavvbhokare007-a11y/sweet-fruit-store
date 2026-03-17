<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sweet & Fruit Store</title>

<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  background: linear-gradient(120deg,#fff8f0,#ffe0cc);
}

html {
  scroll-behavior: smooth;
}

header {
  background: #ff6f61;
  padding: 15px;
  color: white;
  text-align: center;
  position: sticky;
  top: 0;
}

nav a {
  margin: 10px;
  color: white;
  text-decoration: none;
  font-weight: bold;
}

nav a:hover {
  color: yellow;
}

.container {
  padding: 20px;
  animation: fadeIn 1s ease-in;
}

.card {
  background: white;
  padding: 15px;
  margin: 15px;
  border-radius: 15px;
  box-shadow: 0 5px 15px rgba(0,0,0,0.2);
  display: inline-block;
  width: 220px;
  transition: transform 0.3s;
}

.card:hover {
  transform: scale(1.08);
}

img {
  width: 100%;
  border-radius: 10px;
}

button {
  background: #ff6f61;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background: #e85c50;
}

input {
  padding: 10px;
  margin: 5px;
  width: 90%;
  border-radius: 5px;
  border: 1px solid #ccc;
}

#userDisplay {
  font-size: 14px;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px);}
  to { opacity: 1; transform: translateY(0);}
}
</style>
</head>

<body>

<header>
  <h1>🍰 Sweet & Fruit Store 🍎</h1>
  <h3 id="userDisplay">Not Logged In</h3>

  <nav>
    <a href="#login">Login</a>
    <a href="#home">Home</a>
    <a href="#sweets">Sweets</a>
    <a href="#fruits">Fruits</a>
    <a href="#cart">Cart</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<!-- LOGIN -->
<div class="container" id="login">
  <h2>Login / Registration</h2>

  <input type="text" id="username" placeholder="Username"><br>
  <input type="password" id="password" placeholder="Password"><br>

  <button onclick="register()">Register</button>
  <button onclick="login()">Login</button>

  <p id="message" style="color: green;"></p>
</div>

<!-- HOME -->
<div class="container" id="home">
  <h2>Welcome</h2>
  <p>Enjoy fresh fruits and delicious sweets 🍓🍩</p>
  <img src="https://images.unsplash.com/photo-1606787366850-de6330128bfc">
</div>

<!-- SWEETS -->
<div class="container" id="sweets">
  <h2>Sweets</h2>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1606313564200-e75d5e30476c">
    <h3>Ladoo</h3>
    <p>₹200/kg</p>
    <button onclick="addToCart('Ladoo')">Add to Cart</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1627308595229-7830a5c91f9f">
    <h3>Barfi</h3>
    <p>₹300/kg</p>
    <button onclick="addToCart('Barfi')">Add to Cart</button>
  </div>

</div>

<!-- FRUITS -->
<div class="container" id="fruits">
  <h2>Fruits</h2>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1567306226416-28f0efdc88ce">
    <h3>Apple</h3>
    <p>₹150/kg</p>
    <button onclick="addToCart('Apple')">Add to Cart</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1550258987-190a2d41a8ba">
    <h3>Pineapple</h3>
    <p>₹120/kg</p>
    <button onclick="addToCart('Pineapple')">Add to Cart</button>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1574226516831-e1dff420e8f8">
    <h3>Banana</h3>
    <p>₹60/dozen</p>
    <button onclick="addToCart('Banana')">Add to Cart</button>
  </div>

</div>

<!-- CART -->
<div class="container" id="cart">
  <h2>Your Cart</h2>
  <ul id="cartList"></ul>
</div>

<!-- ABOUT -->
<div class="container" id="about">
  <h2>About Us</h2>
  <p>We deliver fresh fruits and traditional sweets with love ❤️</p>
</div>

<!-- CONTACT -->
<div class="container" id="contact">
  <h2>Contact</h2>
  <p>Email: sweetfruit@gmail.com</p>
</div>

<script>
// REGISTER
function register() {
  let user = document.getElementById("username").value;
  let pass = document.getElementById("password").value;

  if (user === "" || pass === "") {
    document.getElementById("message").innerText = "Fill all fields!";
    return;
  }

  localStorage.setItem(user, pass);
  document.getElementById("message").innerText = "Registered Successfully!";
}

// LOGIN
function login() {
  let user = document.getElementById("username").value;
  let pass = document.getElementById("password").value;

  let storedPass = localStorage.getItem(user);

  if (storedPass === null) {
    document.getElementById("message").innerText = "User not found!";
  } else if (storedPass === pass) {
    document.getElementById("message").innerText = "Login Successful!";
    document.getElementById("userDisplay").innerText = "Welcome " + user;

    window.location.href = "#home";
  } else {
    document.getElementById("message").innerText = "Wrong Password!";
  }
}

// CART
function addToCart(item) {
  let list = document.getElementById('cartList');
  let li = document.createElement('li');
  li.textContent = item + ' added';
  list.appendChild(li);
}
</script>

</body>
</html>

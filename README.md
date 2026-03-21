<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sweet & Fruit Store</title>

<style>
body {
  font-family: Arial;
  margin: 0;
  background: linear-gradient(120deg,#fff8f0,#ffe0cc);
}

header {
  background: #ff6f61;
  padding: 15px;
  color: white;
  text-align: center;
}

nav a {
  margin: 10px;
  color: white;
  text-decoration: none;
  font-weight: bold;
  cursor: pointer;
}

nav a:hover {
  color: yellow;
}

.section {
  display: none;
  padding: 20px;
  animation: fade 0.5s;
}

.active {
  display: block;
}

.card {
  background: white;
  padding: 15px;
  margin: 15px;
  border-radius: 15px;
  display: inline-block;
  width: 220px;
  box-shadow: 0 5px 10px gray;
}

img {
  width: 100%;
  border-radius: 10px;
}

button {
  background: #ff6f61;
  color: white;
  border: none;
  padding: 8px;
  cursor: pointer;
}

@keyframes fade {
  from {opacity:0;}
  to {opacity:1;}
}
</style>
</head>

<body>

<header>
<h1>🍰 Sweet & Fruit Store 🍎</h1>
<h3 id="userDisplay">Not Logged In</h3>

<nav>
<a onclick="showPage('login')">Login</a>
<a onclick="showPage('home')">Home</a>
<a onclick="showPage('sweets')">Sweets</a>
<a onclick="showPage('fruits')">Fruits</a>
<a onclick="showPage('cart')">Cart</a>
<a onclick="showPage('about')">About</a>
<a onclick="showPage('contact')">Contact</a>
</nav>
</header>

<!-- LOGIN -->
<div id="login" class="section active">
<h2>Login</h2>
<input id="username" placeholder="Username"><br>
<input id="password" type="password" placeholder="Password"><br>
<button onclick="register()">Register</button>
<button onclick="login()">Login</button>
<p id="msg"></p>
</div>

<!-- HOME -->
<div id="home" class="section">
<h2>Welcome</h2>
<p>Fresh fruits & sweets 🍓</p>
<img src="https://images.unsplash.com/photo-1606787366850-de6330128bfc">
</div>

<!-- SWEETS -->
<div id="sweets" class="section">
<h2>Sweets</h2>
<div class="card">
<img src="https://images.unsplash.com/photo-1606313564200-e75d5e30476c">
<h3>Ladoo</h3>
<button onclick="addToCart('Ladoo')">Add</button>
</div>
<div class="card">
<img src="https://images.unsplash.com/photo-1627308595229-7830a5c91f9f">
<h3>Barfi</h3>
<button onclick="addToCart('Barfi')">Add</button>
</div>
<h4>kajukatli</h4>
<img src ="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT93Xp55HP33vx7gIJ24vn00V1xmdDUNfvTrXwaO0mn6otbMGAncWOWRl635FvJ6X0-BTppJePkRtUMOm7dQBHbmcneQCkzo9RINbgyAMvdW1xQFgPBFxXjJiWdA4wFI9AFkFJp&s=10&ec=121584920"
<h4> price 600 rs /kg</h4>
<button on onclick="addToCart('kajukatli')">Add</button>
</div>

<!-- FRUITS -->
<div id="fruits" class="section">
<h2>Fruits</h2>
<div class="card">
<img src="https://images.unsplash.com/photo-1567306226416-28f0efdc88ce">
<h3>Apple</h3>
<h3>price ="150 Rs \kg"</h3>
<img src="data:image/webp;base64,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"
<h4>mango</h4>
<h4> price="5000 RS \kg"</h4>

<button onclick="addToCart('Apple')">Add</button>
</div>
</div>

<!-- CART -->
<div id="cart" class="section">
<h2>Cart</h2>
<h3> apple, mango, cake, cherry, barfi, ladoo.....</h3>
<ul id="cartList"></ul>
</div>

<!-- ABOUT -->
<div id="about" class="section">
<h2>About</h2>
<p>We deliver fresh items ❤️ 
 "Love is a fruit in season at all times, and within reach of every hand."=</p>
</div>

<!-- CONTACT -->
<div id="contact" class="section">
<h2>Contact</h2>
<p>Email:vaibhavbhokare@gmail.com</p>
</div>

<script>
// PAGE SWITCH
function showPage(pageId) {
  let pages = document.querySelectorAll('.section');
  pages.forEach(p => p.classList.remove('active'));
  document.getElementById(pageId).classList.add('active');
}

// REGISTER
function register() {
  let u = username.value;
  let p = password.value;

  if (!u || !p) return msg.innerText="Fill all fields";

  if (localStorage.getItem(u)) {
    msg.innerText="User exists!";
  } else {
    localStorage.setItem(u,p);
    msg.innerText="Registered!";
  }
}

// LOGIN
function login() {
  let u = username.value;
  let p = password.value;

  if (localStorage.getItem(u) === p) {
    localStorage.setItem("user", u);
    userDisplay.innerText="Welcome " + u;
    showPage('home');
  } else {
    msg.innerText="Invalid login";
  }
}

// CART
function addToCart(item) {
  let user = localStorage.getItem("user");
  if (!user) return alert("Login first");

  let li = document.createElement("li");
  li.innerText=item;
  cartList.appendChild(li);
}

// AUTO LOGIN
window.onload = function() {
  let u = localStorage.getItem("user");
  if (u) userDisplay.innerText="Welcome " + u;
};
</script>

</body>
</html>
<input type="text" id="myInput" onkeyup="searchProducts()" placeholder="Search for sweets...">

<div id="productGrid" style="display: flex; gap: 20px; margin-top: 20px;">
  <div class="product" data-name="Kaju Katli">
    <img src="kaju_katli.jpg" width="100"><p>Kaju Katli</p>
  </div>
  <div class="product" data-name="Gulab Jamun">
    <img src="gulab_jamun.jpg" width="100"><p>Gulab Jamun</p>
  </div>
  <div class="product" data-name="Besan Ladoo">
    <img src="ladoo.jpg" width="100"><p>Besan Ladoo</p>
  </div>
</div>

<script>
function searchProducts() {
  let input = document.getElementById('myInput').value.toLowerCase();
  let products = document.querySelectorAll('.product');

  products.forEach(item => {
    let name = item.getAttribute('data-name').toLowerCase();
    item.style.display = name.includes(input) ? "block" : "none";
  });
}
</script>

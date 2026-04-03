# heavenlyloaf.github.io

<html lang="en">
<head>
<meta charset="UTF-8">
<title>Paint By Pastries</title>

<style>
body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: #fff7f5;
}

header {
    background: #ffc1cc;
    padding: 15px;
    text-align: center;
    color: white;
    font-size: 24px;
    font-weight: bold;
}

nav {
    display: flex;
    justify-content: center;
    background: #ffd6dc;
    padding: 10px;
}
nav button {
    margin: 5px;
    padding: 8px 15px;
    border: none;
    border-radius: 20px;
    background: white;
    cursor: pointer;
}

.container {
    display: flex;
}

.main {
    width: 75%;
    padding: 20px;
}

.cart {
    width: 25%;
    background: #fff0f3;
    padding: 15px;
    position: sticky;
    top: 0;
    height: 100vh;
    border-left: 2px solid #ffd6dc;
}

.grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
}

.card {
    background: white;
    border-radius: 15px;
    padding: 10px;
    text-align: center;
}

.card img {
    width: 100%;
    border-radius: 10px;
}

button {
    cursor: pointer;
}

.section {
    display: none;
}
.active {
    display: block;
}

.box {
    background: white;
    padding: 20px;
    border-radius: 15px;
}

.checkout-btn {
    width: 100%;
    padding: 10px;
    background: #ff8fa3;
    color: white;
    border: none;
    border-radius: 10px;
    margin-top: 10px;
}
</style>
</head>

<body>

<header>🎨 Paint By Pastries</header>

<nav>
    <button onclick="showSection('home')">Store</button>
    <button onclick="showSection('about')">About</button>
    <button onclick="showSection('contact')">Contact</button>
    <button onclick="showSection('location')">Find Us</button>
</nav>

<div class="container">

<div class="main">

<!-- STORE -->
<div id="home" class="section active">
    <h2>Our Bento Kits 🎂</h2>
    <div class="grid">

        <div class="card">
            <img src="paint_by_pastries_1.png">
            <p>Studio Kit</p>
            <p>₱100</p>
            <button onclick="addToCart('Studio Kit',100)">Add</button>
        </div>

        <div class="card">
            <img src="paint_by_pastries_2.png">
            <p>Studio Kit + Letter</p>
            <p>₱125</p>
            <button onclick="addToCart('Studio Kit + Letter',125)">Add</button>
        </div>

        <div class="card">
            <img src="paint_by_pastries_3.png">
            <p>Studio Kit + Florals</p>
            <p>₱175</p>
            <button onclick="addToCart('Studio Kit + Florals',175)">Add</button>
        </div>

        <div class="card">
            <img src="paint_by_pastries_4.png">
            <p>Complete Masterpiece</p>
            <p>₱200</p>
            <button onclick="addToCart('Complete Masterpiece',200)">Add</button>
        </div>

    </div>
</div>

<!-- ABOUT -->
<div id="about" class="section">
    <div class="box">
        <h2>About Us 💕</h2>
        <p>Paint By Pastries is a creative dessert experience where you design your own cake.</p>
    </div>
</div>

<!-- CONTACT -->
<div id="contact" class="section">
    <div class="box">
        <h2>Contact 📩</h2>
        <p>Instagram: @paintbypastries</p>
    </div>
</div>

<!-- LOCATION -->
<div id="location" class="section">
    <div class="box">
        <h2>Find Us 📍</h2>
        <iframe src="https://maps.google.com/maps?q=Pamantasan%20ng%20Lungsod%20ng%20Maynila&output=embed"></iframe>
    </div>
</div>

<!-- CHECKOUT PAGE -->
<div id="checkout" class="section">
    <div class="box">
        <h2>Checkout 🧾</h2>
        <div id="checkoutItems"></div>
        <p><strong>Total: ₱<span id="checkoutTotal">0</span></strong></p>
        <button onclick="placeOrder()" class="checkout-btn">Place Order</button>
    </div>
</div>

</div>

<!-- CART -->
<div class="cart">
    <h3>🛒 Cart</h3>
    <div id="cartItems"></div>
    <p><strong>Total: ₱<span id="total">0</span></strong></p>
    <button class="checkout-btn" onclick="goToCheckout()">Checkout</button>
</div>

</div>

<script>
let total = 0;
let cartData = [];

function addToCart(name, price) {
    cartData.push({name, price});
    
    let cart = document.getElementById("cartItems");
    let item = document.createElement("div");
    item.textContent = name + " - ₱" + price;
    cart.appendChild(item);

    total += price;
    document.getElementById("total").textContent = total;
}

function goToCheckout() {
    if(cartData.length === 0){
        alert("Your cart is empty!");
        return;
    }

    let checkoutItems = document.getElementById("checkoutItems");
    checkoutItems.innerHTML = "";

    cartData.forEach(item => {
        let div = document.createElement("div");
        div.textContent = item.name + " - ₱" + item.price;
        checkoutItems.appendChild(div);
    });

    document.getElementById("checkoutTotal").textContent = total;

    showSection('checkout');
}

function placeOrder(){
    alert("Order placed successfully! 🎉");
    location.reload();
}

function showSection(sectionId) {
    let sections = document.querySelectorAll(".section");
    sections.forEach(sec => sec.classList.remove("active"));
    document.getElementById(sectionId).classList.add("active");
}
</script>

</body>
</html>

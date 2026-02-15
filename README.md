<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Pharmacy</title>
  <style>
    body { font-family: Arial, sans-serif; margin:0; padding:0; background:#f9f9f9;}
    header { background:#2a9df4; color:white; padding:20px; text-align:center; }
    nav a { margin: 0 15px; color:white; text-decoration:none; }
    .container { padding:20px; }
    .medicine { border:1px solid #ccc; padding:15px; margin:10px; border-radius:5px; background:white; display:inline-block; width:200px; vertical-align:top; }
    .medicine img { width:100%; height:150px; object-fit:cover; }
    .cart { position:fixed; top:20px; right:20px; background:#ff7f50; color:white; padding:10px; border-radius:5px; cursor:pointer; }
    .cart-items { display:none; position:fixed; top:60px; right:20px; background:white; padding:10px; border:1px solid #ccc; max-width:300px; }
    button { background:#2a9df4; color:white; border:none; padding:8px 12px; margin-top:5px; cursor:pointer; border-radius:3px; }
    button:hover { background:#1b6dbf; }
    footer { background:#333; color:white; text-align:center; padding:15px; margin-top:20px; }
  </style>
</head>
<body>

<header>
  <h1>My Pharmacy</h1>
  <nav>
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<div class="cart" onclick="toggleCart()">Cart 🛒 <span id="cart-count">0</span></div>
<div class="cart-items" id="cart-items"></div>

<div class="container" id="home">
  <h2>Available Medicines</h2>
  <div class="medicine">
    <img src="https://via.placeholder.com/200x150" alt="Medicine 1">
    <h3>Paracetamol</h3>
    <p>Price: $5</p>
    <button onclick="addToCart('Paracetamol', 5)">Add to Cart</button>
  </div>
  <div class="medicine">
    <img src="https://via.placeholder.com/200x150" alt="Medicine 2">
    <h3>Vitamin C</h3>
    <p>Price: $10</p>
    <button onclick="addToCart('Vitamin C', 10)">Add to Cart</button>
  </div>
  <div class="medicine">
    <img src="https://via.placeholder.com/200x150" alt="Medicine 3">
    <h3>Cough Syrup</h3>
    <p>Price: $8</p>
    <button onclick="addToCart('Cough Syrup', 8)">Add to Cart</button>
  </div>
</div>

<div class="container" id="about">
  <h2>About Us</h2>
  <p>Welcome to My Pharmacy. We provide quality medicines and health products at affordable prices.</p>
</div>

<div class="container" id="contact">
  <h2>Contact Us</h2>
  <p>Email: info@mypharmacy.com</p>
  <p>Phone: +1234567890</p>
</div>

<footer>
  &copy; 2026 My Pharmacy
</footer>

<script>
  let cart = [];
  
  function addToCart(name, price) {
    cart.push({name, price});
    document.getElementById('cart-count').innerText = cart.length;
    updateCartItems();
  }

  function toggleCart() {
    const cartDiv = document.getElementById('cart-items');
    cartDiv.style.display = cartDiv.style.display === 'block' ? 'none' : 'block';
  }

  function updateCartItems() {
    const cartDiv = document.getElementById('cart-items');
    cartDiv.innerHTML = '';
    let total = 0;
    cart.forEach(item => {
      const div = document.createElement('div');
      div.innerHTML = `${item.name} - $${item.price}`;
      cartDiv.appendChild(div);
      total += item.price;
    });
    if(cart.length>0){
      const totalDiv = document.createElement('div');
      totalDiv.style.fontWeight = 'bold';
      totalDiv.style.marginTop = '10px';
      totalDiv.innerHTML = `Total: $${total} <br><button onclick="checkout()">Checkout</button>`;
      cartDiv.appendChild(totalDiv);
    } else {
      cartDiv.innerHTML = 'Cart is empty';
    }
  }

  function checkout() {
    alert('Thank you for your order! (This is a demo, no payment processed)');
    cart = [];
    document.getElementById('cart-count').innerText = 0;
    updateCartItems();
  }
</script>

</body>
</html>

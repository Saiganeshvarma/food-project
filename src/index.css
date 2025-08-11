import React, { useEffect, useState } from 'react';
import './App.css';
import { ToastContainer, toast } from 'react-toastify';


function App() {
  const [recipes, setRecipes] = useState([]);
  const [cart, setCart] = useState([]);
  const [showCart, setShowCart] = useState(false); // Toggle modal

  // Fetch food data
  async function fetchData() {
    const res = await fetch("https://dummyjson.com/recipes");
    const json = await res.json();
    setRecipes(json.recipes || []);
  }

  useEffect(() => {
    fetchData();
  }, []);

  // Add to cart
  const addToCart = (item) => {
    const exists = cart.find(cartItem => cartItem.id === item.id);
    if (!exists) {
      setCart([...cart, item]);
      toast.success(`${item.name} added to cart!`);
    } else {
      toast.error(`${item.name} is already in cart!`);
    }
  };

  // Remove from cart
  const removeFromCart = (id) => {
    setCart(cart.filter(item => item.id !== id));
    toast.info("Item removed from cart.");
  };

  return (
    <div className="app">
           <ToastContainer position="top-right" autoClose={2000} />
      <h1 className="title">🍽️ Food Store</h1>

      {/* Cart button */}
      <div
        className="cart-info"
        onClick={() => setShowCart(true)}
        style={{ cursor: "pointer" }}
      >
        🛒 Cart Items: {cart.length}
      </div>

      {/* Product list */}
      <div className="list">
        {recipes.map((item) => (
          <div key={item.id} className="card">
            <img className="card-image" src={item.image} alt={item.name} />
            <h2 className="card-title">{item.name}</h2>
            <p className="card-description">
              Ingredients: {item.ingredients.join(', ')}
            </p>
            <div className="card-footer">
              <button className="cart-button" onClick={() => addToCart(item)}>Add to Cart</button>
            </div>
          </div>
        ))}
      </div>

      {/* Cart Modal */}
      {showCart && (
        <div className="cart-modal">
          <div className="cart-modal-content">
            <h2>Your Cart</h2>
            {cart.length === 0 ? (
              <p>Your cart is empty.</p>
            ) : (
              cart.map(item => (
                <div key={item.id} className="cart-item">
                  <img src={item.image} alt={item.name} />
                  <span>{item.name}</span>
                  <button onClick={() => removeFromCart(item.id)}>Remove</button>
                </div>
              ))
            )}
            <button className="close-button" onClick={() => setShowCart(false)}>Close</button>
          </div>
        </div>
      )}


   
    </div>
  );
}

export default App;



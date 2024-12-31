let cart = [];
let total = 0;

// Añadir producto al carrito
function addToCart(item, price) {
    cart.push({ item, price });
    total += price;
    displayCart();
}

// Mostrar el carrito
function displayCart() {
    const cartList = document.getElementById('cart');
    cartList.innerHTML = '';
    cart.forEach((cartItem, index) => {
        const listItem = document.createElement('li');
        listItem.textContent = `${cartItem.item} - $${cartItem.price}`;
        const removeButton = document.createElement('button');
        removeButton.textContent = 'Remove';
        removeButton.onclick = () => removeFromCart(index);
        listItem.appendChild(removeButton);
        cartList.appendChild(listItem);
    });
    document.getElementById('total').textContent = total.toLocaleString();
}

// Eliminar producto del carrito
function removeFromCart(index) {
    total -= cart[index].price;
    cart.splice(index, 1);
    displayCart();
}

// Vaciar el carrito
function clearCart() {
    cart = [];
    total = 0;
    displayCart();
}
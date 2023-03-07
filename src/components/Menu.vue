<script setup>
import { ref } from 'vue'

const items = [
  {
    id: 1,
    name: 'Ham and Pineapple',
    description: 'A Delicious tomato based pizza topped with mozzarella, ham and pineapple',
    options: [{
      size: 9,
      price: 7.95
    },
    {
      size: 12,
      price: 10.95
    }]
  },
  {
    id: 2,
    name: 'Peperoni Pizza',
    description: 'A Delicious peperoni based pizza topped with mozzarella, ham and pineapple',
    options: [{
      size: 9,
      price: 6.95
    },
    {
      size: 12,
      price: 9.95
    }]
  }
]
const pizzas = ref(items)
const emptyCartMessage = ref('No Pizzas in you cart ordered yet!')
const cart = ref([])

function addToCart(pizza, pizzaOption) {
  this.cart.push({
    name: pizza.name,
    price: pizzaOption.price,
    size: pizzaOption.size,
    quantity: 1
  })
}
function incrementQuantity(item) {
  item.quantity++
}
function decreaseQuantity(item) {
  item.quantity--
  if (item.quantity === 0) {
    this.removeItemFromCart(item)
  }
}

function removeItemFromCart(item) {
  this.cart.splice(this.cart.indexOf(item), 1)
}

</script>

<template>
  <div>
    <div>
      <table>
        <thead>
          <tr>
            <th>Size</th>
            <th>Price</th>
            <th>Add to basket</th>
          </tr>
        </thead>
        <tbody v-for="pizza in pizzas" :key="pizza.id">
          <tr>
            <td><strong>{{ pizza.name }}</strong></td>
          </tr>
          <tr v-for="option in pizza.options">
            <td>{{ option.size }}"</td>
            <td>{{ option.price }}</td>
            <td>
              <button class="button" type="button" @click="addToCart(pizza, option)">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                  stroke="currentColor" class="icon-default-size">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" />
                </svg>
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <div v-if="cart.length > 0">
      <table>
        <thead>
          <th>Quantity</th>
          <th>Item</th>
          <th>Total</th>
        </thead>
        <tbody v-for="item in cart">
          <tr>
            <td>
              <button class="button" @click="decreaseQuantity(item)"><span>
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                    stroke="currentColor" class="icon-default-size">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 12h-15" />
                  </svg>
                </span>
              </button>
              <span class="quantity-number">{{ item.quantity }}</span>
              <button class="button" @click="incrementQuantity(item)"><span>
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                    stroke="currentColor" class="icon-default-size">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" />
                  </svg>
                </span>
              </button>
            </td>
            <td>{{ item.name }} - {{ item.size }}</td>
            <td>{{ item.price * item.quantity }}</td>
          </tr>

        </tbody>
      </table>
      <div>
        <p>Order total:</p>
        <button>Place Order</button>
      </div>
    </div>
    <div v-else>
      <p>{{ emptyCartMessage }}</p>
    </div>
  </div>
</template>
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
              <button type="button" @click="addToCart(pizza, option)">+</button>
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
              <button><span>-</span></button>
              <button><span>+</span></button>
            </td>
            <td>{{ item.name }} - {{ item.size }}</td>
            <td>{{ item.price }}</td>
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
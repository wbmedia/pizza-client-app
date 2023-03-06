<script setup>
import NewPizza from './NewPizza.vue'
</script>
<template>
  <div>
    <div>
      <NewPizza />
    </div>
    <div>
      <h3>Menu:</h3>
      <table>
        <thead>
          <tr>
            <th>Item</th>
            <th>Remove from menu</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>
              <p>Peperoni Pizza</p>
            </td>
            <td>
              <button>Remove</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <div>
      <h3>Current orders:</h3>
      <table>
        <thead>
          <tr>
            <th>Item</th>
            <th>Size</th>
            <th>Quantity</th>
            <th>Price</th>
          </tr>
        </thead>
        <tbody>
          <div>
            <strong><em>Order Number: 1</em></strong>
            <button>Remove</button>
          </div>
          <tr>
            <td>Peperoni Pizza</td>
            <td>9"</td>
            <td>1</td>
            <td>6.99</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
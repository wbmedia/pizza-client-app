<script setup>
import { ref } from "vue"
const newPizza = ref({
  'name': 'Eg. Peperoni Pizza',
  'description': 'Eg. Peperoni Pizza with tomato sauce and mozzarella cheese',
  'options': [{
    'size': 9,
    'price': 6.99
  }, {
    'size': 12,
    'price': 10.95
  }]
})


function addMenuItem() {
  console.log(newPizza)
}
</script>
<template>
  <div>
    <h3>Add new Pizza:</h3>
    <form>
      <div>
        <label for="name">Name</label>
        <input type="text" name="name" v-model="newPizza.name">
      </div>

      <div>
        <label for="description">Description</label>
        <textarea v-model="newPizza.description" name="description" id="descriptions" cols="30" rows="10"></textarea>
      </div>

      <div>
        <p>Option 1:</p>
        <label for="option1">Size (")</label>
        <input type="text" name="option1" v-model="newPizza.options[0].size">
        <label for="price1">Price</label>
        <input type="text" name="price1" v-model="newPizza.options[0].price">
      </div>

      <div>
        <p>Option 2:</p>
        <label for="option2">Size (")</label>
        <input type="text" name="option1" v-model="newPizza.options[1].size">
        <label for="price2">Price</label>
        <input type="text" name="price2" v-model="newPizza.options[1].price">
      </div>

      <button type="button" @click="addMenuItem">Add</button>
    </form>
  </div>
</template>
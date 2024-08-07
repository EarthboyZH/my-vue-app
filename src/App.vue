<script setup>
import { ref } from 'vue'

// Create a reactive reference to an empty string
const value = ref('')

// Create a reactive reference to an array of todo items
const list = ref([
  { value: 'JavaScript', isCompleted: true },
  { value: 'JQuery', isCompleted: false },
  { value: 'Vue', isCompleted: false },
])

// Function to add a new todo item to the list
function add() {
  // Push a new todo item to the list with the value of the input field and isCompleted set to false
  list.value.push({
    value: value.value,
    isCompleted: false,
  })

  // Reset the input field to an empty string
  value.value = ''
}

// Function to delete a todo item from the list
function del(index) {
  // Remove the todo item at the given index from the list
  list.value.splice(index, 1)
}
</script>
<template>
  <div class="todo-app">
    <div class="title">Todo App</div>

    <div class="todo-form">
      <!-- Input field to add a new todo item -->
      <input
        v-model="value"
        type="text"
        class="todo-input"
        placeholder="Add a todo"
      />
      <!-- Button to add a new todo item -->
      <div @click="add" class="todo-button">Add Todo</div>
    </div>

    <!-- Loop through the list of todo items -->
    <div
      v-for="(item, index) in list"
      :class="[item.isCompleted ? 'completed' : 'item']"
    >
      <div>
        <!-- Checkbox to mark a todo item as completed -->
        <input v-model="item.isCompleted" type="checkbox" />
        <!-- Display the value of the todo item -->
        <span class="name">{{ item.value }}</span>
      </div>

      <!-- Button to delete a todo item -->
      <button @click="del(index)" class="del-button">del</button>
    </div>
  </div>
</template>

<style scoped>
.todo-app {
  box-sizing: border-box;
  margin-top: 40px;
  margin-left: 1%;
  padding-top: 30px;
  width: 98%;
  height: 500px;
  background: #ffffff;
  border-radius: 5px;
}

.title {
  text-align: center;
  font-size: 30px;
  font-weight: 700;
}

.todo-form {
  display: flex;
  margin: 20px 0 30px 20px;
}

.todo-button {
  width: 100px;
  height: 52px;
  border-radius: 0 20px 20px 0;

  text-align: center;
  background: linear-gradient(
    to right,
    rgb(113, 65, 168),
    rgba(44, 114, 251, 1)
  );
  color: #fff;
  line-height: 52px;
  cursor: pointer;
  font-size: 14px;
  user-select: none;
}

.del-button {
  width: 60px;
  height: 30px;
  border-radius: 5px 5px 5px 5px;
  text-align: center;
  background:blue;
  border:none;
  color:#FFF;
  cursor: pointer;
}

.todo-input {
  padding: 0px 15px 0px 15px;
  border-radius: 20px 0 0 20px;
  border: 1px solid #dfe1e5;
  outline: none;
  width: 60%;
  height: 50px;
}

.item {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 80%;
  height: 50px;
  margin: 8px auto;
  padding: 16px;
  border-radius: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
}

.del {
  color: red;
}

.completed {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 80%;
  height: 50px;
  margin: 8px auto;
  padding: 16px;
  border-radius: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
  text-decoration: line-through;
  opacity: 0.4;
}
</style>
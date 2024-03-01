<script setup>
import { ref } from "vue"
const toDo = ref({ done: false })
const toDoList = ref([])
function submitfunction() {
  toDoList.value.push({ ...toDo.value })
  toDo.value = { done: false }
}
function deletefunction(searchterm) {
  toDoList.value = toDoList.value.filter((element) => element.title !== searchterm)
}
</script>

<template>
  <header>
    <h1>To-Do List</h1>
  </header>
  <aside>
    <form action="">
      <input type="text" v-model="toDo.title">
      <input type="text" v-model="toDo.description">
      <button type="submit" @click.prevent="submitfunction()" class="btn1">Add</button>
    </form>
  </aside>
  <main>
    <div v-for="element in toDoList">
      <input type="checkbox" v-model="element.done">
      <span>{{ element.title }}</span>
      <span>{{ element.description }}</span>
      <button class="btn2" @click.prevent="deletefunction(element.title)">Delete</button>
    </div>
  </main>
</template>

<style>
body {
  background-color: lightgray;
}

h1 {
  width: 100%;
  color: red;
}

form {
  width: 100%;
  display: flex;

}

.btn1 {
  border: none;
  outline: none;
  padding: 16px 50px;
  color: #fff;
  background: #ff5945;
  font-size: 16px;
  cursor: pointer;
  border-radius: 40px;
}

.btn2 {
  color: lightcoral;
  border: none;
  outline: none;
  padding: 16px 30px;
  border-radius: 20px;

}

input {
  background: lightcoral;
  border: none;
  outline: none;
  border-radius: 40px;
  flex: 1;
  padding: 10px;
  margin-right: 5px;
}
</style>

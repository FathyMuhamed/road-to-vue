<script setup lang="ts">
import { ref } from 'vue'

const inputText = ref<string>('')
const todo = ref<string[]>([])

function addNewTodo() {
  todo.value.push(inputText.value)
  inputText.value = ''
}

function handleRemoveClick(deletedTodo: string) {
  console.log(deletedTodo)
}
</script>

<template>
  <main>
    <input type="text" v-model="inputText" @keypress.enter="addNewTodo" />
    <ul>
      <li class="todo-item" v-for="t in todo" :key="t">
        {{ t }}
        <span @click="($evenet) => handleRemoveClick(t)" class="remove">x</span>
      </li>
    </ul>
  </main>
</template>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  gap: 5px;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}
.remove {
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  color: red;
  border: 1px solid red;
  width: 18px;
  height: 18px;
  text-align: center;
  border-radius: 50%;
}
</style>

<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import AppArray from './components/AppArray.vue'

// import WelcomeItem from './WelcomeItem.vue'
import type { Task } from '@/typing'
import { ref } from 'vue'

// const greeting = ref('Hello du parent')

const id = ref<number>(0)

let inputValue = ref<string>('')
let todoArray = ref<Array<Task>>([])

//Incrémentation et réinitialisation de la l'entrée input
function changeValue(): void {
  id.value++
  inputValue.value = ''
}

//Ajout d'un nouvel élément à notre tableau
function addList(): void {
  todoArray.value.push({
    id: id.value,
    text: inputValue.value,
    etat: false
  })

  changeValue()
  // console.log(todoArray.value)
}
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Acceuil</RouterLink>
      <RouterLink to="/about">Contactez-nous</RouterLink>
      <RouterLink to="/about">A propos</RouterLink>
    </nav>
  </header>
  <div class="contain">
    <h1>TODOLIST</h1>
    <div class="container">
      <form @submit.prevent="addList">
        <label for="">Ajoutez une tâche !</label>
        <br />
        <input
          class="modifinput"
          type="text"
          required
          placeholder="Ajouter une tâche..."
          v-model="inputValue"
        />
        <br />
        <button class="button-62" type="submit">Ajouter</button>
      </form>
    </div>
 
    <AppArray :valueArray="todoArray" />
    <!-- <input type="checkbox">
    <label for="checkbox">Tâches traitée(s)</label><br>
    <input type="checkbox">
    <label for="checkbox">Tâches non traitée(s)</label> -->
  </div>
</template>

<style scoped>
.contain {
  width: 800px;
  background-color: white;
  height: 800px;
  text-align: center;
  box-shadow: rgb(38, 57, 77) 0px 20px 30px -10px;
}

.table {
  border: solid 1px;
  display: flex;
  justify-content: space-around;
  /* width: 100%; */
  margin: 0 auto;
  width: 80%;
  box-shadow:
    rgba(9, 30, 66, 0.25) 0px 4px 8px -2px,
    rgba(9, 30, 66, 0.08) 0px 0px 0px 1px;
}

.editing {
  border: none;
  padding: 8px;
  background-color: #bcd2f7;
}

.button-16 {
  background-color: #f8f9fa;
  border: 1px solid #f8f9fa;
  border-radius: 4px;
  color: #3c4043;
  cursor: pointer;
  font-family: arial, sans-serif;
  font-size: 14px;
  height: 36px;
  line-height: 27px;
  min-width: 54px;
  padding: 0 16px;
  text-align: center;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: pre;
}

.button-16:hover {
  background-color: #6cbe45;
  border-color: #dadce0;
  box-shadow: rgba(0, 0, 0, 0.1) 0 1px 1px;
  color: #ffffff;
}

.button-16:focus {
  border-color: #4285f4;
  outline: none;
}

.modifinput {
  border: none;
  border-radius: 5px;
  box-shadow:
    rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
    rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
  width: 300px;
  height: 25px;
  margin: 10px;
}

label {
  font-weight: bold;
  font-size: 18px;
}

h1 {
  color: blue;
}

table th,
table td {
  padding-inline: 15px;
  padding-block: 5px;
  border: solid 1px;

  border-collapse: collapse;
}

table {
  border-collapse: collapse;
  width: 100%;
}

.button-62 {
  background: linear-gradient(to bottom right, #ef4765, #ff9a5a);
  border: 0;
  border-radius: 12px;
  color: #ffffff;
  cursor: pointer;
  display: inline-block;
  font-family: -apple-system, system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  line-height: 2.5;
  outline: transparent;
  padding: 0 1rem;
  text-align: center;
  text-decoration: none;
  transition: box-shadow 0.2s ease-in-out;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: nowrap;
  margin: 10px;
}

.button-62:not([disabled]):focus {
  box-shadow:
    0 0 0.25rem rgba(0, 0, 0, 0.5),
    -0.125rem -0.125rem 1rem rgba(239, 71, 101, 0.5),
    0.125rem 0.125rem 1rem rgba(255, 154, 90, 0.5);
}

.button-62:not([disabled]):hover {
  box-shadow:
    0 0 0.25rem rgba(0, 0, 0, 0.5),
    -0.125rem -0.125rem 1rem rgba(239, 71, 101, 0.5),
    0.125rem 0.125rem 1rem rgba(255, 154, 90, 0.5);
}



.icons {
  display: flex;
  justify-content: space-around;
}

.icon1 {
  transition: transform 0.2s;
  cursor: pointer;
}

.icon2 {
  transition: transform 0.1s;
  cursor: pointer;
}

.icon1:hover {
  transform: scale(1.1);
}

.icon2:hover {
  transform: scale(1.1);
}
</style>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <p>Utilizo el proposal setup</p>
  <form @submit.prevent="addTodo">
    <input type="text" name="text" v-model="texto" placeholder="Nueva tarea">
  </form>
  <!--HelloWorld msg="Hello Vue 3 + Vite" /-->
  <ul v-if="todos.length">
    <tarea v-for="t in todos" :key="t.id" :tarea="t" @del="delTodo" />
  </ul>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
p  {
  margin-left: auto;
  margin-right: auto;
}

ul {
  padding: 0px;
  margin: 0px;
}
</style>

<script setup>
import { onMounted, ref } from 'vue';
//import HelloWorld from './components/HelloWorld.vue';
import tarea from './components/tarea.vue';


// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md

let id = 0,
    texto = ref('');

const todos = ref([]);
//      state = reactive()

function addTodo()
{
  const trimmed = texto.value.trim();

  console.log("addTodo", texto.value);

  if (trimmed)
    todos.value.push(insTodo(trimmed));

  texto.value = '';
}

function insTodo(text)
{
  return {
    text,
    id: id++
  };
}

function delTodo(tarea)
{
  console.log("eliminado", tarea);
  todos.value = todos.value.filter(todo => todo !== tarea)
}

onMounted(() =>{
  console.log("Montado");
  todos.value.push(insTodo("Mi primera tarea"));
});

</script>
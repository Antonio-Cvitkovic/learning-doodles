<script setup>
import { ref, computed } from 'vue'
import Home from './components/Home.vue'
import About from './components/About.vue'
import Contact from './components/Contact.vue'

const routes = {
  '/': Home,
  '/about': About
}

const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/'] || Contact
})
</script>

<template>

  <img src="./components/icons/vue-transparent.png" id="img1">
  <nav class = navbar>
    <br>
  <button onclick="location.href='#/'">Home </button>
  <button onclick="location.href='#/about'">About</button>
  <button onclick="location.href='#/contact'">Contact</button>
  <component :is="currentView" />
  </nav>



</template>

<style scoped>
@import './assets/base.css';

.navbar{
  text-align: center;
  background: rgb(45 45 45);
  margin: 0%;
}

#img1 {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
  max-width: 20%;
  max-height: 20%;
}

button{
  background-color: #555555;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  cursor: pointer;
  margin-left: 0.25%;
  margin-right: 0.25%;


}

</style>
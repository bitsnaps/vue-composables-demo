<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { ref } from 'vue'
import { useTitle } from '@vueuse/core'
import { useRefHistory } from '@vueuse/core'
import HelloWorld from './components/HelloWorld.vue'


const title = useTitle('Home', {titleTemplate: 'Vite & Vue3 App'})

// Manage Redo/Undo history
const state = ref({})
const { undo } = useRefHistory(state, {
  deep: true,
  capacity: 15
})
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + Vite" />
  
  <p>
    <router-link :to="{ name: 'home' }">Home</router-link>
    |
    <router-link :to="{ name: 'about' }">About</router-link>
  </p>
  <router-view />
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
</style>

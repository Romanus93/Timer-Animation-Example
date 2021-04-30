<template>
  <!-- <CounterEx />
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + TypeScript + Vite" />
  <Counter /> -->
  <h1>-----------</h1>
  <Container />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
// import Counter from './components/Counter.vue'
// import CounterEx from './components/CounterEx.vue'
import Container from './pages/Container.vue'

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,
    // Counter,
    // CounterEx,
    Container
  }
})
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.png" width="50" height="50" />
    <h1>Vue App by Nadia</h1>
  </header>

  <main>
    <section class="click-counter">
        <div class="section-box">
        <h2>Click Counter</h2>
        <div class="counter-number">{{ counter }}</div> 
        <button class="primary-btn" @click="incrementCounter">
        Click to Count 
      </button>
      </div>
    </section>
    
  </main>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

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

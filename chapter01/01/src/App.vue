<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <div class="app">
    <div class="logos">
      <a href="https://vitejs.dev" target="_blank">
        <img src="/favicon.svg" class="logo" alt="Vite logo" />
      </a>
      <a href="https://vuejs.org/" target="_blank">
        <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
      </a>
    </div>

    <h1 class="title">Vite + Vue</h1>

    <button class="btn" @click="count++">count is {{ count }}</button>
    <p class="tip">Edit components/HelloWorld.vue to test HMR</p>

    <div class="info">
      <p>我的第一个 Vue 界面</p>
      <p>江贤松</p>
      <p>32605150615</p>
    </div>

    <div class="links">
      <p>
        Check out
        <a href="https://github.com/vuejs/create-vue" target="_blank">create-vue</a>,
        the official Vue + Vite starter
      </p>
      <p>Install Volar in your IDE for a better DX</p>
      <p>Click on the Vite and Vue logos to learn more</p>
    </div>
  </div>
</template>

<style scoped>
.app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  text-align: center;
}
.logos {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 2rem;
}
.logo {
  height: 6em;
}
.logo.vue {
  height: 6.5em;
}
.title {
  font-size: 3.2rem;
  font-weight: 700;
  margin: 1.5rem 0;
}
.btn {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  background-color: #f9f9f9;
  cursor: pointer;
}
.btn:hover {
  border-color: #42b883;
}
.tip {
  color: #888;
  margin-top: 1rem;
}
.info p {
  font-size: 1.3rem;
  font-weight: 600;
  color: #42b883;
  line-height: 1.8;
}
.links {
  margin-top: 3rem;
  color: #888;
  font-size: 0.95rem;
  line-height: 1.9;
}
.links a {
  color: #42b883;
  text-decoration: none;
}
</style>

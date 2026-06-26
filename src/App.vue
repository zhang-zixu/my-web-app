<script setup>
import { ref } from 'vue'

const count = ref(10)
const version = 'develop'
const features = ['新配色方案', '优化按钮样式', '开发环境预览']
</script>

<template>
  <div class="container">
    <h1>🌿 My Web App</h1>
    <p>Vue 3 + Vite · <strong>Develop</strong> 分支开发中</p>
    <span class="badge">{{ version }} · GitHub Actions + Docker</span>

    <ul class="features">
      <li v-for="item in features" :key="item">{{ item }}</li>
    </ul>

    <div class="counter">
      <button @click="count--">−</button>
      <span>{{ count }}</span>
      <button @click="count++">+</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  text-align: center;
  padding: 2.5rem;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 1.5rem;
  backdrop-filter: blur(8px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15);
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 0.75rem;
}

p {
  font-size: 1.15rem;
  opacity: 0.95;
}

.badge {
  display: inline-block;
  margin-top: 1rem;
  padding: 0.4rem 1rem;
  background: rgba(255, 255, 255, 0.25);
  border-radius: 2rem;
  font-size: 0.85rem;
  letter-spacing: 0.5px;
}

.features {
  list-style: none;
  margin-top: 1.5rem;
  padding: 0;
}

.features li {
  display: inline-block;
  margin: 0.25rem 0.5rem;
  padding: 0.35rem 0.85rem;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 1rem;
  font-size: 0.9rem;
}

.counter {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1.25rem;
  margin-top: 2rem;
}

.counter button {
  width: 2.75rem;
  height: 2.75rem;
  border: 2px solid rgba(255, 255, 255, 0.4);
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
  color: #fff;
  font-size: 1.25rem;
  cursor: pointer;
  transition: all 0.2s;
}

.counter button:hover {
  background: rgba(255, 255, 255, 0.45);
  transform: scale(1.05);
}

.counter span {
  font-size: 1.75rem;
  font-weight: 600;
  min-width: 2.5rem;
}
</style>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
  color: #fff;
}

#app {
  width: 100%;
  max-width: 480px;
  padding: 1rem;
}
</style>

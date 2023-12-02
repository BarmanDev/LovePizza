<template>
  <header>
    <nav>
      <div class="logo-container">
        <img class="img-logo" src="../assets/favicon.png" alt="Logo de la Pizzería">
      </div>
      <ul>
        <li><router-link to="/" class="nav-link">Inicio</router-link></li>
        <li><router-link to="/about" class="nav-link">Pedidos</router-link></li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Header',
});
</script>

<style scoped>
nav {
  height: 120px;
  background-color: var(--color-green);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.logo-container {
  display: flex;
  align-items: center;
}

.img-logo {
  max-width: 100px; 

}

ul {
  list-style: none;
  display: flex;
  gap: 20px;
}

li {
  font-size: 1.5rem; 
  font-family: Arial, Helvetica, sans-serif;
  text-transform: uppercase;
  font-weight: bold;
}

.nav-link {
  color: var( --color-red-pomodoro); 
  text-decoration: none; 
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #fff; 
}
</style>

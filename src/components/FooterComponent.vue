<template>
  <footer>
    <div class="footer-container">
      <p>&copy; 2023 VUE PIZZA</p>
      <ul>
        <li class="footer-link">Contacto</li>
        <li class="footer-link">Política de privacidad</li>
      </ul>
    </div>
  </footer>
</template>


<style>
.footer-container{
  background-color: var(--color-green);
  color: var( --color-red-pomodoro); 
  padding: 20px;
  text-align: center;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;

}

.footer-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

ul {
  list-style: none;
  display: flex;
  gap: 20px;
}

</style>


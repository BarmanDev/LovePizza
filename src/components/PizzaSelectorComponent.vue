<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      selectedPizza: "" as string,
      pizzas: [
        {
          nombre: "4 Quesos",
          ingredientes: ["Mozzarella", "Gorgonzola", "Parmesano", "Ricotta"]
        },
        {
          nombre: "Pepperoni",
          ingredientes: ["Mozzarella", "Pepperoni", "Tomate"]
        },
        {
          nombre: "Hawaiana",
          ingredientes: ["Mozzarella", "Jamón", "Piña"]
        },
        {
          nombre: "Margherita",
          ingredientes: ["Mozzarella", "Tomate", "Albahaca"]
        },
        {
          nombre: "Vegetariana",
          ingredientes: ["Mozzarella", "Tomate", "Pimientos", "Cebolla", "Aceitunas"]
        },
        {
          nombre: "Mexicana",
          ingredientes: ["Mozzarella", "Carne molida", "Pimientos", "Cebolla", "Chiles jalapeños"]
        },
        {
          nombre: "Barbacoa",
          ingredientes: ["Mozzarella", "Carne de res", "Cebolla caramelizada", "Salsa barbacoa"]
        },
        {
          nombre: "Mariscos",
          ingredientes: ["Mozzarella", "Langostinos", "Calamares", "Mejillones", "Salsa de tomate"]
        },
        {
          nombre: "Caprese",
          ingredientes: ["Mozzarella", "Tomate fresco", "Albahaca", "Aceite de oliva"]
        },
        {
          nombre: "Diavola",
          ingredientes: ["Mozzarella", "Pepperoni picante", "Aceitunas negras", "Chiles rojos"]
        },
        {
          nombre: "Pollo BBQ",
          ingredientes: ["Mozzarella", "Pollo a la barbacoa", "Cebolla", "Salsa BBQ"]
        },
        {
          nombre: "Primavera",
          ingredientes: ["Mozzarella", "Tomate cherry", "Espinacas", "Champiñones", "Aceitunas"]
        }
      ] as { nombre: string; ingredientes: string[] }[],
      ingredientes: [] as string[],
      preparacion: "" as string,
      pedidoRealizado: "" as string
    };
  },
  methods: {
    mostrarIngredientes() {
      const selectedPizza = this.pizzas.find(pizza => pizza.nombre === this.selectedPizza);
      if (selectedPizza) {
        this.ingredientes = selectedPizza.ingredientes;
        this.preparacion = ""; 
      } else {
        this.ingredientes = [];
        this.preparacion = "";
      }
    },
    prepararPizza() {
      const selectedPizza = this.pizzas.find(pizza => pizza.nombre === this.selectedPizza);
      if (selectedPizza) {
        this.ingredientes = [];
        this.preparacion = `<h2>Preparación de ${selectedPizza.nombre}:</h2>`;
        this.preparacion += "<p> Extender la masa</p>";
        this.preparacion += "<p> Agregar la salsa de tomate</p>";
        this.preparacion += "<p> Agregar el queso mozzarella</p>";

        selectedPizza.ingredientes.forEach(ingrediente => {
          this.preparacion += `<p> Agregar ${ingrediente}</p>`;
        });

        this.preparacion += "<p> Hornear la pizza</p>";
      } else {
        this.ingredientes = [];
        this.preparacion = "";
      }
    },
    realizarPedido() {
      if (this.selectedPizza) {
        this.pedidoRealizado = `Su pedido de ${this.selectedPizza} se ha realizado correctamente.`;
      } else {
        this.pedidoRealizado = "Por favor, seleccione una pizza antes de realizar el pedido.";
      }
    }
  }
});
</script>


<template>
  <form>
    <label for="pizzaSelect">Elige una pizza:</label>
    <select v-model="selectedPizza" @input="mostrarIngredientes">
      <option value="" disabled selected>Selecciona una pizza</option>
      <option v-for="pizza in pizzas" :key="pizza.nombre" :value="pizza.nombre">{{ pizza.nombre }}</option>
    </select>
    <button type="button" @click="mostrarIngredientes">Mostrar Ingredientes</button>
    <button type="button" @click="prepararPizza">Preparar Pizza</button>
    <button type="button" @click="realizarPedido">Realizar pedido</button>
  </form>
  
  <div id="resultado">
    <h2 v-if="selectedPizza">Resultado para {{ selectedPizza }}:</h2>
    <ul v-if="selectedPizza">
      <li v-for="ingrediente in ingredientes" :key="ingrediente">{{ ingrediente }}</li>
    </ul>
    <p v-if="preparacion" v-html="preparacion"></p>
    <p v-if="pedidoRealizado">{{ pedidoRealizado }}</p>
  </div>
</template>


<style scoped>
  form {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  label {
    margin-bottom: 10px;
    font-size: 1.2rem;
    color: #333;
  }

  select {
    margin-bottom: 15px;
    padding: 10px;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 5px;
  }

  button {
    margin-bottom: 15px;
    padding: 10px 15px;
    font-size: 1rem;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  button:hover {
    background-color: #45a049;
  }

  #resultado {
    margin-top: 20px;
    padding: 20px;
    border: 1px solid #4caf50;
    border-radius: 5px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }

  h2 {
    font-size: 1.5rem;
    color: #4caf50;
    margin-bottom: 10px;
  }

  ul {
    list-style: none;
    padding: 0;
  }

  li {
    margin-bottom: 5px;
    font-size: 1rem;
    color: #333;
  }

  p {
    font-size: 1rem;
    color: #333;
  }

  .preparacion {
    margin-top: 20px;
    padding: 20px;
    border: 1px solid #4caf50;
    border-radius: 5px;
    background-color: #e6ffe6;
  }

  .preparacion h2 {
    font-size: 1.5rem;
    color: #4caf50;
    margin-bottom: 10px;
  }

  .preparacion p {
    font-size: 1rem;
    color: #333;
  }
</style>



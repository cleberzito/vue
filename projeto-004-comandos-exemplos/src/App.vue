<template>
  <h1>Preço inicial {{preco}}</h1>
  <ul>
    <li v-for="produto in produtos" :key="produto.name" :class="{red: (preco > produto.preco)}">{{produto.preco}} - {{produto.name}}</li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  data() {
    return {
      preco: 41,
      produtos: [
          { id: 1, name: 'Camisa', preco: (Math.round(Math.random()*100)), stock: true  },
          { id: 2, name: 'Camisa', preco: (Math.round(Math.random()*100)), stock: false },
          { id: 3, name: 'Camisa', preco: (Math.round(Math.random()*100)), stock: false },
          { id: 4, name: 'Camisa', preco: (Math.round(Math.random()*100)), stock: true  }
      ]
    }
  },
  mounted() {
    this.preco = Math.round(Math.random()*100)
  }
});
</script>

<style scoped>
  .red {
    color: #FF0000;
  }
</style>
<template>
  <div>
    <p><strong>this.pessoa.nome:</strong> {{ pessoa.nome }}</p>
    <p><strong>this.pessoa.sobrenome:</strong> {{ pessoa.sobrenome }}</p>
    <p><strong>computed:</strong> nomeCompleto » {{ nomeCompleto }}</p>
    <h2>{{ contador }}</h2>
    <button @click="adicao">adição</button>
    <button @click="subtracao">subtração</button>
    <button @click="reset">reset</button>
    <div>
      <small>{{ contadorAlterado }}</small>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

interface Pessoa {
  nome: string;
  sobrenome: string;
  idade: number;
}

export default defineComponent({
  data() {
    return {
      pessoa: {} as Pessoa,
      email: "",
      contador: 0,
      contadorAlterado: "",
    };
  },
  created() {
    this.pessoa.nome = "Cleber";
    this.pessoa.sobrenome = "Costa";
    this.pessoa.idade = 41;
    this.email = "cleber.email@gmail.com";
  },
  computed: {
    nomeCompleto(): string {
      return `${this.pessoa.nome} ${this.pessoa.sobrenome}`;
    },
  },
  watch: {
    contador(newValue, oldValue) {
      this.contadorAlterado = `newValue ${newValue} oldValue ${oldValue}`;
    },
  },
  methods: {
    adicao() {
      this.contador++;
    },
    subtracao() {
      this.contador--;
    },
    reset() {
      this.contador = 0;
    },
  },
});
</script>

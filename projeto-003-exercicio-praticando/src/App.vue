<template>
  <ul>
    <li>[x] Definir o dado todos</li>
    <li>[x] Preencher os todos quando o componente é criado</li>
    <li>[X] Exibir em tela apenas todos concluídos</li>
    <li>[x] Ter um método para concluir os todos</li>
    <li>[] Mostrar um alerta quando todos os todos forem finalizados</li>
  </ul>
  <h1>Tarefas concluídas</h1>
  <ul>
    <li v-for="tarefa in tarefasConcluidas" :key="tarefa">
      {{ tarefa.tarefa }}
    </li>
  </ul>
  <button @click="concluirTarefas">Concluir tarefas</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

interface Tarefas {
  tarefa: string;
  status: boolean;
}

export default defineComponent({
  data() {
    return {
      tarefas: [] as Tarefas[],
    };
  },
  created() {
    this.tarefas = [
      { tarefa: "Estudar Typescript", status: true },
      { tarefa: "Lavar os pratos", status: false },
      { tarefa: "Aprender Nuxt.js", status: true },
    ];
  },
  computed: {
    tarefasConcluidas(): Tarefas[] {
      return this.tarefas.filter((tarefa) => tarefa.status);
    },
  },
  watch: {
    tarefas(newValue: Tarefas[]) {
      const finalizado = !newValue.some(({status}) => !status);
      if (finalizado) alert("Finalizados");
    },
  },
  methods: {
    concluirTarefas() {
      this.tarefas = this.tarefas.map((tarefa) => {
        tarefa.status = true;
        return tarefa;
      });
    },
  },
});
</script>

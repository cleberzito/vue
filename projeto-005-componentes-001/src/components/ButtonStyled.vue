<template>
  <button :class="['button-styled', color]">
    {{ text }}
    {{ user }}
    <span>Teste de Sistema</span>
  </button>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue"

type color = "success" | "primary" | "danger"

interface User {
  id: number
  nome: string
}

export default defineComponent({
  props: {
    text: {
      type: String,
      default: "Texto padrão",
    },
    color: {
      type: String,
      default: "primary",
      validator: (value: color) => {
        return ["primary", "danger", "success"].includes(value)
      },
    },
    user: {
      type: Object as PropType<User>,
      require: true,
    },
  },
})
</script>

<style scoped>
.button-styled {
  color: #fff;
  border-radius: 0.3rem;
  padding: 0.5rem 1rem;
  outline: none;
  border: none;
  cursor: pointer;
  display: block;
  margin-bottom: 1rem;
  background-color: #2d6cea;
}

.success {
  background: green;
}
.primary {
  background: #2d6cea;
}
.danger {
  background: red;
}
</style>

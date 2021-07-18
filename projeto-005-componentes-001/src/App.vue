<template>
  <ButtonStyled text="Cadastro" />
  <ButtonStyled text="Login" />
  <ButtonStyled />
</template>

<script lang="ts">
/* eslint-disable */
import { defineComponent } from "vue"
import ButtonStyled from "@/components/ButtonStyled.vue"

export default defineComponent({
  components: {
    ButtonStyled,
  },
})
</script>

<style scoped>
.button-styled {
  border-bottom: 3px solid #a00;
}

::v-deep.button-styled span {
  color: #ffff00;
}
</style>

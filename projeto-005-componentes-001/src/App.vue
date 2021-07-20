<template>
  <ButtonStyled text="Cadastro" color="danger" :user="user" />
  <ButtonStyled text="Login" color="success" :user="user" />
  <ButtonStyled :user="user" />
</template>

<script lang="ts">
import { defineComponent } from "vue"
import ButtonStyled from "@/components/ButtonStyled.vue"

export default defineComponent({
  components: {
    ButtonStyled,
  },
  data() {
    return {
      user: {
        id: 1,
        name: "cleber",
      },
    }
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

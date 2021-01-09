<template>
  <div id="app">
    <br /><Titulo /><br />
          <Usuario /><br />
          <Conversa />
  </div>
</template>

<script>
import Usuario from "./components/Usuario.vue";
import Titulo from "./components/Titulo.vue";
import Conversa from "./components/Conversa.vue";

export default {
  name: "app",
  components: {
    Usuario,
    Titulo,
    Conversa,
  },
};
</script>

<style></style>

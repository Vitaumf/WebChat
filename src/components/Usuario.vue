<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-sm">
        <div class="card-header">
          <form @submit.prevent="enviaMensagem">
            <div class="gorm-group">
              <label for="nome">Nome:</label>
              <input type="text" v-model="nome" class="form-control"/>
            </div>
            <div class="gorm-group pb-3">
              <label for="mensagem">Mensagem:</label>
              <input type="text" v-model="mensagem" class="form-control" />
            </div>
            <button type="submit" class="btn btn-primary">Enviar</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import io from "socket.io-client";

export default {
  data() {
    return {
      nome: "",
      mensagem: "",
      socket: io("localhost:3001"),
    };
  },
  methods: {
    enviaMensagem(e) {
      e.preventDefault();
      this.socket.emit("mensagem1", {
        nome: this.nome,
        mensagem: this.mensagem,
      });
      this.mensagem = "";
    },
  },
};
</script>

<style></style>

<template>
  <div class="container-fluid">
    <div class="card bg-primary text-white">
      <div class="card-body">
        <div class="mensagens" v-for="(msg, index) in mensagens" :key="index">
          <p>
            <span class="font-weight-bold">{{ msg.nome }} </span
            >{{ msg.mensagem }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import io from "socket.io-client";
import axios from "axios";

export default {
  data() {
    return {
      posts: [],
      errors: [],
      mensagens: [],
      socket: io("localhost:3001"),
    };
  },

  created() {
    axios
      .get(`http://localhost:3001/`)
      .then((response) => {
        this.posts = response.data;
        this.mensagens = this.posts;
        console.log(this.posts);
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
  mounted() {
    this.socket.on("mensagem2", (data) => {
      this.mensagens = [...this.mensagens, data];
    });
  },
};
</script>

<style></style>

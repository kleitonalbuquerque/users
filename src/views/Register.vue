<template>
  <div>
    <h3 class="title is-3">Cadastro de Usuário</h3>
    <hr />
    <div class="columns is-mobile">
      <div class="column is-half is-offset-one-quarter">
        <div v-if="error != undefined">
          <div class="notification is-danger">
            {{ error }}
          </div>
        </div>
        <label class="label">Nome:</label>
        <input
          type="text"
          placeholder="Nome do usuário"
          class="input"
          v-model="name"
        />
        <label class="label">E-mail:</label>
        <input
          type="email"
          placeholder="E-mail"
          class="input"
          v-model="email"
        />
        <label class="label">Senha:</label>
        <input
          type="password"
          placeholder="******"
          class="input"
          v-model="password"
        />
        <!-- TO DO -->
        <!-- Select com as opções de tipo de usuário: Comum(0) e Admin(1)  -->
        <hr />
        <button class="button is-success" @click="register">Cadastrar</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      name: "",
      email: "",
      password: "",
      error: undefined,
    };
  },
  methods: {
    register() {
      axios
        .post("http://localhost:8686/user", {
          name: this.name,
          email: this.email,
          password: this.password,
        })
        .then((data) => {
          console.log(data);
          this.$router.push({ name: "Home" });
        })
        .catch((err) => {
          let msgErro = err.response.data.err;
          this.error = msgErro;
        });
      // console.log(this.name);
      // console.log(this.email);
      // console.log(this.password);
    },
  },
};
</script>

<style></style>

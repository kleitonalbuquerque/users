<template>
  <div>
    <h3 class="title is-3">Login</h3>
    <hr />
    <div class="columns is-mobile">
      <div class="column is-half is-offset-one-quarter">
        <div v-if="error != undefined">
          <div class="notification is-danger">
            {{ error }}
          </div>
        </div>
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
        <button class="button is-success" @click="login">Logar</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      email: "",
      password: "",
      error: undefined,
    };
  },
  methods: {
    login() {
      axios
        .post("http://localhost:8686/login", {
          email: this.email,
          password: this.password,
        })
        .then((res) => {
          console.log(res);
          localStorage.setItem("token", res.data.token);
          this.$router.push({ name: "Home" });
        })
        .catch((err) => {
          let msgErro = err.response.data.err;
          this.error = msgErro;
        });
    },
  },
};
</script>

<style></style>

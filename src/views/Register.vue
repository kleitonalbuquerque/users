<template>
  <div>
    <h3 class="title is-3">Cadastro de Usuário</h3>
    <hr />
    <div class="columns is-mobile">
      <div class="column is-half is-offset-one-quarter">
        <label class="label">Nome:</label>
        <input type="text" placeholder="Nome do usuário" class="input" />
        <label class="label">E-mail:</label>
        <input type="email" placeholder="E-mail" class="input" />
        <label class="label">Senha:</label>
        <input type="password" placeholder="******" class="input" />
        <!-- TO DO -->
        <!-- Select com as opções de tipo de usuário: Comum(0) e Admin(1)  -->
        <hr />
        <button class="button is-success">Cadastrar</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style></style>

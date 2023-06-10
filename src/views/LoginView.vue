<script setup>
  import { reactive, onMounted } from 'vue'

  const user = reactive({
    email: '',
    password: ''
  })

  function login() {
    console.log(user.email, user.password);
  }
</script>

<template>
  <h1 class="text-blue-900 font-bold text-3xl">Login</h1>

  <form action="" @submit.prevent="login">
    <input type="text" placeholder="Email" v-model="user.email">
    <input type="text" placeholder="Senha" v-model="user.password">

    <button type="submit">Login</button>
  </form>
</template>

<style>
</style>


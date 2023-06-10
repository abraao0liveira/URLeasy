<script setup>
  import { reactive } from 'vue'

  const user = reactive({
    name: '',
    email: '',
    password: ''
  })

  function login() {
    console.log(user.name, user.email, user.password);
  }
</script>

<template>
    <form action="" @submit.prevent="login">
      <div>
        <h1>Cadastre-se</h1>
        <input type="text" placeholder="Nome" v-model="user.name">
        <input type="text" placeholder="Email" v-model="user.email">
        <input type="text" placeholder="Senha" v-model="user.password">
  
        <button type="submit">Entrar</button>
      </div>
    </form>
  </template>

<style>
form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
form div {
  width: 22%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 2.188rem 1.25rem;
  background-color: var(--gray-800);
  border-radius: 0.938rem;
  box-shadow: 0px 10px 40px #00000056;
}
form div h1 {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 1.5rem;
}
form div input {
  border: none;
  border-radius: 0.5rem;
  padding: 0.75rem;
  background: var(--gray-700);
  color: var(--white);
  font-size: 12pt;
  outline: none;
  box-sizing: border-box;
  margin-bottom: 1rem;
}
form div button {
  width: 65%;
  padding: 0.75rem 0rem;
  margin: 0.75rem;
  border: none;
  border-radius: 0.5rem;
  outline: none;
  text-transform: uppercase;
  font-weight: 700;
  letter-spacing: 0.188rem;
  color: var(--white);
  background: var(--green-500);
  cursor: pointer;
}
form div button:hover {
  filter: brightness(0.9);
  transition: filter 0.2s;
}
</style>


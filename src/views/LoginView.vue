<script setup>
  import { reactive } from 'vue'
  import { useRouter } from 'vue-router'

  const router = useRouter()

  const user = reactive({
    email: '',
    password: ''
  })

  function login() {
    const savedUser = JSON.parse(localStorage.getItem('user'))
    
    if (savedUser && user.email === savedUser.email && user.password === savedUser.password) {
      console.log('Login bem-sucedido!')
      router.push('/user')
    } else {
      alert('Email ou senha incorretos!')
      return
    }
  }
</script>

<template>
  <form action="" @submit.prevent="login">
    <div>
      <img src="../assets/link.svg" alt="">

      <input type="text" placeholder="Email" v-model="user.email">
      <input type="password" placeholder="Senha" v-model="user.password">

      <button type="submit" @click="login">Entrar</button>
      <a href="/signIn">Cadastre-se</a>
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
  form div img {
    width: 2.5rem;
    margin-bottom: 1.563rem;
    background: var(--green-500);
    border-radius: 50%;
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
    border-radius: 0.938rem;
    outline: none;
    font-weight: 700;
    color: var(--white);
    background: var(--green-500);
    cursor: pointer;
  }
  form div button:hover {
    filter: brightness(0.9);
    transition: filter 0.2s;
  }
  form div a {
    text-decoration: none;
    color: var(--green-300);
    font-size: 10pt;
    border: none;
    border-radius: 0.188rem;
  }
</style>


<script setup>
  
</script>

<template>
  <nav>
    <img src="../assets/link.svg" alt="linkLogo">
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/login">Login</RouterLink>
  </nav>
</template>

<style>
  nav img {
    margin: auto;
    margin-left: -1rem;
    height: 2.25rem;
    width: 2.25rem;
    background: var(--green-500);
    border-radius: 50%;
  }
  nav {
    background-color: var(--gray-800);
    padding: 1.25rem 3.125rem;
    
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }
  nav a {
    background: var(--green-500);
    color: var(--white);
    text-decoration: none;
    margin-left: 1.25rem;
    font-weight: bold;
    padding: 0 1rem;
    border: 0;
    border-radius: 6px;
    cursor: pointer;
  }
  nav a:hover {
    background: var(--green-700);
    transition: background-color 0.2s;
  }
</style>

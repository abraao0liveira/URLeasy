<script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import Menu from './components/Menu.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <Menu />
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style>

</style>

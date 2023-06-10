<script>
  import { RouterView } from 'vue-router'
  import Header from './components/Header.vue'

  export default {
  components: {
    Header,
  },
  computed: {
    notIsLoginPage() {
      return this.$route.name !== 'login' && this.$route.name !== 'signIn'
    }
  }
}
</script>

<template>
  <Header v-if="notIsLoginPage" />

  <RouterView />
</template>

<style>
</style>

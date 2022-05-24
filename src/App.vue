<template>
  <div id="app">
    <!-- Header  -->
    <AppHeader :class="{ scrolled: isScrolled }" />

    <!-- Game -->
    <TicTacToe />

    <!-- Footer -->
    <AppFooter />
  </div>
</template>

<script>
import Vue from 'vue'

import TicTacToe from './components/tic-tac-toe/tic-tac-toe'
import AppHeader from './components/app/app-header'
import AppFooter from './components/app/app-footer'

export default Vue.extend({
  name: 'app',

  components: {
    AppHeader,
    AppFooter,
    TicTacToe,
  },

  data() {
    return {
      scrollPosition: null,
    }
  },

  computed: {
    isScrolled() {
      return this.scrollPosition > 150
    },
  },

  methods: {
    updateScroll() {
      this.scrollPosition = window.scrollY
    },
  },

  mounted() {
    window.addEventListener('scroll', this.updateScroll)
  },
})
</script>

<style>
#app {
  font-family: 'Glacial Indifference', 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

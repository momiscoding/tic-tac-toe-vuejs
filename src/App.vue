<template>
  <div id="app">
    <!-- AppHeader  -->
    <AppHeader :class="{ scrolled: isScrolled }" />

    <!-- TicTacToe -->
    <TicTacToe />

    <!-- AppFooter -->
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
    TicTacToe,
    AppHeader,
    AppFooter,
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

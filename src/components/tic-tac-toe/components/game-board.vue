<template>
  <div class="game-board">
    <div v-for="row in 3" :key="row">
      <GameCell
        v-for="i in 3"
        :key="indexByRow(i, row)"
        :token="cells[indexByRow(i, row)]"
        :disabled="!!winner"
        :winner="!!winner && winner.includes(indexByRow(i, row))"
        @click="click(i, row)"
      />
    </div>
  </div>
</template>

<script>
import GameCell from './game-cell.vue'

export default {
  name: 'GameBoard',

  components: { GameCell },

  props: {
    cells: Array,
    winner: Array,
  },

  methods: {
    indexByRow(index, row, max = 3) {
      return row * max + index - (max + 1)
    },
    click(index, row) {
      this.$emit('click', this.indexByRow(index, row))
    },
  },
}
</script>

<style lang="scss">
.game-board {
  display: flex;
  flex-wrap: wrap;
  width: 204px;
  height: 204px;
  margin: 0 auto;
}
</style>

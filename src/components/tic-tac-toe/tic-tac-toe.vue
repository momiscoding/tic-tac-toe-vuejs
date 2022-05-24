<template>
  <div class="tic-tac-toe">
    <div class="container bg-light">
      <div class="row">
        <h4>Tic tac toe games</h4>
        <p>Welcome to the best game in the world.</p>
        <div class="col-md-6 order-md-2">
          <GameBoard :cells="cells" :winner="winner" @click="click" />
        </div>
        <!-- TODO: This could become a component - someday.... -->
        <div class="col col-md-3 order-1 order-md-1 game__player">
          <p class="fs-5 fw-bold">Player 1</p>
          <p class="fs-1">{{ playerXVictories }}</p>
          <span v-if="playerXVictories == matchesToWin">WINNER! 🥳</span>
        </div>
        <div class="col col-md-3 order-3 order-md-3 game__player">
          <p class="fs-5 fw-bold">Player 2</p>
          <p class="fs-1">{{ playerOVictories }}</p>
          <span v-if="playerOVictories == matchesToWin">WINNER! 🥳</span>
        </div>
        <div class="col col-md-3 order-2 order-md-4 game__timer">
          <GameTimer ref="timer" />
        </div>
      </div>
    </div>
    <div
      v-if="
        playerXVictories == matchesToWin || playerOVictories == matchesToWin
      "
    >
      <GameStatistics
        :limit="matchesLimit"
        :played-matches="playedMatches"
        :history="gameHistory"
        :totalTime="timeElapsed"
      />
    </div>
  </div>
</template>

<script>
import Vue from 'vue'

import GameBoard from './components/game-board.vue'
import GameStatistics from './components/game-statistics/game-statistics.vue'
import GameTimer from './components/game-timer.vue'

export default Vue.extend({
  name: 'TicTacToe',

  components: {
    GameBoard,
    GameStatistics,
    GameTimer,
  },

  data() {
    return {
      cells: Array(9).fill(null),
      stepNumber: 0,
      currentPlayer: 'X',
      winner: null,
      playerXVictories: 0,
      playerOVictories: 0,
      playsCounter: 0,
      playedMatches: 0,
      matchesLimit: 9,
      gameHistory: [],
      matchesToWin: 5,
      timeElapsed: '00:00:00',
    }
  },

  watch: {
    stepNumber: function (val) {
      // It's a tie
      if (val === 9) {
        this.gameHistory.push('-')
        this.restart()
      }
    },
  },

  // mounted() {
  //   setTimeout(() => {
  //     this.$watch(
  //       () => this.$refs.timer.timeElapsed,
  //       value => {
  //         this.timeElapsed = value;
  //       }
  //     );
  //   }, 2000);
  // },

  methods: {
    hasWinner() {
      if (this.winner) return true
      const cells = this.cells
      const matches = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6],
      ]
      for (let i = 0; i < matches.length; i++) {
        const [a, b, c] = matches[i]
        if (cells[a] && cells[a] === cells[b] && cells[a] === cells[c]) {
          this.winner = [a, b, c]

          // Number os wins per player
          this.currentPlayer === 'X'
            ? this.playerXVictories++
            : this.playerOVictories++

          // Populate game history
          this.gameHistory.push(this.currentPlayer)

          this.restart()

          return true
        }
      }
      return false
    },

    restart() {
      this.playedMatches++

      // Stop timer
      this.$refs.timer.stop()

      setTimeout(() => {
        this.cells = Array(9).fill(null)
        this.stepNumber = 0
        // this.currentPlayer = this.currentPlayer;
        this.winner = null
        this.playsCounter++
      }, 2000)
    },

    click(i) {
      if (
        this.cells[i] ||
        this.winner ||
        this.playedMatches === this.matchesLimit ||
        this.playerXVictories == this.matchesToWin ||
        this.playerOVictories == this.matchesToWin
      )
        return

      // start timer
      this.$refs.timer.start()

      this.$set(this.cells, i, this.currentPlayer)
      if (!this.hasWinner()) {
        this.stepNumber++
        this.currentPlayer = this.currentPlayer === 'X' ? 'O' : 'X'
      }
    },
  },
})
</script>

<style lang="scss">
.tic-tac-toe {
  max-width: 100%;
  padding: 65px;

  .game {
    &__player {
      margin: auto 0;
    }

    @media only screen and (min-width: 768px) {
      &__timer {
        width: 100%;
      }
    }
  }
}
</style>

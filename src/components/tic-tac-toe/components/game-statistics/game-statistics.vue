<template>
  <div class="game-statistics">
    <div class="container bg-white">
      <div class="row">
        <h4>Awesome statistics</h4>
        <p>All statistics in one place!</p>
      </div>
      <div class="row">
        <div class="col-md-6">
          <h6>Game victories %</h6>
          <!-- TODO: Add input to insert player name -->
          <GameStatisticsPlayer :playerName="`Player 1`" stats="" />
          <GameStatisticsPlayer :playerName="`Player 2`" stats="" />
        </div>
        <div class="col-md-6">
          <div class="game-statistics__section">
            <h6>Played matches</h6>
            <div>
              <div
                v-for="i in limit"
                :key="i"
                :class="[
                  i <= playedMatches ? 'matches--played' : '',
                  'matches',
                ]"
              ></div>
            </div>
          </div>
          <div class="game-statistics__section">
            <h6>Game history</h6>
            <div>
              <div v-for="(item, index) in limit" :key="index" class="history">
                <span>{{ mappedHistory[index] }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="row">
        <h4>Total time</h4>
        <span>{{ totalTime }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import GameStatisticsPlayer from './components/game-statistics-player.vue'

const mapPlayer = {
  X: 'P1',
  O: 'P2',
}

export default {
  name: 'GameStatistics',

  components: {
    GameStatisticsPlayer,
  },

  props: {
    limit: Number,

    playedMatches: {
      type: Number,
      default: 0,
    },

    history: Array,

    totalTime: {
      type: String,
      default: '00:00:00',
    },
  },

  computed: {
    mappedHistory() {
      const result = this.history.map((res) => {
        return mapPlayer[res] || res
      })
      return result
    },
  },
}
</script>

<style lang="scss">
.game-statistics {
  padding: 65px;

  &__section {
    display: inline-block;
    padding-bottom: 20px;
  }
}

.matches,
.history {
  float: left;
  width: 25px;
  height: 25px;
  margin-right: 5px;
  border: 1px solid grey;
}

.matches {
  border-radius: 50%;

  &:last-of-type {
    margin: 0;
  }

  &--played {
    background-color: #00dca4;
    border: none;
  }
}
</style>

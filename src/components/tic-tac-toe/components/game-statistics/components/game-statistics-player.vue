<template>
  <div class="game-statistics-player">
    <p>{{ name }}</p>
    <div class="game-statistics-player__numbers">0%<br /><span>V</span></div>
    <div class="game-statistics-player__numbers">0%<br /><span>L</span></div>
  </div>
</template>

<script>
export default {
  name: "GameStatisticsPlayer",

  props: {
    name: String
    // stats: {
    //   type: Object,
    //   default: function() {
    //     return { victories: "0", losses: "0" };
    //   }
    // }
  }
};
</script>

<style lang="scss">
.game-statistics-player {
  float: left;
  width: inherit;

&__numbers {
  display: inline-block;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background-color: grey;
  color: white;
  padding-top: 3px;
}

&__numbers > span {
  color: black;
  }
}
</style>

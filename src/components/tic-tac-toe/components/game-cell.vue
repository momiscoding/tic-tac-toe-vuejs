<template>
  <div @click="$emit('click')" class="cell" :class="[playerToken]">
    <span>{{ token }}</span>
  </div>
</template>

<script>
export default {
  name: 'GameCell',

  props: {
    token: String,
  },

  computed: {
    playerToken() {
      return {
        'x-token': this.token && this.token === 'X',
        'o-token': this.token && this.token === 'O',
      }
    },
  },
}
</script>

<style>
.cell {
  width: 64px;
  height: 64px;
  border: 2px solid rgb(75, 75, 75);
  font-size: 42px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 5px;
}
</style>

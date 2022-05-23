<template>
  <div @click="$emit('click')" class="cell" :class="[playerToken]"></div>
</template>

<script>
export default {
  name: 'GameCell',

  props: {
    value: String,
  },

  computed: {
    playerToken() {
      return {
        'x-token': this.value && this.value === 'X',
        'o-token': this.value && this.value === 'O',
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

.x-token {
  background-image: url('/public/assets/img/X_bright.svg');
  background-position: top; /* Center the image */
  background-repeat: no-repeat; /* Do not repeat the image */
  background-size: cover; /* Resize the background image to cover the entire container */
}

.o-token {
  background-image: url('/public/assets/img/O_bright.svg');
  background-position: top; /* Center the image */
  background-repeat: no-repeat; /* Do not repeat the image */
  background-size: cover; /* Resize the background image to cover the entire container */
}
</style>

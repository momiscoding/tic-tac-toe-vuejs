<!-- Timer based on https://codepen.io/raphael_octau/pen/XxeqRJ -->
<template>
  <div class="play-time">
    <span class="time">{{ time }}</span>
  </div>
</template>

<script>
// TODO: Change this to mixin instead of component
export default {
  data() {
    return {
      time: '00:00:00',
      timeElapsed: '00:00:00',
      timeBegan: null,
      timePartial: null,
      started: null,
      running: false,
    }
  },

  methods: {
    start() {
      if (this.running) return

      if (this.timeBegan === null) {
        this.stop()
        this.timeBegan = new Date()
      }

      this.timePartial = new Date()
      this.started = setInterval(this.clockRunning, 10)
      this.running = true
    },

    stop() {
      this.timeElapsed = this.formatTimer(
        new Date(this.timeElapsed + this.timePartial)
      )

      this.running = false
      clearInterval(this.started)
      this.timeBegan = null
      setTimeout(() => {
        this.time = '00:00:00'
      }, 2000)
    },

    clockRunning() {
      var currentTime = new Date(),
        timeElapsed = new Date(currentTime - this.timeBegan)

      this.timePartial = timeElapsed

      this.time = this.formatTimer(timeElapsed)
    },

    formatTimer(time) {
      let hour = time.getUTCHours(),
        min = time.getUTCMinutes(),
        sec = time.getUTCSeconds()

      time =
        this.zeroPrefix(hour, 2) +
        ':' +
        this.zeroPrefix(min, 2) +
        ':' +
        this.zeroPrefix(sec, 2)

      return time
    },

    zeroPrefix(num, digit) {
      var zero = ''
      for (var i = 0; i < digit; i++) {
        zero += '0'
      }
      return (zero + num).slice(-digit)
    },
  },
}
</script>

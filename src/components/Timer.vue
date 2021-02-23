<template>
  <div class="timer">
    {{ time }}
  </div>
  <div class="buttonContainer">
    <button @click="startTime">Start</button>
    <button @click="stopTime">Stop</button>
    <button @click="reset">Reset</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  data() {
    //seconds are temporary and will be removed
    const time = ref("00:00:00");
    const stoppedDuration = ref(0);
    const running = ref(false);
    const timeBegan = ref(null);
    const timeStopped = ref(null);
    const started = ref(null);

    function startTime() {
      if (running.value) return;
      if (timeBegan.value === null) {
        reset();
        timeBegan.value = new Date();
      }

      if (timeStopped.value !== null) {
        stoppedDuration.value += new Date() - timeStopped.value;
      }

      started.value = setInterval(clockRunning, 10);
      running.value = true;
    }
    function stopTime() {
      running.value = false;
      timeStopped.value = new Date();
      clearInterval(started.value);
    }

    function reset() {
      running.value = false;
      clearInterval(started.value);
      stoppedDuration.value = 0;
      timeBegan.value = null;
      timeStopped.value = null;
      time.value = "00:00:00";
    }

    function clockRunning() {
      let currentTime = new Date(),
        timeElapsed = new Date(
          currentTime - timeBegan.value - stoppedDuration.value
        ),
        hour = timeElapsed.getUTCHours(),
        min = timeElapsed.getUTCMinutes(),
        sec = timeElapsed.getUTCSeconds();

      time.value =
        zeroPrefix(hour, 2) +
        ":" +
        zeroPrefix(min, 2) +
        ":" +
        zeroPrefix(sec, 2);
    }

    function zeroPrefix(num, digit) {
      let zero = "";
      for (let i = 0; i < digit; i++) {
        zero += "0";
      }
      return (zero + num).slice(-digit);
    }

    return {
      time,
      startTime,
      stopTime,
      reset,
      stoppedDuration,
      timeBegan,
      timeStopped,
      started,
    };
  },
  methods:{
  }
};
</script>

<style scoped>
.timer {
  font-size: 2em;
}
button {
  background-color: #4caf50;
  border: none;
  color: white;
  width: 60px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  -webkit-transition-duration: 0.4s; /* Safari */
  transition-duration: 0.4s;
}
button:hover {
  box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.24),
    0 17px 50px 0 rgba(0, 0, 0, 0.19);
}
</style>

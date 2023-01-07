<script setup lang="ts">
import { ref, defineEmits } from "vue";
import Stopwatch from "./Stopwatch.vue";

const timeInSeconds = ref(0);
const timer = ref(0);
const isTiming = ref(false);

const emit = defineEmits(["timerStopped"]);

function start() {
  timer.value = setInterval(() => {
    timeInSeconds.value += 1;
  }, 1000);
  isTiming.value = true;
}

function stop() {
  clearInterval(timer.value);
  isTiming.value = false;
  emit("timerStopped", timeInSeconds);
}
</script>

<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Stopwatch :time-in-seconds="timeInSeconds" />
    <button class="button" :disabled="isTiming" @click="start">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" :disabled="!isTiming" @click="stop">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

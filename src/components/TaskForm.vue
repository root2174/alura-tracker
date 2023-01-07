<script setup lang="ts">
import { computed, ref } from "vue";

const timeInSeconds = ref(0);
const timer = ref(0);

const formattedTime = computed(() =>
  new Date(timeInSeconds.value * 1000).toISOString().substring(11, 19)
);

function start() {
  timer.value = setInterval(() => {
    timeInSeconds.value += 1;
  }, 1000);
}

function stop() {
  clearInterval(timer.value);
}
</script>

<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="form to add a new task.">
        <input
          type="text"
          class="input"
          placeholder="Which task you want to begin?"
        />
      </div>
      <div class="column">
        <div
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
          <section>
            <strong>{{ formattedTime }}</strong>
          </section>
          <button class="button" @click="start">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button class="button" @click="stop">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

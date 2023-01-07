<script setup lang="ts">
import { ref } from "vue";
import ITask from "../interfaces/ITask";
import Timer from "./Timer.vue";

const description = ref("");
const emit = defineEmits(["taskDone"]);

function taskDone(timeInSeconds: number) {
  emit("taskDone", {
    description: description.value,
    timeInSeconds,
  } as ITask);
  description.value = "";
}
</script>

<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="form to add a new task.">
        <input
          v-model="description"
          type="text"
          class="input"
          placeholder="Which task you want to begin?"
        />
      </div>
      <div class="column">
        <Timer @timer-stopped="taskDone" />
      </div>
    </div>
  </div>
</template>

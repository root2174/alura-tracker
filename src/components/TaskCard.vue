<script setup lang="ts">
import Stopwatch from "./Stopwatch.vue";
import ITask from "../interfaces/ITask";
import TaskBox from "./TaskBox.vue";

defineProps<{
  task: ITask;
}>();
</script>

<template>
  <TaskBox>
    <div class="columns">
      <div class="column is-7">
        {{ task.description || "Task without description" }}
      </div>
      <div class="column">
        <Stopwatch :time-in-seconds="task.timeInSeconds" />
      </div>
    </div>
  </TaskBox>
</template>

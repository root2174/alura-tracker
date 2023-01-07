<script setup lang="ts">
import { computed, ref } from "vue";
import SideBar from "./components/SideBar.vue";
import TaskBox from "./components/TaskBox.vue";
import TaskCard from "./components/TaskCard.vue";
import TaskForm from "./components/TaskForm.vue";
import ITask from "./interfaces/ITask";

const tasks = ref<ITask[]>([]);

function saveTask(task: ITask) {
  tasks.value.push(task);
}

const isListEmpty = computed(() => tasks.value.length === 0);
</script>

<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <TaskForm @task-done="saveTask" />
      <div class="list">
        <TaskCard v-for="(task, index) in tasks" :key="index" :task="task" />
        <TaskBox v-if="isListEmpty">
          You're not so productive today :(
        </TaskBox>
      </div>
    </div>
  </main>
</template>

<style scoped>
.lista {
  padding: 1.25rem;
}
</style>

<style scoped></style>

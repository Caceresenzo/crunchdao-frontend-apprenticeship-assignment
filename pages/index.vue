<template>
  <v-main>
    <v-container>
      <v-row>
        <v-col cols="12" sm="6">
          <v-card>
            <v-card-title> Pending </v-card-title>
            <v-card-subtitle>
              <v-text-field
                v-model="text"
                variant="outlined"
                density="compact"
                hide-details
                @keydown.enter="create"
              />
            </v-card-subtitle>
            <task-list :items="pending" @toggle="toggle" />
          </v-card>
        </v-col>
        <v-col cols="12" sm="6">
          <v-card title="Completed">
            <task-list :items="completed" @toggle="toggle" />
          </v-card>
        </v-col>
        <v-col cols="12">
          <v-card title="Chart">
            <task-chart
              :pending="pending.length"
              :completed="completed.length"
            />
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script setup lang="ts">
import { Task } from "@/types/Task";

const text = ref("");

const todos = reactive(Array<Task>());

const pending = computed(() => todos.filter(({ done }) => !done));
const completed = computed(() => todos.filter(({ done }) => done));

const toggle = (taskId: number) => {
  const task = todos.find(({ id }) => id === taskId);

  if (task) {
    task.done = !task.done;
  }
};

const create = () => {
  if (!text.value) {
    return;
  }

  todos.push({
    id: todos.length,
    text: text.value,
    done: false,
  });

  text.value = "";
};
</script>

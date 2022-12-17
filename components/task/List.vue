<template>
  <v-list>
    <v-list-item v-for="task in items" :key="task.id">
      <template #prepend>
        <v-list-item-action start>
          <v-checkbox-btn :model-value="task.done" :true-value="true" @click="toggle(task)" />
        </v-list-item-action>
      </template>
      <v-list-item-title> {{ task.text }} </v-list-item-title>
    </v-list-item>
  </v-list>
</template>

<script setup lang="ts">
import { Task } from "@/types/Task";
import { PropType } from "vue";

const props = defineProps({
  items: {
    type: Array as PropType<Array<Task>>,
    required: true
  },
});

const emit = defineEmits(["toggle"])

const { items } = toRefs(props)

const toggle = (task: Task) => {
    emit("toggle", task.id)
}
</script>
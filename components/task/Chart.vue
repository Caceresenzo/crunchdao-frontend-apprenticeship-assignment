<template>
  <apexchart type="pie" height="300" :options="chartOptions" :series="series" />
</template>

<script setup lang="ts">
const props = defineProps({
    pending: Number,
    completed: Number,
})

const chartOptions = reactive({
  labels: ["Pending", "Completed"],
  theme: {
    mode: "dark",
  },
});

const series = computed(() => [props.pending, props.completed])
</script>

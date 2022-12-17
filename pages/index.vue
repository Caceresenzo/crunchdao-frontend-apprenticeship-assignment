<template>
  <v-main>
    <v-container>
      <v-row>
        <v-col cols="12" sm="6">
          <v-card title="Left Column" :text="lorem" />
        </v-col>
        <v-col cols="12" sm="6">
          <v-card title="Right Column" :text="lorem" />
        </v-col>
        <v-col cols="12">
          <v-card title="Simple Chart">
            <apexchart type="pie" height="300" :options="chartOptions" :series="series" />
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script setup lang="ts">
const lorem = ref(
  "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia ullam ducimus dolores voluptates, itaque assumenda temporibus id rem nulla praesentium commodi harum non tenetur? Exercitationem voluptatum dolorum blanditiis rem ducimus."
);

const chartOptions = reactive({
  labels: ['Team A', 'Team B', 'Team C', 'Team D', 'Team E'],
  theme: {
    mode: "dark"
  }
});

const series = reactive([44, 55, 13, 43, 22]);
</script>

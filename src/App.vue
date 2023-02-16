<script setup>
import { ref, shallowRef, computed, watch, nextTick } from "vue";
import chart from "chart.js/auto";

const weights = ref([]);

const weightChartEl = ref(null);

const wheightChart = shallowRef(null);

const weightInput = ref(60.0)

</script>

<template>
  <h1>Hello World</h1>
</template>

<style scoped>

</style>

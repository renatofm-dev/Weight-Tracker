<script setup>
import { ref, shallowRef, computed, watch, nextTick } from "vue";
import chart from "chart.js/auto";

const weights = ref([]);

const weightChartEl = ref(null);

const wheightChart = shallowRef(null);

const weightInput = ref(60.0);

const currentWeight = computed(() => {
  return weights.value.sort((a,b)=> b.date - a.date)[0] || { weight: 0 }
});

const addWeight = () => {
  weights.value.push({
    weight: weightInput.value,
    date: new Date().getTime()
  })
}

</script>

<template>
  <h1>Hello World</h1>
</template>

<style scoped>

</style>

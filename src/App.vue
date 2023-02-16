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
  <main>
    <h1>Weight Tracker</h1>

    <div class="current">
      <span>{{ currentWeight.weight }}</span>
      <small>Current Weight (Kg)</small>

      <form @submit.prevent="addWeight">

        <input type="number" step="0.1" v-model="weightInput"/>

        <input type="submit" value="Add Weight"/>

      </form>
    </div>

    <div v-if="weights && weights.length > 0">

      <h2>Last 7 Days</h2>

      <div class="canvas-box">
        <canvas ref="weightChartEl"></canvas>
      </div>

      <div class="weight-history">
        <h2>Weight History</h2>
        <ul>
          <li v-for="weight in weights">
            <span>{{ weight.weight }}Kg</span>
            <small>{{ new Date(weight.date).toLocaleDateString() }}</small>
          </li>
        </ul>
      </div>

    </div>
  </main>
</template>

<style scoped>

</style>

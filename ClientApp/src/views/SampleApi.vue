<template>
  <div class="sample-api">
    <h1>Sample page fetching data from the SampleDataController</h1>
    <h3>These are the initial values:</h3>
    <ul class="values-list">
      <li v-for="value in values" :key="value.dateFormatted">
        {{ value.dateFormatted }} - {{ value.temperatureC }} - {{ value.summary }}
      </li>
    </ul>
    <button @click="onTryPost">Try POST action</button>
  </div>
</template>

<script setup lang="ts">

import { ref } from 'vue';

    const values = ref([]);
    const reload = async () => {
        const res = await fetch('/weatherforecast');
        const data = await res.json();
        values.value = data;
    };

    reload();

</script>

<style scoped>
.values-list {
  list-style: none;
}
</style>
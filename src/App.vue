<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <div class="bg-white p-8 flex flex-col space-y-4 rounded-xl shadow-md w-96">
      <input
          v-model="zipCode"
          @input="fetchCity"
          placeholder="Zip Code"
          class="w-full p-2 border rounded-md focus:outline-none focus:ring focus:ring-blue-200 transition"
      />
      <input
          v-model="city"
          placeholder="City"
          class="w-full p-2 border rounded-md focus:outline-none focus:ring focus:ring-blue-200 transition"
          readonly
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import axios from 'axios';
import { useDebounceFn } from '@vueuse/core';

const zipCode = ref('');
const city = ref('');

const fetchCity = useDebounceFn(async () => {
  if (zipCode.value) {
    try {
      const response = await axios.get(`https://hur.webmania.cc/zips/${zipCode.value}.json`);
      const zips = response.data?.zips;
      if (zips && zips.length > 0) {
        city.value = zips[0].name;
      } else {
        city.value = '';
      }
    } catch (error) {
      console.error('Error fetching city data:', error);
      city.value = '';
    }
  } else {
    city.value = '';
  }
}, 500);

</script>



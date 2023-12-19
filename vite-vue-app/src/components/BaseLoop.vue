<script setup>
import { ref, computed } from 'vue';

const inputTime = ref(''); // User input for time

const generateGreeting = () => {
  const timeRegex = /^(\d{1,2}):(\d{2})$/;
  const match = inputTime.value.match(timeRegex);

  if (match) {
    const hour = parseInt(match[1]);

    if (hour >= 0 && hour < 12) {
      return 'Good Morning';
    } else if (hour >= 12 && hour < 17) {
      return 'Good Afternoon';
    } else {
      return 'Good Evening';
    }
  } else {
    return 'Invalid format (HH:MM)';
  }
};

const greeting = computed(generateGreeting);
</script>


<template>
  <div id="app">
    <label for="userTime">Enter the time (HH:MM):</label>
    <input type="text" id="userTime" v-model="inputTime" />

    <div>
      <p v-if="greeting === 'Good Morning'">{{ greeting }}</p>
      <p v-else-if="greeting === 'Good Afternoon'">{{ greeting }}</p>
      <p v-else-if="greeting === 'Good Evening'">{{ greeting }}</p>
      <p v-else>{{ greeting }}</p>
    </div>
  </div>
</template>
<script setup>
// TODO: TDD Exercise: complete the implementation of this component
// to pass all the tests defined in its companion .test.js file

import { ref, onMounted } from 'vue';
const response = ref({});
const loaded = ref(false);
const error = ref(false);
onMounted(async () => {
  try {
    const res = await fetch('https://yesno.wtf/api');

    response.value = await res.json();
    loaded.value = true;
  } catch (error) {
    expect(error).toBe('error');
  }
});
</script>

<template>
  <img :src="response.image" v-if="loaded" />

  <v-else>loading...</v-else>
</template>

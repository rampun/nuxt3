<template>
  <div class="grid grid-cols-4 gap-4">
    <nuxt-link
      v-for="iphone in iphones"
      :key="iphone"
      :to="`/iphone/${iphone}`"
      class="shadow-lg border rounded-lg text-center"
    >
      <h2>{{ iphone }}</h2>
      <div class="flex justify-center">
        <img :src="`/images/${iphone}.jpeg`" width="200" alt="" />
      </div>
    </nuxt-link>
  </div>
</template>

<script setup>
useHead({
  title: "Nuxt3 - iPhones",
});

const { data } = useFetch("/api/iphones");
const iphones = data;
</script>

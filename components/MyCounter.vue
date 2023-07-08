<template>
  <button @click="increment">Incrementor</button>
  <p>{{ count }}</p>
  <button @click="decrement">Decrementor</button>
</template>

<script setup>
const count = ref(0);

function increment() {
  count.value++;
}

function decrement() {
  count.value--;
}
</script>

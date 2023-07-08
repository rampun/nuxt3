<template>
  <nav
    class="bg-blue-400 shadow-lg p-3 text-white text-lg flex justify-between gap-3"
  >
    <div class="flex gap-2">
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/iphone">iPhones</NuxtLink>
      <p>Cart ({{ cart.length }})</p>
      <p>Routes visitd: {{ pageVisitCount }}</p>
    </div>
    <div v-if="auth.isAuthenticated">
      <NuxtLink to="/profile">Profile</NuxtLink>
      <button class="ml-3" @click="logout">Logout</button>
    </div>
    <div v-else>
      <NuxtLink to="/login">Login</NuxtLink>
    </div>
  </nav>
</template>

<script setup>
const cart = useCart();
const auth = useAuth();
const pageVisitCount = usePageVisitCount();

const logout = () => {
  auth.value.isAuthenticated = false;
};
</script>

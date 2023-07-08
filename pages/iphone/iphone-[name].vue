<template>
  <div>
    <Head>
      <Title> Nuxt3 - {{ fullname }} </Title>
    </Head>
    <div class="flex gap-8 flex-column items-center">
      <div><img :src="`/images/${fullname}.jpeg`" width="540" /></div>
      <div>
        <p>{{ fullname }}</p>
        <button
          class="bg-blue-700 border rounded text-white py-2 px-3"
          @click="addToCart"
        >
          <span v-if="isInCart()">Remove from cart</span>
          <span v-else>Add to cart</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
const route = useRoute();

const fullname = computed(() => {
  return `iphone-${route.params.name}`;
});

const cart = useCart();

const isInCart = () => {
  return !!cart.value.find((ct) => ct.name === fullname.value);
};

const addToCart = () => {
  const found = cart.value.find((ct) => ct.name === fullname.value);
  if (!found) {
    cart.value.push({
      name: fullname,
    });
  } else {
    cart.value = cart.value.filter((ct) => ct.name !== fullname.value);
  }
};
// useHead({
//   title: `Nuxt3 - iPhone  ${name.value}`,
// });
</script>

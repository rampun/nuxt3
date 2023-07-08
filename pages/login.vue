<template>
  <div>
    <form @submit.prevent="onSubmit">
      <input v-model="body.email" type="text" name="email" class="border" />
      <input
        v-model="body.password"
        type="password"
        name="password"
        class="border"
      />
      <button class="bg-blue-700 border text-white px-3 py-2">
        <span v-if="isLoading">Loading ...</span>
        <span v-else>Sign In</span>
      </button>
    </form>
    <div v-if="_error">
      <p class="bg-red-600 text-white p-5 text-sm">{{ _error }}</p>
    </div>
  </div>
</template>

<script setup>
const url = "https://reqres.in/api/login";
const isLoading = ref(false);
const _error = ref(null);

const body = reactive({
  email: "eve.holt@reqres.in",
  password: "cityslicka",
});

const onSubmit = async () => {
  if (isLoading.value) return;
  isLoading.value = true;
  const { data, error } = await useFetch(url, {
    method: "POST",
    body,
  });

  isLoading.value = false;
  if (error.value) {
    _error.value = error.value.data.error;
    return;
  }

  const auth = useAuth();
  auth.value.isAuthenticated = true;
  navigateTo("/");
};
</script>

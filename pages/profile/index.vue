<template>
  <div>
    <h2>Profile</h2>
    <p>This is a profile view</p>
  </div>
</template>

<!-- <script>
definePageMeta({
  layout: "sidebar",
});
</script> -->
<script>
definePageMeta({
  middleware: ["auth"],
});
</script>

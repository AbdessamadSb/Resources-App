<template>
  <TheHeader title="RememberMe" />
  <div class="container mx-auto">
    <TheResources />
  </div>
</template>
<script>
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "./components/learning-resources/TheResources.vue";
export default {
  components: {
    TheHeader,
    TheResources,
  },
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>

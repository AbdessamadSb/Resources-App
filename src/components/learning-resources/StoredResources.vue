<template>
  <ul class="list-none">
    <ResourcesItem
      v-for="res in resources"
      :key="res.id"
      :id="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    />
  </ul>
</template>
<script>
import ResourcesItem from "./ResourcesItem.vue";
export default {
  components: {
    ResourcesItem,
  },
  inject: ["resources"],
};
</script>

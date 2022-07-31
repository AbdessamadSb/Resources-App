<template>
  <div>
    <ul>
      <ResourcesItem />
    </ul>
  </div>
</template>
<script>
import ResourcesItem from "./components/learning-resources/ResourcesItem.vue";
export default {
  components: {
    ResourcesItem,
  },
  data() {
    return {
      storedResources: [
        {
          id: "official-guide",
          title: "Official Guide",
          description: "The Official Vue js documentation.",
          link: "https://vuejs.org/",
        },
        {
          id: "google",
          title: "Google",
          description: "Learn how to google stuff",
          link: "https://google.com/",
        },
      ],
    };
  },
  components: { ResourcesItem },
};
</script>

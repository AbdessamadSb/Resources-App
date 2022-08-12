<template>
  <base-card>
    <base-button @click="switchTab('stored-resources')" :mode="storedButton"
      >Stored Resources</base-button
    >
    <base-button @click="switchTab('add-resource')" :mode="addResButton"
      >Add Resources</base-button
    >
  </base-card>
  <keep-alive>
    <component @delete="deleteRes" :is="selectedTab"></component>
  </keep-alive>
</template>
<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";
import { v4 as uuidv4 } from "uuid";
export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: "stored-resources",
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

  computed: {
    storedButton() {
      return this.selectedTab === "stored-resources" ? null : "flat";
    },
    addResButton() {
      return this.selectedTab === "add-resource" ? null : "flat";
    },
  },
  provide() {
    return {
      resources: this.storedResources,
      addRes: this.addResource,
      deleteRes: this.deleteRes,
    };
  },
  methods: {
    deleteRes(id) {
      const resIndex = this.storedResources.findIndex((item) => item.id == id);
      this.storedResources.splice(resIndex, 1);
    },
    addResource(title, desc, link) {
      const newResource = {
        id: uuidv4(),
        title: title,
        description: desc,
        link: link,
      };
      this.storedResources.push(newResource);
      this.selectedTab = "stored-resources";
    },
    switchTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>

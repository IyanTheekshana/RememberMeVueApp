<template>
  <base-card>
    <base-button
      v-on:click="setSelectedTab('stored-resources')"
      :mode="storeResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      v-on:click="setSelectedTab('add-resource')"
      :mode="addReButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <Keep-alive>
    <component v-bind:is="selectedTab"></component>
  </Keep-alive>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";

export default {
  components: {
    "stored-resources": StoredResources,
    "add-resource": AddResource,
  },
  data() {
    return {
      selectedTab: "stored-resources",
      storedResources: [
        {
          id: "Official-guide",
          title: "Official Guide",
          description: "The official vue.js documentation",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          description: "Learn to google",
          link: "https://google.com",
        },
      ],
    };
  },

  methods: {
    setSelectedTab(tab) {
      return (this.selectedTab = tab);
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = "stored-resources";
    },
    removeResource(resId) {
      // this.storedResources = this.storedResources.filter(
      //   (res) => res.id !== resId
      // );
      const resIndex = this.storedResources.findIndex(
        (res) => res.id === resId
      );
      this.storedResources.splice(resIndex, 1);
    },
  },
  computed: {
    storeResButtonMode() {
      return this.selectedTab === "stored-resources" ? "flat" : null;
    },
    addReButtonMode() {
      return this.selectedTab === "add-resource" ? "flat" : null;
    },
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.removeResource,
    };
  },
};
</script>

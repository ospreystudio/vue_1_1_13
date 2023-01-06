<template>
<base-card>
  <base-button @click="setSelectedTab('stored-resource')" :mode="storedResButtonMode">Stored Resources</base-button>
  <base-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode">Add Resource</base-button>
</base-card>
  <keep-alive>
  <component :is="selectedTab"></component>
  </keep-alive>

</template>

<script>

import StoredResource from "./StoredResource";
import AddResource from "./AddResource";
export default {
  components: {
    StoredResource,
    AddResource
  },
  name: "TheResource",
  data() {
    return {
      selectedTab: 'stored-resource',
      storedResources: [
        {
          id: 'official-gide',
          title: 'Official Gide',
          description: 'The official Vue.js Documentation',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.org'
        }
      ],
    }
  },
  provide() {
    return {
      resources: this.storedResources,
      addNote: this.addNote,
      removeNote: this.removeNote
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab
    },
    addNote(title, description, link) {
      const newNote = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: link
      };
      this.storedResources.unshift(newNote);
      this.selectedTab = 'stored-resource'
    },
    removeNote(resId) {
      const resIndex = this.storedResources.findIndex(res => res.id === resId);
      this.storedResources.splice(resIndex, 1)
    }
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resource' ? null : 'flat'
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat'
    },

  }
}
</script>

<style scoped>

</style>
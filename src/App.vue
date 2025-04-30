<template>
  <Header title="Learning Resources App"></Header>
  <StoredResources :resources="storedResources"></StoredResources>
</template>

<script>
import StoredResources from './components/learning-resources/StoredResources.vue';
import Header from './components/layouts/Header.vue';

export default {
  components: {
    StoredResources,
    Header,
  },
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vuejs documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google as a programmer',
          link: 'https://google.com',
        },
      ],
    };
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>

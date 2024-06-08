<template>
    <h1>Oluwole-young's Repositories</h1>

    <ul>
        <RouterLink to="/" v-for="repo in repos">
            <h3>
                {{ repo.name }}
            </h3>
            <p>{{ repo.description? repo.description : "no descrption" }}</p>
        </RouterLink>
    </ul>
</template>

<script>
    import { RouterLink } from 'vue-router';
    import axios from 'axios'

    export default {
  data() {
    return {
      repos: []
    };
  },
  async created() {
    try {
      const response = await axios.get('https://api.github.com/users/youngie8/repos');
      this.repos = response.data;
    } catch (error) {
      console.error(error);
    }
  }
};
</script>
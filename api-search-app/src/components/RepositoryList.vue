<template>
  <!-- Conditional rendering based on the length of 'repos' array -->
  <div v-if="repos.length">
    <h3>Repositories</h3>
    <ul>
      <!-- Loop through each 'repo' in 'repos' array -->
      <li v-for="repo in repos" :key="repo.id">
        <!-- Link to the repository with its name -->
        <a :href="repo.html_url" target="_blank">{{ repo.name }}</a>
        <!-- Description of the repository -->
        <p>{{ repo.description }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    repos: Array, // Prop 'repos' expects an array of repository objects
  },
};
</script>

<style scoped>
/* Styling limited to this component only */

ul {
  list-style: none; /* Removes default list styles */
  padding: 0; /* Removes padding from the <ul> */
}

li {
  margin: 10px 0; /* Adds margin above and below each <li> */
}

a {
  font-weight: bold; /* Sets font weight to bold for links */
  color: #42b983; /* Sets link color to a shade of green */
}

p {
  margin: 5px 0; /* Adds margin above and below each <p> */
}
</style>

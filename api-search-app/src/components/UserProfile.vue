<template>
  <!-- Conditional rendering based on presence of 'userData' -->
  <div v-if="userData">
    <!-- User avatar displayed with dynamic source binding -->
    <img :src="userData.avatar_url" alt="User Avatar" width="150" />
    <!-- User's name -->
    <h2>{{ userData.name }}</h2>
    <!-- User's bio -->
    <p>{{ userData.bio }}</p>
    <!-- Link to user's GitHub profile -->
    <p><a :href="userData.html_url" target="_blank">GitHub Profile</a></p>
  </div>
</template>

<script>
export default {
  props: {
    userData: Object, // Prop 'userData' expects an object containing user data
  },
};
</script>

<style scoped>
/* Styles limited to this component only */

div {
  text-align: center; /* Centers content horizontally within the <div> */
  margin: 20px; /* Adds margin around the <div> */
}

img {
  border-radius: 50%; /* Rounds the corners of the user avatar */
}

h2 {
  margin: 10px 0; /* Adds margin above and below the <h2> */
}

p {
  margin: 5px 0; /* Adds margin above and below each <p> */
}
</style>

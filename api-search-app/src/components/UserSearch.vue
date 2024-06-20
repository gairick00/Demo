<template>
  <!-- Input field and button for searching GitHub user -->
  <div>
    <!-- Input field for entering GitHub username -->
    <input v-model="username" placeholder="Enter GitHub username" @keyup.enter="searchUser" />
    <!-- Button to trigger the search -->
    <button @click="searchUser">Search</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '', // Initializes 'username' data property for storing user input
    };
  },
  methods: {
    // Method triggered when user presses 'Enter' in input field or clicks 'Search' button
    searchUser() {
      this.$emit('search', this.username); // Emits 'search' event with current 'username' value
    },
  },
};
</script>

<style scoped>
/* Styles limited to this component only */

div {
  margin: 20px; /* Adds margin around the entire component */
}

input {
  padding: 10px; /* Adds padding inside the input field */
  font-size: 16px; /* Sets font size of the text inside the input */
}

button {
  padding: 10px; /* Adds padding inside the button */
  font-size: 16px; /* Sets font size of the button text */
  margin-left: 10px; /* Adds left margin between input field and button */
}
</style>

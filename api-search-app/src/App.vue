<template>
  <div id="app">
    <!-- Header section with title -->
    <header>
      <h1>Searching for Github Repo Via Name</h1>
    </header>
    <!-- Main content section -->
    <main>
      <!-- UserSearch component for searching GitHub users 
      UserProfile component to display user profile
      Repo List component to display user's repositories 
      -->
      <UserSearch @search="fetchUserData" />
      <UserProfile :userData="userData" />
      <RepositoryList :repos="repos" />
    </main>
  </div>
</template>

<script>
// Import statements
import UserSearch from './components/UserSearch.vue';
import UserProfile from './components/UserProfile.vue';
import RepositoryList from './components/RepositoryList.vue';
import axios from 'axios';

//component
export default {
  name: 'App',
  components: {
    UserSearch,
    UserProfile,
    RepositoryList,
  },
  data() {
    return {
      userData: null,
      repos: [],
    };
  },
  methods: {
    async fetchUserData(username) {
      try {
        // fetch , fetch , update , catch error 
        const userResponse = await axios.get(`https://api.github.com/users/${username}`);
        const repoResponse = await axios.get(`https://api.github.com/users/${username}/repos`);
        this.userData = userResponse.data;
        this.repos = repoResponse.data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    },
  },
};
</script>

<style>

header {
  text-align: center;
  margin: 20px;
}

main {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

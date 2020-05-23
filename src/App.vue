<template>
  <div id="app">
    <img alt="Vue logo" class="logo" src="./assets/github.png" />
    <Navbar />
    <div class="container">
      <div class="card card-body">
        <h1>Search GitHub User</h1>
        <p class="lead">You can search for users on GitHub type a name</p>
        <input
          @keyup="allUsers"
          type="text"
          id="searchBar"
          class="form-control"
          placeholder="type user name.."
        />
      </div>

      <div class="row mt-2" v-if="user.length !== 0">
        <div class="col-md-4">
          <UsersProfile :user="user" />
        </div>
        <div class="col-md-8">
          <Repository v-for="repo in repos" :key="repo" :repo="repo" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import axios from "axios";
import UsersProfile from "./components/UsersProfile.vue";
import Repository from "./components/Repository.vue";
export default {
  name: "App",
  data() {
    return {
      allData: {
        url: "https://api.github.com/users",
        clientID: "Iv1.4b2cac779d0b299b",
        clientSecret: "69817c4de293fb2d7e5a46d7b6a4f2ac9119ac58",
        count: 6,
        sort: "created: asc"
      },
      user: [],
      repos: []
    };
  },

  components: {
    Navbar,
    UsersProfile,
    Repository
  },

  methods: {
    allUsers(event) {
      const user = event.target.value;
      const { url, clientID, clientSecret, count, sort } = this.allData;
      axios
        .get(
          `${url}/${user}?client_id=${clientID}&client_secret=${clientSecret}`
        )
        .then(({ data }) => (this.user = data));

      axios
        .get(
          `${url}/${user}/repos?per_page=${count}&sort=${sort}&client_id=${clientID}&client_secret=${clientSecret}`
        )
        .then(({ data }) => (this.repos = data));
    }
  }
};
</script>

<style scoped>
.logo {
  width: 90px;
  padding: 20px;
}
</style>



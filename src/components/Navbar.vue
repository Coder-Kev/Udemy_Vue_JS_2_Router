<template>
  <nav class="main-nav">
    <ul>
      <li><router-link to="/">Home</router-link></li>
      <li><router-link :to="{ name: 'About' }">About</router-link></li>
    </ul>
    <h2>User Profiles</h2>
    <ul>
      <li v-for="(id, index) in userIds" :key="index">
        <router-link :to="{ name: 'ViewProfile', params: { user_id: id } }">
          <span>Profile {{ id }}</span>
        </router-link>
      </li>
    </ul>
    <h2>Navigation Controls</h2>
    <ul>
      <li><button @click="goBack">Go Back</button></li>
      <li><button @click="goHome">Redirect To Home</button></li>
      <li><button @click="goForward">Go Forward</button></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      userIds: ["1", "2", "3", "4"]
    };
  },
  methods: {
    goHome() {
      // $router keeps track of our Navigation History
      // same as response.redirect
      this.$router.push({ name: "Home" });
    },
    goBack() {
      // On codesandbox.io goBack changes URL but does not render
      // After adding mode: "history" in router/index.js it worked
      this.$router.go(-1);
    },
    goForward() {
      // On codesandbox.io goForward changes URL but does not render
      // After adding mode: "history" in router/index.js it worked
      this.$router.go(1);
    }
  }
};
</script>

// NOTE that router-link become anchor tags
<style>
ul {
  list-style-type: none;
  padding: 0;
}
a {
  color: #42b983;
}
li {
  display: inline-block;
  margin: 10px;
}
</style>

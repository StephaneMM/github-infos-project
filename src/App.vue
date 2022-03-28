<template>
  <div id="app">
    <UserInput @fetchedInofos="setCurrentUserInfo" />
    <UserInfos :userInfos="currentUserInfos"/>
  </div>
</template>

<script>
import UserInput from "./components/UserInput.vue";
import axios from "axios";

export default {
  name: "App",
  data: () => ({
    currentUserInfos: {},
    currentUserRepo:{}
  }),
  methods: {
    setCurrentUserInfo(fetchedInfos) {
      console.log(fetchedInfos);
      this.currentUserInfos = fetchedInfos;
    },

    async fetchUserRepo() {
      console.log("fetchedInfos");
      try {
        const user = await axios.get(
          `https://api.github.com/users/${this.currentUserInfos.repos_url}`
        );
        this.fetchedInfos = user.data;
        this.$emit('fetchedInfos',this.fetchedInfos);
      } catch (error) {
        console.log(error);
      }
    },
  },
  components: {
    UserInput,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

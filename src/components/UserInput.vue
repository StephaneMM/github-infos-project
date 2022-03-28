<template>
  <div class="container">
    <input v-model="username" type="text" />
    <button @click="fetchUser">Search User</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "UserInput",
  data: () => ({
    username: "",
  }),
  methods: {
    async fetchUser() {
      console.log("fetchedInfos");

      // async call
      try {
        const user = await axios.get(
          `https://api.github.com/users/${this.username}`
        );
        this.fetchedInfos = user.data;
        this.$emit('fetchedInfos',this.fetchedInfos);
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>

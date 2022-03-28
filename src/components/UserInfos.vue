<template>
  <div class="container">
    <ul>
      <li></li>
      <li></li>
      <li></li>
      <!-- <li
          v-for="repo in userInfos"
          :key=".id"
          :contact="contact"
        />
      </li> -->
    </ul>
  </div>
</template>

<script>
export default {
  nmae: "UserInfos",
  data: () => ({}),

  props: {
    userInfos: {
      type: Object,
    },
  },
  methods: {
     example() {},
  },
};
</script>

<style></style>

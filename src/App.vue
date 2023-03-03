<template>
  <the-header :title="title"></the-header>
  <the-resourses></the-resourses>
</template>

<script>
import TheHeader from "./components/layout/TheHeader.vue";
import TheResources from "./components/learning-resources/TheResources.vue";

export default {
  components: {
    "the-header": TheHeader,
    "the-resourses": TheResources,
  },
  data() {
    return {
      title: "REMEMBER ME",
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
  background: linear-gradient(to right, #131532, #192155);
}
</style>

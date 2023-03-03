<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ["title"],
};
</script>

<style scoped>
header {
  width: 100%;
  height: 10rem;
  background-color: transparent;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

header h1 {
  color: white;
}
</style>

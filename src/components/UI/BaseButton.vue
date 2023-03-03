<template>
  <button :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ["mode"],
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  /* background-color: #3a0061; */
  background-image: linear-gradient(to right, #131532, #192155);
  border: 1px solid #3a0061;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}

button:hover,
button:active {
  background: #270041;
  border-color: #270041;
}

button:not(:first-child) {
  margin-left: 5px;
}

.flat {
  background: transparent;
  color: #3a0061;
  border: none;
}

.flat:hover,
.flat:active {
  background: #edd2ff;
}
</style>

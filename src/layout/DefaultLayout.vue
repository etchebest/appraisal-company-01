<template>
  <div class="default-layout">
    <slot />
  </div>
</template>

<script>
export default {
  name: "DefaultLayout",
};
</script>

<style lang="scss" scoped>
.default-layout {
  font-family: "Trebuchet MS", sans-serif;
  background-color: #cccfe0;
}
</style>

<template>
  <div class="default-layout">
    <slot />
  </div>
</template>

<script>

export default {
  name: 'DefaultLayout',
};
</script>

<style lang="scss" scoped>
.default-layout{
  font-family: 'Trebuchet MS', sans-serif;
  background-color: #CCCFE0;
}
</style>

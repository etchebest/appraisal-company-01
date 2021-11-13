<template>
  <button class="button-custom">{{ text }}</button>
</template>

<script>
import Vuetypes from 'vue-types';

export default {
  name: 'logo',
  props: {
    textBtn: Vuetypes.string,
  },
};
</script>

<style lang="scss" scoped>
.button-custom {
}
</style>

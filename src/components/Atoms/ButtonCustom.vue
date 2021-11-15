<template>
  <v-btn color="#4A1E96" light >
    <span class="button-custom">{{ textBtn }}</span>
  </v-btn>
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
  color: #fff;
  text-transform: capitalize;
  font-weight: 600;
}
</style>

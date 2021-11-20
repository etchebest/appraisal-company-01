<template>
  <v-btn color="#6B2BD9" light :block="block" @click.prevent="click()">
    <span class="button-custom">{{ textBtn }}</span>
  </v-btn>
</template>

<script>
import Vuetypes from "vue-types";

export default {
  name: "logo",
  props: {
    textBtn: Vuetypes.string,
    block: Vuetypes.bool.def(false),
  },
  methods: {
    click() {
      this.$emit("click");
    },
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

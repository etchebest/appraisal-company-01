<template>
  <div class="text-center">
    <v-menu offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn class="btn-custom" color="transparent" v-bind="attrs" v-on="on">
          {{ dataItems.text }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list>
        <v-list-item v-for="(item, index) in dataItems" :key="index">
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import VueTypes from "vue-types";

export default {
  name: "OptionsDropdown",
  props: {
    dataItems: VueTypes.object,
  },
};
</script>

<style lang="scss" scoped>
.btn-custom {
  text-transform: none;
}
</style>

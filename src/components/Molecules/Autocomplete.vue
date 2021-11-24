<template>
  <v-autocomplete
    :items="dataFilter.title"
    @change="getSelect()"
    v-model="selected"
    auto-select-first
    clearable
    dense
    solo
    :label="dataFilter.label"
    :prepend-inner-icon="dataFilter.ico"
  />
</template>

<script>
import VueTypes from "vue-types";

export default {
  name: "AutocompleteCustom",

  data() {
    return {
      selected: "",
    };
  },
  methods: {
    getSelect() {
      this.$emit("responseSelected", this.selected);
    },
  },
  props: {
    dataFilter: VueTypes.object,
  },
};
</script>

<template>
  <v-text-field
    v-model="text"
    clearable
    dense
    solo
    :label="dataText.label"
    :prepend-inner-icon="dataText.icon"
  />
</template>

<script>
import VueTypes from "vue-types";

export default {
  name: "TextField",
  data() {
    return {
      text: "",
    };
  },
  props: {
    dataText: VueTypes.object,
  },
  watch: {
    text() {
      this.$emit("responseText", this.text);
    },
  },
};
</script>

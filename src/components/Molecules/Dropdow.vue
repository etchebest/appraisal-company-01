<template>
  <div class="text-center">
    <v-menu offset-y dark open-on-hover rounded="2">
      <template v-slot:activator="{ on, attrs }">
        <nav class="menu-item" v-bind="attrs" v-on="on">
          {{ data.menu }}
          <v-icon>{{ data.icon }}</v-icon>
        </nav>
      </template>
      <div class="submenu-item" v-for="(sub, index) in data.submenu" :key="index">
        <a :href="sub.link">{{ sub.item }}</a>
      </div>
    </v-menu>
  </div>
</template>

<script>
import VueTypes from 'vue-types';

export default {
  name: 'Dropdown',
  props: {
    data: VueTypes.object,
  },
};
</script>

<style lang="scss" scoped>
.menu-item,
.submenu-item {
  font-size: 0.9em;
  color: #848794;
  padding: 2px 10px;
  margin: 0 2px;
}
div.submenu-item {
  margin: 0;
  padding: 10px 5px;
  background-color: #fff;
  a {
    text-decoration: none;
    color: #848794;
  }

  &:hover {
    background-color: #ebe5fb;
    color: #8a67ec;
  }
}
</style>

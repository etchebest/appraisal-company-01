<template>
  <nav>
    <Dropdow :data="service" v-for="service in services" :key="service.menu" />
  </nav>
</template>

<script>
import Dropdow from './Dropdow.vue';

export default {
  name: 'Navbar',
  components: {
    Dropdow,
  },
  data() {
    return {
      services: [
        {
          menu: 'Jobs',
          linkmenu: '#',
          icon: 'mdi-chevron-down',
          submenu: [
            { item: 'Sub menu 1', link: '#' },
            { item: 'Sub Menu 2', link: '#' },
            { item: 'Sub Menu 3', link: '#' },
          ],
        },
        {
          menu: 'Companies',
          linkmenu: '#',
          icon: 'mdi-chevron-down',
          submenu: [
            { item: 'Sub menu 1', link: '#' },
            { item: 'Sub Menu 2', link: '#' },
            { item: 'Sub Menu 3', link: '#' },
          ],
        },
        {
          menu: 'Pricing',
          linkmenu: '#',
        },
        {
          menu: 'Advice',
          linkmenu: '#',
        },
        {
          menu: 'Updates',
          linkmenu: '#',
        },
        {
          menu: 'Community',
          linkmenu: '#',
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
nav {
  display: flex;
  align-items: center;
  width: fit-content;
}
</style>

<template>
  <div class="header-site">
    <Logo />
    <div>
      <Navbar />
      <Avatar />
    </div>
  </div>
</template>

<script>
import Logo from "@/components/Atoms/Logo.vue";
import Navbar from "@/components/Molecules/Navbar.vue";
import Avatar from "@/components/Molecules/Avatar.vue";

export default {
  name: "Header",
  components: {
    Logo,
    Navbar,
    Avatar,
  },
};
</script>

<style lang="scss" scoped>
.header-site {
  padding: 20px 0;
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  justify-content: space-between;
  div {
    display: flex;
    div:last-child {
      margin-left: 15px;
    }
  }
}
</style>

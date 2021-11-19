<template>
  <v-avatar color="grey lighten-2" size="42">
    <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
  </v-avatar>
</template>

<script>
export default {
  name: "Avatar",
  data() {
    return {
      user: {
        initials: "JD",
        fullName: "John Doe",
        email: "john.doe@doe.com",
      },
    };
  },
};
</script>

<style></style>

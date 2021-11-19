<template>
  <DefaultLayout>
    <div class="home-site">
      <Header />
      <SearchCustom />
      <ContentResults />
    </div>
  </DefaultLayout>
</template>

<script>
import DefaultLayout from "@/layout/DefaultLayout.vue";
import Header from "@/components/Organisms/Header.vue";
import SearchCustom from "@/components/Organisms/SearchCustom.vue";
import ContentResults from "@/components/Organisms/ContentResults.vue";

export default {
  name: "Home",
  components: {
    DefaultLayout,
    Header,
    SearchCustom,
    ContentResults,
  },
};
</script>
<style lang="scss" scoped>
.home-site {
  border-top: 20px solid #e7e7ef;
  background-color: #f2f3f7;
  padding-top: 15px;
  padding: 0 80px;
}
</style>
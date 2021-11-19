<template>
  <div class="search-list">
    <v-row>
      <v-col cols="12" sm="12" class="filters-top">
        <v-autocomplete
          chips
          deletable-chips
          multiple
          class="mr-5"
        ></v-autocomplete>
        <v-autocomplete
          chips
          deletable-chips
          multiple
          class="mr-5"
        ></v-autocomplete>
        <span class="mr-5">Clear</span>
        <ButtonCustom :textBtn="'Search'" />
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="12" class="filters-bottom">
        <div class="menu-datalhe">
          <OptionsDropdown
            v-for="item in items"
            :dataItems="item"
            :key="item.text"
          />
        </div>
        <span>Clear all</span>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ButtonCustom from "@/components/Atoms/ButtonCustom.vue";
import OptionsDropdown from "./OptionsDropdown.vue";

export default {
  name: "SearchList",
  components: {
    ButtonCustom,
    OptionsDropdown,
  },
  data() {
    return {
      items: [
        { text: "Company" },
        { text: "Salary" },
        { text: "Type of work" },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.search-list {
  .filters-top {
    display: flex;
    flex-flow: row;
    justify-content: space-between;
    align-items: center;
  }
  .filters-bottom {
    display: flex;
    flex-flow: row;
    justify-content: space-between;
    align-items: center;
    .menu-datalhe {
      display: flex;
      flex-flow: row nowrap;
      justify-content: flex-start;
      div {
        margin-right: 10px;
      }
    }
  }
}
</style>

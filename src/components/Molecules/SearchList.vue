<template>
  <div class="search-list">
    <v-row>
      <v-col cols="12" sm="5">
        <v-autocomplete
          :items="jobsList"
          v-model="filterSelect.jobTitleText"
          auto-select-first
          clearable
          dense
          solo
          label="Job title or keyword"
          prepend-inner-icon="mdi-magnify"
        />
      </v-col>
      <v-col cols="12" sm="5">
        <v-autocomplete
          :items="coutryList"
          v-model="filterSelect.locationName"
          auto-select-first
          clearable
          dense
          solo
          label="Country or timezone"
          prepend-inner-icon="mdi-magnify"
        />
      </v-col>
      <v-col cols="12" sm="2" class="btn-action">
        <ButtonCustom :textBtn="'Search'" @click="getFilters(filterSelect)" />
      </v-col>
    </v-row>
    <v-row>
      <v-col
        cols="12"
        sm="4"
        class="filters-bottom"
        v-for="item in items"
        :key="item.text"
      >
        <div class="menu-datalhe">
          <Autocomplete :dataFilter="item" @selected="item.value = $event" />
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import VueTypes from "vue-types";
import ButtonCustom from "@/components/Atoms/ButtonCustom.vue";
import Autocomplete from "./Autocomplete.vue";

export default {
  name: "SearchList",
  components: {
    ButtonCustom,
    Autocomplete,
  },
  data() {
    return {
      jobsList: [],
      coutryList: [],
      companyName: [],
      annualWage: [],
      typeWork: [],
      dataFilter: null,
      dataSubfilter: [],
      items: [],
      filterSelect: {},
    };
  },
  props: {
    dataSearch: VueTypes.array,
    dataSubSearch: VueTypes.array,
  },
  watch: {
    dataSearch: {
      immediate: true,
      handler() {
        if (this.dataSearch) {
          this.dataFilter = this.dataSearch;
          this.getOptions();
        }
      },
    },
    dataSubSearch: {
      handler() {
        if (this.dataSubSearch) {
          this.dataSubfilter = this.dataSubSearch;
          this.getOptions();
        }
      },
      deep: true,
    },
  },
  methods: {
    getOptions() {
      this.jobsList = this.dataFilter.map((v) => v.jobTitleText).sort();
      this.coutryList = this.dataFilter.map((v) => v.locationName).sort();
      const values = [
        {
          label: "Company",
          ico: "mdi-chevron-down",
          title: this.dataSubfilter.map((v) => v.companyName).sort(),
          value: null,
        },
        {
          label: "Salary",
          ico: "mdi-chevron-down",
          title: this.dataSubfilter.map((v) => v.annualWage).sort(),
          value: null,
        },
        {
          label: "Type of work",
          ico: "mdi-chevron-down",
          title: this.dataSubfilter.map((v) => v.typeWork).sort(),
          value: null,
        },
      ];
      this.items = values;
    },
    getFilters(value) {
      this.$emit("filterSelect", value);
    },
  },
};
</script>

<style lang="scss" scoped>
.search-list {
  .btn-action {
    display: flex;
    justify-content: flex-end;
  }
}
</style>

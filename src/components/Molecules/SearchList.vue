<template>
  <div class="search-list">
    <v-row>
      <v-col cols="12" sm="5">
        <TextField
          :dataText="dataText[0]"
          @responseText="filterSelect.jobTitleText = $event"
        />
      </v-col>
      <v-col cols="12" sm="5">
        <TextField
          :dataText="dataText[1]"
          @responseText="filterSelect.locationName = $event"
        />
      </v-col>
      <v-col cols="12" sm="2" class="btn-action">
        <ButtonCustom :textBtn="textBtn" @click="getFilters(filterSelect)" />
      </v-col>
    </v-row>
    <v-row>
      <v-col
        cols="12"
        sm="4"
        class="filters-bottom"
        v-for="(item, i) in items"
        :key="item.text"
      >
        <div class="menu-datalhe">
          <Autocomplete
            :dataFilter="item"
            @responseSelected="items[i].value = $event"
          />
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import VueTypes from "vue-types";
import ButtonCustom from "@/components/Atoms/ButtonCustom.vue";
import Autocomplete from "./Autocomplete.vue";
import TextField from "./TextField.vue";

export default {
  name: "SearchList",
  components: {
    ButtonCustom,
    Autocomplete,
    TextField,
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
      textBtn: "Search",
      dataText: [
        { label: "Job title or keyword", icon: "mdi-magnify" },
        { label: "Country or timezone", icon: "mdi-magnify" },
      ],
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
    items: {
      handler: "getSubFilter",
      deep: true,
    },
  },
  methods: {
    unique(value, index, self) { 
      return self.indexOf(value) === index;
    },
    getOptions() {
      this.jobsList = this.dataFilter.map((v) => v.jobTitleText).sort();
      this.coutryList = this.dataFilter.map((v) => v.locationName).sort();
      const tWork = this.dataSubfilter.map((v) => v.typeWork);
      const works = [];
      for (let i = 0; i < tWork.length; i++) {
        for (let x = 0; x < tWork[i].length; x++) {         
          if(works.indexOf(tWork[i][x]) === -1){
            works.push(tWork[i][x])
          }         
        }        
      }
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
          title: works.sort(),
          value: null,
        },
      ];
      this.items = values;
    },
    getFilters(value) {
      this.$emit("responseSelect", value);
    },
    getSubFilter() {
      const data = {
        companyName: this.items[0].value,
        annualWage: this.items[1].value,
        typeWork: this.items[2].value,
      };
      this.$emit("responseSubFilter", data);
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

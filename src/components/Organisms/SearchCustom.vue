<template>
  <div class="serach-custom">
    <v-row>
      <v-col cols="12" sm="12" class="info-site">
        <p v-html="fitMsg" />
        <h1 v-html="title" />
        <p>
          Find your next remote job at compaines like
          <span>Intercom, Spotify, Square,</span> and <span>Twitter</span>.
        </p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <SearchList
          :dataSearch="dataResults"
          :dataSubSearch="filterSelect"
          @responseSelect="aplyFilter($event)"
          @responseSubFilter="aplySubFilter($event)"
        />
      </v-col>
    </v-row>
    <ContentResults :dataResults="filterSelect" />
  </div>
</template>

<script>
import axios from "axios";
import SearchList from "@/components/Molecules/SearchList.vue";
import ContentResults from "@/components/Organisms/ContentResults.vue";

export default {
  name: "SearchCustom",
  components: {
    SearchList,
    ContentResults,
  },
  data() {
    return {
      fitMsg: "Remote jobs",
      title: "Remote jobs",
      description: "",
      dataResults: [],
      filterSelect: [],
    };
  },
  mounted() {
    this.getData();
  },
  methods: {
    aplyFilter(value) {
      const listAll = this.dataResults;
      const filterJob = listAll.filter(
        (job) =>
          job.jobTitleText.indexOf(value.jobTitleText) !== -1 ||
          job.locationName.indexOf(value.locationName) !== -1,
      );
      this.filterSelect = filterJob.length > 0 ? filterJob : listAll;
    },
    aplySubFilter(value) {
      const preFilter = this.filterSelect;
      const subFilter = preFilter.filter(
        (sub) =>
          sub.companyName === value.companyName ||
          sub.annualWage === value.annualWage ||
          sub.typeWork.indexOf(value.typeWork) !== -1,
      );
      this.filterSelect = subFilter.length > 0 ? subFilter : preFilter;
    },
    async getData() {
      const { data } = await axios.get("http://localhost:3000/jobs");
      this.dataResults = data;
      this.filterSelect = data;
    },
  },
};
</script>

<style lang="scss" scoped>
.serach-custom {
  margin-top: 30px;
  padding-bottom: 80px;
  .info-site {
    span {
      color: #7752b4;
      font-weight: 600;
    }
    h1 {
      font-size: 2.2em;
      font-weight: 500;
      margin-bottom: 10px;
    }
    p {
      padding: 0;
      margin: 0;
      font-size: 0.9em;
      color: #777a8d;
    }
    p:first-child {
      font-size: 0.9em;
      margin-bottom: 20px;
    }
  }
}
</style>

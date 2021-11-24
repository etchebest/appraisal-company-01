<template>
  <div class="result-container">
    <div>
      <v-avatar color="primary" size="40"
        ><img :src="dataResult.companyLogoUrl" alt="Icone"
      /></v-avatar>
    </div>
    <div>
      <h2>{{ dataResult.jobTitleText }}</h2>
      <p class="subtitle">
        Linear
        <span class="salary">
          <v-icon class="icon">mdi-account-multiple-outline</v-icon> 11-50
          <v-icon class="icon">mdi-currency-usd</v-icon>
          {{
            dataResult.annualWage.toLocaleString('USD')
          }}
        </span>
        <span class="tags caption">{{ dataResult.locationName }}</span>
      </p>
      <span
        v-for="(tag, i) in dataResult.typeWork"
        :class="`tags caption mr-3 tags-color-${i + 1}`"
        :key="i"
      >
        {{ tag }}
      </span>
    </div>
    <span class="date-register"> 2 hours ago</span>
  </div>
</template>

<script>
import VueTypes from "vue-types";

export default {
  name: "ResultsContainer",
  props: {
    dataResult: VueTypes.object,
  },
};
</script>

<style lang="scss" scoped>
.result-container {
  background-color: #fff;
  min-width: 50px;
  position: relative;
  display: flex;
  flex-flow: row wrap;
  border: 1px solid rgb(219, 219, 219);
  border-radius: 8px;
  justify-content: flex-start;
  padding: 15px;
  div:nth-child(1) {
    width: 50px;
  }
  div:nth-child(2) {
    h2 {
      font-size: 1em;
      font-weight: 600;
    }
    .subtitle {
      font-size: 0.8em;
      font-weight: 600;
    }
  }
  .date-register {
    position: absolute;
    font-size: 0.9em;
    right: 0;
    padding: 0 15px;
    color: #747991;
    font-weight: 600;
  }
  .salary {
    color: #747991;
    font-weight: 400;
    margin: 0 10px;
  }
  .icon {
    font-size: 1.3em;
  }
  .tags {
    padding: 3px 8px;
    border-radius: 8px;
    font-weight: 600;
    background-color: #ececf2;
  }
  .tags-color-2 {
    background-color: #d1eaf8;
    color: rgb(67, 190, 251);
  }
  .tags-color-1 {
    background-color: #eddff8;
    color: #c186f1;
  }
}
</style>

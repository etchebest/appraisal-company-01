<template>
  <div class="content-results">
    <v-row>
      <v-col cols="12" sm="8" class="results">
        <div v-for="(item, i) in dataResults" :key="i">
          <ResultContainer :dataResult="item" />
        </div>
      </v-col>
      <v-col cols="12" sm="4">
        <div class="newslatter">
          <div>
            <v-avatar color="#dfd7ff" size="40" class="mb-5">
              <v-icon color="#c186f1">mdi-email-multiple-outline</v-icon>
            </v-avatar>
            <h2>Weekly newslater</h2>
            <p>
              We'll keep you updated when the best new remote jobs pop up on
              Himalayas
            </p>
            <v-text-field
              background-color="#fff"
              label="Enter you email"
              single-line
              outlined
              dense
            ></v-text-field>
            <span class="privacy">
              We care about your data in our
              <a href="#">privacy policy</a>
            </span>
            <ButtonCustom class="mt-4" block :textBtn="'Subscribe'" />
          </div>
        </div>
        <div class="popular-searches">
          <h2>Popular Search</h2>
          <div v-for="(search, i) in searches" :key="i" class="ps-results">
            <p>{{ search.title }}</p>
            <p class="tags-color">{{ search.result }} jobs</p>
          </div>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import VueTypes from "vue-types";
import ResultContainer from "@/components/Molecules/ResultContainer.vue";
import ButtonCustom from "../Atoms/ButtonCustom.vue";

export default {
  name: "ContentResults",
  components: {
    ResultContainer,
    ButtonCustom,
  },
  data() {
    return {
      searches: [
        { title: "Product Designer", result: 204 },
        { title: "Customer Success", result: 80 },
        { title: "Product Manager", result: 120 },
      ],
    };
  },
  props: {
    dataResults: VueTypes.array,
  },
};
</script>

<style lang="scss" scoped>
.content-results {
  .results {
    div {
      margin-bottom: 15px;
    }
  }
  .newslatter,
  .popular-searches {
    min-width: 300px;
    width: 100%;
    height: auto;
    background-color: #e8e2ff;
    border-radius: 8px;
    padding: 20px;
    color: #a688d2;
    font-weight: 400;
    h2 {
      font-size: 1em;
      color: #4d347d;
      font-weight: 600;
      margin: 10px 0;
    }
    p {
      font-size: 0.9em;
    }
    .privacy {
      font-size: 0.8em;
    }
    .tf-new {
      background-color: #fff;
    }
  }
  .popular-searches {
    margin-top: 15px;
    h2,
    p {
      color: rgb(34, 34, 34);
    }
    .ps-results {
      font-size: 0.85em;
      font-weight: 600;
      display: flex;
      flex-flow: row wrap;
      justify-content: space-between;
      p:last-child {
        color: #bb74f5;
      }
    }
  }
}
.tags-color {
  background-color: #e1d2f0;
  padding: 1px 8px;
  border-radius: 8px;
}
</style>

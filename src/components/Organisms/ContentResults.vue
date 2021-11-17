<template>
  <div class="content-results">
    <v-row>
      <v-col cols="12" sm="8" class="results">
        <ResultContainer />
        <ResultContainer />
        <ResultContainer />
        <ResultContainer />
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
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ResultContainer from '@/components/Molecules/ResultContainer.vue';
import ButtonCustom from '../Atoms/ButtonCustom.vue';

export default {
  name: 'ContentResults',
  components: {
    ResultContainer,
    ButtonCustom,
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
  .newslatter {
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
    .privacy{
      font-size: 0.8em;
    }
    .tf-new {
      background-color: #fff;
    }
  }
}
</style>

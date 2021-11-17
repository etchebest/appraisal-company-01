<template>
  <div class="serach-custom">
    <v-row>
      <v-col cols="12" sm="12" class="info-site">
        <p v-html="fitMsg" />
        <h1 v-html="title" />
        <p>
          Find your next remote job at compaines like <span>Intercom, Spotify, Square,</span> and
          <span>Twitter</span>.
        </p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <SearchList />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import SearchList from '@/components/Molecules/SearchList.vue';

export default {
  components: { SearchList },
  name: 'SearchCustom',
  data() {
    return {
      fitMsg: 'Remote jobs',
      title: 'Remote jobs',
      description: '',
    };
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

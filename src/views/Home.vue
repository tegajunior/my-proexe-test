<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Youruhhh Vue.js App"/> -->
    <v-form v-model="valid">
      <v-row justify="space-between" align="center">
        <v-col cols="12" md="7" lg="5">
          <v-text-field
            v-model="image"
            label="Search image"
            :rules="searchTextRules"
            hide-details="auto"
          ></v-text-field>
        </v-col>
        <v-col cols="12" md="3" lg="4" class="mt-4">
          <v-btn color="success" :disabled="!valid" @click="search">
            Search
          </v-btn>
        </v-col>
      </v-row>
    </v-form>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
// const apiKey = AIzaSyAVTFBHujc8Cr-CpR7KO4UFiRu9lrFXr7Q
//const serpApi_Api_Key = 8e1dfbe59979db78fdf1396969dc8b91a78546ee7157247df7685273739bb661
import GoogleImages from 'google-images';
const client = new GoogleImages(
  'cc93b476cdcef1a55',
  'AIzaSyAVTFBHujc8Cr-CpR7KO4UFiRu9lrFXr7Q'
);

export default {
  name: 'Home',
  mounted() {

  },
  data() {
    return {
      valid: true,
      searchTextRules: [
        (value) => !!value || 'Required.',
        (value) => (value && value.trim().length >= 1) || 'Enter a character',
      ],
      image: '',
    };
  },
  methods: {
    async search() {
      let res = await fetch('https://serpapi.com/search.json?q=Apple&tbm=isch&ijn=0&api_key=8e1dfbe59979db78fdf1396969dc8b91a78546ee7157247df7685273739bb661', {mode: 'no-cors', method: 'GET'});
      console.log(res)
   
    },
  },
  components: {
    // HelloWorld
  },
};
</script>

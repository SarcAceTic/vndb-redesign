<script setup>
import apiTok from '/Frontend Works/vndb-redesign/sensitive-information.json'
import axios from 'axios'
import { ref, onMounted } from 'vue'
import LandingHeader from './LandingHeader.vue'

const options = {
 method: 'GET',
 url: 'https://api.vndb.org/kana/stats',
 headers: {
  Authorization: `token ${apiTok.apiToken}`
 }
}

let somevn = await axios.request(options)

console.log(somevn)
</script>

<template>
 <main>
  <div class="landing-image h-screen">
   <v-container class="fill-height">
    <LandingHeader />
    <v-row class="unlayered">
     <v-col cols="12"><h1 class="">Visual Novel Database</h1></v-col>
     <v-col cols="12"><p class="">Get the most accurate, up-to-date Visual Novels</p></v-col>
    </v-row>
    <v-row>
     <v-col cols="12"
      ><p>{{ somevn.data.vn }}</p></v-col
     >
    </v-row>
   </v-container>
  </div>
 </main>
</template>

<style scoped>
.landing-image {
 width: 100%;
 background-size: cover;
 background-image: url('/vndb-redesign-landing.png');
}
.landing-image::before {
 content: '';
 position: absolute;
 top: 0;
 right: 0;
 bottom: 0;
 left: 0;
 background: rgba(0, 0, 0, 0.5);
}
.unlayered {
  position: relative;
  z-index: 0;
}
</style>

<script setup>
import apiTok from '/Frontend Works/vndb-redesign/sensitive-information.json'
import axios from 'axios'
import { ref, onMounted } from 'vue'

const options = {
 method: 'POST',
 url: 'https://api.vndb.org/kana/vn',
 headers: {
  Authorization: `token ${apiTok.apiToken}`,
  'Content-Type': 'application/json'
 },
 data: {
  fields: 'title, image.url, length, rating, description',
  results: '4',
  reverse: true,
  sort: 'released'
 }
}

const lateVns = await axios.request(options)

console.log(lateVns)
</script>

<template>
 <v-container>
  <section>
   <h1 class="mb-5 d-flex justify-space-between">Latest Visual Novels<a><span>View all novels</span></a></h1>
   <v-row>
    <v-col cols="3" v-for="vn in lateVns.data.results">
      <img class="card-image" :src="vn.image.url" />
      <h3>{{ vn.title }}</h3>
    </v-col>
   </v-row>
  </section>
 </v-container>
</template>

<style scoped>
.card-image {
 object-fit: cover;
 height: 100%;
 width: 100%;
}
.custom-height {
  height: 100%;
}
span {
  font-size: 15px;
}
</style>

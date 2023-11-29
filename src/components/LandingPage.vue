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
  <LandingHeader />
  <div class="landing-image h-screen">
   <v-container class="fill-height">
    <v-row class="unlayered align-center" no-gutters>
     <v-col cols="6"
      ><v-col
       ><v-col cols=""><h1 class="">Visual Novel Database</h1></v-col>
       <v-col cols=""
        ><p class="">
         VNDB.org strives to be a comprehensive database for information about visual novels.
         website is built as a wiki, meaning that anyone can freely add and contribute information
         to the database, allowing us to create the largest, most accurate and most up-to-date
         visual novel database on the web.
        </p></v-col
       >
       <v-col
        ><v-btn class="mr-5" color="blue-darken-1" elevation="10"
         >See Visual Novels<template v-slot:append
          ><v-icon>mdi-arrow-right</v-icon></template
         ></v-btn
        ><v-btn variant="outlined">Sign Up</v-btn></v-col
       ></v-col
      ></v-col
     >
     <v-col cols="6"
      ><v-col cols="12" class="text-center vn-data"
       ><h3>
        <v-icon color="green">mdi-circle-small</v-icon>{{ somevn.data.vn.toLocaleString() }}
       </h3>
       <h5>Visual Novels</h5></v-col
      ></v-col
     >
     <v-col cols="12" class="mt-10"
      ><v-row class="other-data"
       ><v-col cols="" class="text-center"
        ><h3>
         <v-icon color="green">mdi-circle-small</v-icon>{{ somevn.data.chars.toLocaleString() }}
        </h3>
        <h5>Characters</h5></v-col
       >
       <v-col cols="" class="text-center"
        ><h3>
         <v-icon color="green">mdi-circle-small</v-icon>{{ somevn.data.producers.toLocaleString() }}
        </h3>
        <h5>Producers</h5></v-col
       >
       <v-col cols="" class="text-center"
        ><h3>
         <v-icon color="green">mdi-circle-small</v-icon>{{ somevn.data.releases.toLocaleString() }}
        </h3>
        <h5>Releases</h5></v-col
       >
       <v-col cols="" class="text-center"
        ><h3>
         <v-icon color="green">mdi-circle-small</v-icon>{{ somevn.data.tags.toLocaleString() }}
        </h3>
        <h5>Tags</h5></v-col
       >
       <v-col cols="" class="text-center"
        ><h3>
         <v-icon color="green">mdi-circle-small</v-icon>{{ somevn.data.traits.toLocaleString() }}
        </h3>
        <h5>Traits</h5></v-col
       >
      </v-row>
     </v-col>
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
 background: rgba(0, 0, 0, 0.6);
}
.unlayered {
 position: relative;
 z-index: 0;
}
.vn-data {
 font-size: 40px;
}
.other-data {
 font-size: 25px;
}
</style>

<script setup>
import { ref } from 'vue'

let drawer = ref(false)
const profileMenu = [
 { name: 'Profile', href: 'blank' },
 { name: 'Your List', href: 'blank' }
]
</script>

<template>
 <header>
  <v-app class="bg-transparent">
   <v-app-bar class="bg-transparent" elevation="1">
    <v-col
     ><v-app-bar-title class="ml-10"><span>VNDB.org</span></v-app-bar-title>
    </v-col>
    <v-col>
     <v-btn class="ml-5 text-none w-50 justify-start border"
      ><template v-slot:prepend><v-icon size="25">mdi-magnify</v-icon></template
      >Search</v-btn
     ></v-col
    >
    <template v-slot:append>
     <v-row class="align-center mr-5">
      <v-col
       ><v-btn icon href="https://www.patreon.com/vndb" target="_blank"
        ><v-icon>mdi-patreon</v-icon></v-btn
       >
      </v-col>
      <v-divider class="border-opacity-25" vertical></v-divider>
      <v-col><v-btn href="/" class="bg-transparent">Home</v-btn></v-col>
      <v-col><v-btn class="bg-transparent">FAQ</v-btn></v-col>
      <v-col><v-btn class="bg-transparent">API</v-btn></v-col>
      <v-divider class="border-opacity-25" vertical></v-divider>
      <v-col>
       <v-btn icon><v-icon>mdi-bell</v-icon></v-btn>
      </v-col>
      <v-col>
       <v-avatar>
        <v-img src="/pfpplaceholder.jpeg"></v-img>
        <v-menu activator="parent">
         <v-list>
          <v-list-item v-for="menuItem in profileMenu">
           <h4>{{ menuItem.name }}</h4>
          </v-list-item>
         </v-list>
        </v-menu>
       </v-avatar>
      </v-col>
     </v-row>
    </template>
   </v-app-bar>
  </v-app>
 </header>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Hind:wght@300;400;500;600;700&family=Montserrat:wght@100;200;300;400;500;600;700;800;900&display=swap');
</style>

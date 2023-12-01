<script setup>
import LandingPage from '../components/LandingPage.vue';
import LandingVN from '../components/LandingVN.vue';
import { ref, onMounted } from 'vue'
</script>

<template>
  <Suspense>
    <LandingPage />
  </Suspense>
  <Suspense>
    <LandingVN class="mt-8" />
  </Suspense>
</template>

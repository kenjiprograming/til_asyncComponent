<script setup>
import PersonOne from './components/PersonOne.vue'
import NowLoading from './components/NowLoading.vue'
import ErrorComp from './components/ErrorComp.vue'
import { defineAsyncComponent } from 'vue'
import { ref } from 'vue'

const PersonTwo = defineAsyncComponent({
  loader: () => import('./components/PersonTwo.vue'),
  loadingComponent: NowLoading,
  errorComponent: ErrorComp,
  timeout: 3000
})
const PersonThree = defineAsyncComponent({
  loader: () => import('./components/PersonThree.vue'),
  loadingComponent: NowLoading,
  errorComponent: ErrorComp,
  timeout: 3000
})

const pageNum = ref(1)
</script>

<template>
  <h1>海外の著名人の名言集</h1>

  <PersonOne v-if="pageNum === 1" />
  <PersonTwo v-if="pageNum === 2" />
  <PersonThree v-if="pageNum === 3" />

  <button @click="pageNum = 1">1</button>
  <button @click="pageNum = 2">2</button>
  <button @click="pageNum = 3">3</button>
</template>

<template>
  <div class="bg-neutral">
    <app-header />
    <div class="container bg-olive my-5">
    </div>
    <app-footer />
  </div>
</template>

<script>
import AppHeader from './components/TheHeader.vue'
import AppFooter from './components/TheFooter.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppFooter
  }
}
</script>

<style>
  .bg-orange{background-color: #ffc168;}
  .bg-green{background-color: #c0de9e}
  .bg-neutral{background-color: #e6e9e2}
  .bg-grey{background-color:#3C403D}
</style>


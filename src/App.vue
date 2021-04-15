<template>
  <div class="bg-neutral">
    <app-header />
    <div class="bg-olive m-5">
      <show-colors />
    </div>
    <app-footer />
  </div>
</template>

<script>
import AppHeader from './components/TheHeader.vue'
import AppFooter from './components/TheFooter.vue'
import ShowColors from './components/ShowColors'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppFooter,
    ShowColors
  },
  data(){
    return{
      colors: [],
    }
  }
}
</script>

<style>
  .bg-orange{background-color: #ffc168;}
  .bg-neutral{background-color: #e6e9e2}
  .bg-grey{background-color:#3C403D}
</style>


<template>
  <div class="bg-neutral">
    <app-header />
    <main class="bg-olive m-5">
      <colors-display />
      <plan-display />
      <shopping-list-display />
      <wardrobe-display />
    </main>
    <app-footer />
  </div>
</template>

<script>
import AppHeader from './components/TheHeader.vue'
import AppFooter from './components/TheFooter.vue'
import ColorsDisplay from './components/ColorsDisplay'
import PlanDisplay from './components/PlanDisplay'
import ShoppingListDisplay from './components/ShoppingListDisplay'
import WardrobeDisplay from './components/WardrobeDisplay'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppFooter,
    ColorsDisplay,
    PlanDisplay,
    ShoppingListDisplay,
    WardrobeDisplay
  },
  data(){
    return{
      colors: [],
    }
  }
}
</script>

<style>
  html {font-size: 1.1rem}

  .bg-orange{background-color: #ffc168;}
  .bg-neutral{background-color: #e6e8e3}
  .bg-grey{background-color:#3C403D}

  section{
    background-color: #edefeb;
    padding: 40px 30px;
    margin-bottom: 30px;
    border-radius: 5px;
  }  
</style>


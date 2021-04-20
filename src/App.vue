<template>
  <div class="bg-neutral">
    <app-header />
    <main class="bg-olive m-5">
      <colors-display
        :userColors="user.colors"
        :colorsNotSet="user.colorsNotSet"
        @colorsChanged="user.colors = $event.slice()"
        @choseColors="user.colorsNotSet = false"
      />
      <plan-display
        :userPlan="user.plan"
        @planChanged="Object.assign(user.plan, $event)"
      />
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
      user: {
        username: "guest",
        colorsNotSet: false,
        colors: [
          "#C57C7C",
          "#768A3D",
          "#7A1A1A",
          "#4b3520",
          "#ffffff"
        ],
        plan: {
          coats: {value: "kabáty", quantity: 2},
          sweaters: {value: "svetry", quantity: 5},
          tops: {value: "trička", quantity: 15},
          skirts: {value: "sukně", quantity: 7},
          pants: {value: "kalhoty", quantity: 1},
          shorts: {value: "kraťasy", quantity: 1},
          dresses: {value: "šaty", quantity: 4},
          formal: {value: "společenské šaty", quantity: 1},
          shoes: {value: "boty", quantity: 4},
          bags: {value: "kabelky", quantity: 2},
          accessories: {value: "doplňky, šperky", quantity: 10},
          topsHome: {value: "domácí trička", quantity: 3},
          bottomsHome: {value: "tepláky", quantity: 2},
          sleepHome: {value: "pyžama/košilky", quantity: 2},
          hoodies: {value: "mikiny", quantity: 1},
        },
        shoppingList: {},
        wardrobe: [],
      },
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


<script>
import PresentationCard from "./PresentationCard.vue";
  export default {
    name: 'Cards',
    components: {
      PresentationCard
    },
    props:{
      cardsList: {
        type: Array,
        default: [],
      },

      mounted(){
        console.log('Cards mounted');
      },

      updated(){
        console.log('Cards updated');
      },

    }
  }
</script>


<template>
  <div class="cards" v-for="card in cardsList" v-bind:key="card.id">
    <PresentationCard v-bind:card="card" :name="card.name" v-bind:job="card.job" v-bind:paletteName="card.palette"></PresentationCard>
  </div>
</template>

<style>
</style>

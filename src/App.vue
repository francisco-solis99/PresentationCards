<!-- JS -->
<script>
  import Cards from './components/Cards.vue';
  import AddCard from './components/AddCard.vue';
  export default {
    name: 'App',
    components: {
      Cards, AddCard
    },

    data(){
      return {
        cardsList: localStorage.getItem('cardsList') ? JSON.parse(localStorage.getItem('cardsList')) : [],
        copyCards: [],
      }
    },

    methods: {
      addCard(card){
        card.id = this.cardsList.length;
        this.cardsList.push(card);
        localStorage.setItem('cardsList', JSON.stringify(this.cardsList));
        this.copyCards = [...this.cardsList, ...this.defaultUsers];
      },
    },

    created(){
      console.log('App created');
      this.copyCards = [...this.cardsList, ...this.defaultUsers];
    },

    updated(){
      console.log('App updated');
    },

    computed: {
      defaultUsers() {
        return [
          {
            id: 0,
            name: 'Juan',
            job: 'Digital Creator',
            palette: 'lofi',
          },
          {
            id: 1,
            name: 'Richard',
            job: 'Backend Developer',
            palette: 'cold',
          },
          {
            id: 2,
            name: 'Francisco',
            job: 'Frontend Developer',
            palette: 'warm',
          },
        ];
      }
    },
  }
</script>


<!-- HTML -->
<template v-cloak>
  <header>
    <h1 class="app__title">Presentation Cards </h1>
  </header>
  <section class="cards">
    <Cards v-bind:cardsList="copyCards"/>
  </section>
  <AddCard v-on:create-card="addCard"></AddCard>
</template>


<!-- CSS -->
<style>
  body {
    margin: 0;
    padding: 0;
    font-family: monospace;
  }

  .cards {
    padding: 20px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    place-content: center;
    justify-items: center;
  }

  .app__title {
    margin-bottom: 30px;
    text-align: center;
    font-size: 2rem;
    text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.25);
    color: rgb(153, 42, 180);
  }

</style>



<!-- cardsList: [
          {
            id: 0,
            name: 'Juan',
            job: 'Digital Creator',
            palette: 'lofi',
          },
          {
            id: 1,
            name: 'Richard',
            job: 'Backend Developer',
            palette: 'cold',
          },
          {
            id: 2,
            name: 'Francisco',
            job: 'Fronteend Developer',
            palette: 'warm',
          },
        ], -->

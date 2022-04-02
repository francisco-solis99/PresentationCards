<script>
import PresentationCard from './components/PresentationCard.vue';
  export default {
    name: 'App',
    components: {
      PresentationCard
    },

    data(){
      return {

      }
    },

    methods: {
      closeModal(){
          const modal = document.querySelector('dialog');
          modal.close()
      }
    },

    mounted() {
      const dialog = document.querySelector('dialog');
      const show = document.querySelector('#show');
      show.addEventListener('click', () => dialog.showModal());
    },
  }
</script>

<template v-cloak>
  <header>
    <h1 class="app__title">Presentation Cards </h1>
  </header>
  <section class="cards">
    <PresentationCard name="Juan" job="Digital Creator" paletteName="lofi"></PresentationCard>
    <PresentationCard name="Richard" job="Backend Dev" paletteName="cold"></PresentationCard>
    <PresentationCard name="Francisco" job="Frontend Dev" paletteName="warm"></PresentationCard>
  </section>
  <button id="show" class="add__btn">
  </button>
</template>

<style>
  body {
    margin: 0;
    padding: 0;
    font-family: monospace;
  }

  .app__title {
    margin-bottom: 30px;
    text-align: center;
    font-size: 2rem;
    text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.25);
    color: rgb(153, 42, 180);
  }

  .cards {
    padding: 20px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    place-content: center;
    justify-items: center;
  }

  .add__btn {
    width: 50px;
    height: 50px;
    position: fixed;
    bottom: 20px;
    right: 20px;
    border-radius: 50%;
    border: 0;
    background: rgb(153, 42, 180);
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.25);
    cursor: pointer;
  }

  .add__btn::before, .add__btn::after {
    content: '';
    display: block;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    background: rgb(255, 255, 255);
  }

  .add__btn::before{
    width: 5px;
    height: 60%;
  }

  .add__btn::after{
    width: 60%;
    height: 5px;
  }

  .add__btn:active {
    transform: scale(1.1);
  }

</style>

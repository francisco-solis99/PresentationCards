<script>
  export default {
    name: 'Cards',
    props:{
    }
  }
</script>


<template>
  <section class="cards">

  </section>
</template>

<style scoped>
  .cards {
    padding: 20px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    place-content: center;
    justify-items: center;
  }
</style>

<script>
  const palettes = [
          {
            id: 0,
            name: 'lofi',
            bgcolor: '#cfbaf0',
            lineColor: '#ffcfd2',
            fontColor: '#fff'
          },
          {
            id:1,
            name: 'cold',
            bgcolor: '#005f73',
            lineColor: '#94d2bd',
            fontColor: '#fff'
          },
          {
            id:2,
            name: 'warm',
            bgcolor: '#ff9f1c',
            lineColor: '#ffd6a5',
            fontColor: '#fff'
          },
  ];

  export default {
    name: 'PresentationCard',
    props: {
      name: {
        type: String,
        default: 'Somebody',
        required: false,
        validator: value => value.length > 3
      },

      job: {
        type: String,
        default: 'Some job',
        required: false,
      },

      paletteName: {
        type:String || Object,
        required: false,
      },
    },

    data() {
      return {
        palette: this.getPalette(this.paletteName),
      }
    },
    computed: {},
    methods: {
      getPalette(palette){
        if(typeof palette === 'string') return palettes.find(p => p.name === palette);
        return palette;
      },
    },
  }
</script>


<template>
  <article class="card">
    <div class="card__container">
      <h1 class="card__name">{{name}}</h1>
      <h3 class="card__job">{{job}}</h3>
    </div>
  </article>
</template>



<style scoped>

  .card {
    width: 250px;
    height: 250px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 20px 0;
    font-family: monospace, sans-serif;
    color: v-bind(palette.fontColor);
    box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.25);
    animation: dance 1.5s infinite alternate;
    background: linear-gradient(-45deg, transparent 10%, v-bind(palette.lineColor) 10% 20%, transparent 20% 25%, v-bind(palette.lineColor) 25% 35%, transparent 35% 60%, v-bind(palette.lineColor) 60% 70%, transparent 70% 75%, v-bind(palette.lineColor) 75% 85%, transparent 85%);
    background-color: v-bind(palette.bgcolor);
  }

  @keyframes dance {
    0% {
      transform: translateY(15px);
    }
    100% {
      transform: translateY(0);
    }
  }
  .card__container {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    transform: rotate(-45deg) translateY(7px);
  }

  h1,h3 {
    margin: 0;
  }
  .card__name {
    font-size: 1.8rem;
  }
   .card__job {
    margin-top: 8px;
    font-size: 1rem;
    font-weight: 400;
  }

</style>

<script>

  const palettesAvailable = [
    {
      name: 'lofi',
      bgcolor: '#cfbaf0',
      lineColor1: '#ffcfd2',
      lineColor2: '#f1c0e8',
      fontColor: '#fff'
    },
    {
      name: 'cold',
      bgcolor: '#005f73',
      lineColor1: '#94d2bd',
      lineColor2: '#e9d8a6',
      fontColor: '#fff'
    },
    {
      name: 'warm',
      bgcolor: '#ff9f1c',
      lineColor1: '#ffd6a5',
      lineColor2: '#ffadad',
      fontColor: '#fff'
    },
  ];

  const getPalette = (namePalette) => {
    if(!namePalette) return undefined;
    const palette = palettesAvailable.find(item => namePalette.toLowerCase() === item.name);
    return palette;
  }

  export default {
    name: 'PresentationCard',
    props: {
      name: {
        type: String,
        default: 'Durmon',
        required: false,
        validator: value => value.length > 3
      },

      job: {
        type: String,
        required: true,
      },

      paletteName: {
        type:String,
        required: false,
        validator: palette => getPalette(palette)
      },

      paletteObj: {
        type: Object,
        required: false,
      }
    },
    data() {
      return {
        palette: getPalette(this.paletteName) ?? this.paletteObj ?? getPalette('lofi'),
      }
    },
    computed: {},
    methods: {},

    //ciclo de viuda funciones
    created(){
      // check the $props, $data and $el
      console.groupCollapsed('%c PresentationCard created() ','color: green; font-weight: bold;');
      console.log('created');
      console.log(this.$data);
      console.log(this.$el);
      console.groupEnd();
    },

    mounted(){
      // check the $props, $data and $el
      console.groupCollapsed('%c PresentationCard created() ','color: orange; font-weight: bold;');
      console.log('mounted');
      console.log(this.$data);
      console.log(this.$el);
      console.groupEnd();

      // change colors (this could be a function)
      // const card = this.$el;
      // card.style.background = `
      //   linear-gradient(-45deg, transparent 10%,${this.palette.lineColor1} 10% 20%, transparent 20% 25%, ${this.palette.lineColor1} 25% 35%, transparent 35% 60%, ${this.palette.lineColor1} 60% 70%, transparent 70% 75%, ${this.palette.lineColor1} 75% 85%, transparent 85%)`;
      // card.style.color = this.palette.bgcolor;
      // card.style.color = `${this.palette.fontColor}`;
    }
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
    background: linear-gradient(-45deg, transparent 10%, v-bind(palette.lineColor1) 10% 20%, transparent 20% 25%, v-bind(palette.lineColor1) 25% 35%, transparent 35% 60%, v-bind(palette.lineColor1) 60% 70%, transparent 70% 75%, v-bind(palette.lineColor1) 75% 85%, transparent 85%);
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

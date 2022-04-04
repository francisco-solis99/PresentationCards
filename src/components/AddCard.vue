<script>;
  export default {
    name: 'AddCard',
    emits: ['create-card'],
    props:{
    },
    data(){
      return {
        card: {
          id: 0,
          name: '',
          job: '',
          palette: {
              name: '',
              bgcolor: '#000000',
              lineColor: '#ffffff',
              fontColor: '#ffffff',
          },
        },
      }
    },

    methods: {
      openModal(){
        this.$refs.dialog.showModal();
      },
      closeModal(){
        this.$refs.dialog.close();
      },
      handleSubmit(e){
        const copyCard = JSON.parse(JSON.stringify(this.card));
        this.$emit('create-card', copyCard);
        this.cleanFields();
        this.closeModal();
      },
      cleanFields(){
        this.card.name = '';
        this.card.job = '';
        this.card.palette.name = '';
        this.bgcolor = '#000000';
        this.lineColor = '#ffffff';
        this.fontColor = '#ffffff';
      },
    },
  }
</script>


<template>
  <button id="show" class="add__btn" @click="openModal">
  </button>
  <dialog class="modal" ref="dialog">
    <form action="" @submit.prevent="handleSubmit" class="modal__form">
      <label for="name" class="modal__label">
        <span class="modal__span">Name</span>
        <input type="text" class="modal__input" id="name" minlength="3" maxlength="10" required v-model="card.name">
      </label>
      <label for="job" class="modal__label">
        <span class="modal__span">Job</span>
        <input type="text" class="modal__input" id="job" minlength="3" maxlength="30" required v-model="card.job">
      </label>

       <label for="" class="modal__label">
        <span class="modal__span">Background Color</span>
        <div class="color__container">
          <input type="color" class="modal__input" id="back-color" v-model="card.palette.bgcolor" v-once>
          <span class="modal__color-selected">
            {{card.palette.bgcolor}}
          </span>
        </div>
      </label>

      <label for="" class="modal__label">
        <span class="modal__span">Line Color</span>
        <div class="color__container">
          <input type="color" class="modal__input" id="line-color" v-model="card.palette.lineColor">
          <span class="modal__color-selected">
            {{card.palette.lineColor}}
          </span>
        </div>
      </label>

      <label for="" class="modal__label">
        <span class="modal__span">Font Color</span>
        <div class="color__container">
          <input type="color" class="modal__input" id="font-color" v-model="card.palette.fontColor">
          <span class="modal__color-selected">
            {{card.palette.fontColor}}
          </span>
        </div>
      </label>

      <div class="modal__buttons">
        <button type="button" id="cancel" class="modal__btn" @click="closeModal">Cancel</button>
        <button type="submit" class="modal__btn" id="create">Create Card</button>
      </div>
    </form>
  </dialog>
</template>




<style scoped>
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
  /* for modal */
  dialog.modal{
    width: 50%;
    min-width: 250px;
    padding: 20px;
    border: 0;
    border-radius: 10px;
    background-color: rgba(255, 255, 255, 0.90);
  }

  dialog.modal::backdrop {
    background: rgba(0, 0, 0, 0.45);
  }

  .modal__form {
    display: flex;
    flex-direction: column;
  }

  .modal__label {
    display: flex;
    flex-direction: column;
    margin-bottom: 15px;
  }

  .modal__span {
    margin-bottom: 5px;
    font-size: 1rem;
  }

  .color__container {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .modal__input:not([type=color]) {
    padding: 5px;
    font-size: 1rem;
    font-weight: 400;
    outline: none;
    border: 1px dashed rgb(153, 42, 180);

  }

  input:invalid:required {
    border: 2px dashed red;
  }

  input:valid:required {
    border: 2px dashed rgb(153, 42, 180);
  }

  .modal__input[type=color] {
    width: 40%;
    cursor: pointer;
  }

  .modal__color-selected {
    font-size: 0.9rem;
  }

  .modal__buttons {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }

  .modal__btn {
    width: 40%;
    padding: 10px 5px;
    font-weight: 600;
    border: 0;
    border-radius: 10px;
    cursor: pointer;
    color: rgb(255, 255, 255);
  }

  .modal__btn:first-child {
    background: rgb(236, 74, 74);
  }

  .modal__btn:last-child {
    background: rgb(12, 153, 47);
  }
</style>

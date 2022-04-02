<script>
  export default {
    name: 'AddCard',
    props:{
    }
  }
</script>


<template>
</template>




<style>

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

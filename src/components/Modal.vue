<template>
  <div class="modal" :class="modalClasses" :id="getModalId">
    <div class="modal-background"></div>
    <div class="modal-content">
      <div class="box">
        <div class="content has-text-black has-text-centered">{{modalText}}</div><br>
        <button class="button is-danger" @click="activeModal = false">Fechar modal</button>
      </div>
    </div>
    <button class="modal-close is-large" aria-label="close" @click="activeModal = false"></button>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    modalId: Number,
    modalText: String
  },
  
  data: () => ({
    activeModal: false
  }),

  computed: {
    modalClasses: function() {
      return {
        'is-active': this.activeModal
      }
    },

    getModalId: function() {
      return `modal${this.modalId}`
    }
  }
};
</script>

<style>
</style>

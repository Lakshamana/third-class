<template>
  <div id="card-container">
    <div class="column">
      <div class="card">
        <div class="card-image">
          <figure class="image is-4by3">
            <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
          </figure>
        </div>
        <div class="card-content">
          <div class="media">
            <div class="media-left">
              <figure class="image is-48x48">
                <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
              </figure>
            </div>
            <div class="media-content">
              <p class="title is-4 has-text-black">{{displayName}}</p>
              <p class="subtitle is-6 has-text-black">{{userName}}</p>
            </div>
          </div>

          <div class="content">
            {{description}}
            <button
              class="button is-primary"
              id="button"
              @click="toggleActiveModal"
            >Mostrar Modal</button>
          </div>
        </div>
      </div>
    </div>
    <Modal ref="modal"
      :modalId="modal.modalId"
      :modalText="modal.modalText"/>
  </div>
</template>

<script>
import Modal from './Modal'

export default {
  name: 'Card',
  components: {
    Modal
  },

  props: {
    displayName: String,
    userName: String,
    description: String,
    modal: {
      modalId: Number,
      modalText: String
    }
  },

  methods: {
    toggleActiveModal() {
      this.$refs.modal.$data.activeModal = true
    }
  }
};
</script>

<style>
</style>
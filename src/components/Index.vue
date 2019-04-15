<template>
  <div id="index">
    <section class="hero is-success is-fullheight">
      <!-- Hero head: will stick at the top -->
      <div class="hero-head">
        <header class="navbar">
          <div class="container">
            <div class="navbar-brand">
              <a class="navbar-item">
                <img src="https://bulma.io/images/bulma-type-white.png" alt="Logo">
              </a>
              <span class="navbar-burger burger" data-target="navbarMenuHeroC"></span>
            </div>
            <div id="navbarMenuHeroC" class="navbar-menu">
              <div class="navbar-end">
                <a class="navbar-item is-active">Home</a>
                <a class="navbar-item">Examples</a>
                <a class="navbar-item">Documentation</a>
                <span class="navbar-item">
                  <a class="button is-success is-inverted">
                    <span class="icon">
                      <i class="fab fa-github"></i>
                    </span>
                    <span>Download</span>
                  </a>
                </span>
              </div>
            </div>
          </div>
        </header>
      </div>

      <!-- Hero content: will be in the middle -->
      <div class="hero-body">
        <div class="container has-text-centered">
          <div class="columns">
            <Card v-for="(card, id) of cards" 
              :displayName="card.displayName"
              :userName="card.userName"
              :description="card.description"
              :modal="{ modalId: id + 1, modalText: card.modal.modalText}"
              :key="id"/>       
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Card from './Card'
import axios from 'axios'

export default {
  name: 'Index',
  components: {
    Card
  },
  
  methods: {
    getUsers() {
      return axios.get(`https://jsonplaceholder.typicode.com/users`)
        .then(response => {
          let cardArray = []
          response.data.forEach(user => {
            cardArray.push({
              displayName: user.name,
              userName: '@' + user.username,
              description: `Developer at ${user.company.name}`,
              modal: {
                modalText: user.company.catchPhrase
              }
            })
          })
          this.cards = cardArray.filter((value, idx) => idx < 4)
        })
    }
  },

  created() {
    this.getUsers()
  },

  data: () => ({
    cards: []
  })
};
</script>

<style>
</style>

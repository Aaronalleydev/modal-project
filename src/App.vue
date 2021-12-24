<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if="showModal">
    <Modal  theme="sale" @close="toggleModal"> 
      <h1>Ninja Giveaway</h1>
      <p>Grab you nija swag for half price!</p>
      <template v-slot:links>
        <a href="">Sign up now</a>
        <a href="">More Info</a>
      </template>
    </Modal>
  </teleport>

  <teleport to=".modals" v-if="showModalTwo">
    <modal @close="toggleModalTwo"> 
      <h1>This is the new Modal</h1>
      <p>Creating reusable stuff</p>
    </modal>
  </teleport>
  <button @click.alt="toggleModal" >Open Modal (alt)</button>
  <button @click="toggleModalTwo">Show Modal two</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
},
  data() {
    return {
      title: 'My second Vue app',
      header: 'Sign up for the giveaway!',
      text: 'Grab swag for half price',
      showModal: false,
      showModalTwo: false
    }    
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;

}
</style>

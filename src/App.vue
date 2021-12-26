<template>
  <h1>{{ title }}</h1>

  <input type="text" ref="name" />
  <button @click="handleClick">Click me</button>
  <div v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <h1>Slots heading</h1>
      <p>some text</p>
      <template v-slot:links>
        <a href="#">More info</a>
        <a href="#">Sigh up now</a>
      </template>
    </Modal>
  </div>
  <div v-if="showModalTwo">
    <Modal theme="sale" @close="toggleModalTwo">
      <h1>Modal two</h1>
      <p>asasa</p>
      <template v-slot:links>
        <a href="#">More info</a>
        <a href="#">Sigh up now</a>
      </template>
    </Modal>
  </div>
  <p>Welcome...</p>
  <br />
  <button @click.shift="toggleModal">Open modal (shift)</button>
  <button @click="toggleModalTwo">Open modal two</button>
</template>

<script>
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "Vue app",
      header: "Congratulations!",
      text: "You are signed up",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name.value);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

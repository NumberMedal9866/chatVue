<template>
  <Main

  />
  <button class="clear" @click="clearLocal">clear messages</button>

</template>

<script>
import Main from './components/Main.vue'
  export default {
  components: { Main},
    data() {
      return {
        showModal: false,
        showModal2: false,
      }
    },
  methods: {
    clearLocal(){
      localStorage.clear()
      location.reload()
    }
  },
  }
</script>

<style lang="scss" scoped>
  .clear{
    position: fixed;
    @media screen and (max-width:799px) {
        top: 30px;
        height: max-content;
        font-size: 10px;
    }
    right: 30px;bottom: 30px;
    padding: 10px 20px;
    background: white;
    color: #000;
    border-radius: 10px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    transition: 300ms;
    font-size: 20px;
    border: 2px solid black;
  }
  .clear:hover{
    transform: scale(1.2);
  }
</style>
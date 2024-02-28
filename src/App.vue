<template>

  <Modal :onerooms="onerooms" :clickedRoomNum="clickedRoomNum" :modalOpen="modalOpen" ></Modal>

  <div class="menu">
    <a v-for="(a, i) in menus" :key="i" href="">{{a}}</a>
  </div>

  <Discount></Discount>

  <Card :onerooms="onerooms" :clickedRoomNum="clickedRoomNum"></Card>

</template>

<script>

import oneroom from './assets/oneroom';
import Discount from './components/Discount.vue'
import Modal from './components/Modal.vue'
import Card from './components/Card.vue'

export default {
  name: 'App',
  data() {
    return {
      clickedRoomNum : 0,
      modalOpen : false,
      counts : [0, 0, 0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      onerooms : oneroom
    }
  },
  methods : {
    increase(i){
      this.counts[i]++
    }
  },
  components: {
    Discount, Modal, Card
  }
}
</script>

<style>
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}

</style>

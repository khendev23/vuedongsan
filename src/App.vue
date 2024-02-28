<template>
  <Transition name="fade">
    <Modal @closeModal="modalOpen=false" :onerooms="onerooms" :clickedRoomNum="clickedRoomNum" :modalOpen="modalOpen" ></Modal>
  </Transition>

  <div class="menu">
    <a v-for="(a, i) in menus" :key="i" href="">{{a}}</a>
  </div>

  <Discount v-if="showDiscount == true" :discountNum="discountNum"></Discount>

  <button @click="abcSort">가나다순 정렬</button>
  <button @click="priceSort">저렴한순 정렬</button>
  <button @click="priceBackSort">비싼순 정렬</button>
  <button @click="sortBack">원래 정렬</button>

  <Card @openModal="modalOpen = true; clickedRoomNum=$event" :onerooms="onerooms" :clickedRoomNum="clickedRoomNum"></Card>

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
      discountNum : 30,
      showDiscount : true,
      clickedRoomNum : 0,
      modalOpen : false,
      counts : [0, 0, 0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      onerooms : [...oneroom],
      originalOnerooms : oneroom
    }
  },
  methods : {
    increase(i){
      this.counts[i]++
    },
    priceSort() {
      this.onerooms.sort(function(a, b){
        return a.price - b.price
      })
    },
    sortBack() {
      this.onerooms = [...this.originalOnerooms];
    },
    priceBackSort() {
      this.onerooms.sort(function(a, b){
        return b.price - a.price;
      })
    },
    abcSort(){
      this.onerooms.sort(function(a, b){
        return a.title.toLowerCase() < b.title.toLowerCase()? -1 : 1
      })
    }
  },
  mounted() {
    setInterval(()=>{
      if(this.discountNum > 0) {
        this.discountNum--
      } else if(this.discountNum == 0) {
        this.discountNum = 0
      }
    }, 1000)
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
.fade-enter-from {opacity: 0;}
.fade-enter-active{transition: all 1s}
.fade-enter-to{opacity: 1;}
.fade-leave-from {opacity: 1;}
.fade-leave-active{transition: all 1s}
.fade-leave-to{opacity: 0;}
</style>

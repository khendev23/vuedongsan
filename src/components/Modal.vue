<template>
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <img :src="onerooms[clickedRoomNum].image" alt="" class="room-img">
      <p>{{onerooms[clickedRoomNum].title}}</p>
      <p>{{onerooms[clickedRoomNum].content}}</p>
      <p>{{onerooms[clickedRoomNum].price}}원</p>
      <Discount></Discount>
      <!-- <button @click="modalOpen=false">X</button> -->
    </div>
  </div>
</template>

<script>
import Discount from './Discount.vue'


export default {
  name : 'ModalComponent',
  props : {
    onerooms : Array,
    clickedRoomNum : Number,
    modalOpen : Boolean
  },
  components: {
    Discount
  }
}
</script>

<style>
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 
</style>
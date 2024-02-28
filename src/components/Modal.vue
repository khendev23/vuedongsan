<template>
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <img :src="onerooms[clickedRoomNum].image" alt="" class="room-img">
      <p>{{onerooms[clickedRoomNum].title}}</p>
      <p>{{onerooms[clickedRoomNum].content}}</p>
      <input v-model.trim="month">
      <p> {{month}}개월 선택함 : {{onerooms[clickedRoomNum].price * month}}원</p>
      <button @click="$emit('closeModal')">X</button>
    </div>
  </div>
</template>

<script>
export default {
  name : 'ModalComponent',
  data() {
    return {
      month : 1,
    }
  },
  beforeUpdate(){
    if(this.month == 2){
      alert('ㄴㄴ');
      this.month = 3
    }
  },
  watch : {
    month(a){
      if(isNaN(a) == true){
        alert('숫자만 입력하셈');
        this.month = 1
      } else if(a >= 13) {
        alert('13이상 입력하지 마셈')
        this.month = 1
      }
    },
  },
  props : {
    onerooms : Array,
    clickedRoomNum : Number,
    modalOpen : Boolean
  },
  components: {
    
  },
  
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
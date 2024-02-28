<template>
  <div v-for="(oneroom, i) in onerooms" :key="i">
    <img :src="oneroom.image" alt="" class="room-img">
    <h4 @click="$emit('openModal', oneroom.id)">{{oneroom.title}}</h4>
    <!-- <p>{{oneroom.content}}</p> -->
    <p>{{oneroom.price}}원</p>
  </div>
</template>

<script>
export default {
  name : "CardComponent",
  props : {
    onerooms : Array,
    clickedRoomNum : Number
  },
}
</script>

<style>
.room-img {
  width: 80%;
  margin-top: 40px;
}
</style>
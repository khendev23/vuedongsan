<template>
  <div class="discount">
    <h4>지금 결제시 {{discountNum}}% 할인!</h4>
  </div>
</template>

<script>
export default {
  name : 'DiscountComponent',
  data(){
    return {
      
    }
  },
  props : {
    discountNum : Number
  }
}
</script>

<style>
.discount {
  background : #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
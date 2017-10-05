<template>
  <div>header</div>
  <div class="bulletin">
    <span>{{seller.bulletin}}</span>
  </div>
  
</template>
<script>
export default {
   props: {
     seller: {
       type: Object
     }
   }
};
</script>
<style lang="sass">
.bulletin
  height: 28px
  line-height: 28px
  white-space: nowrap
  overflow: hidden
  text-overflow: ellipsis

</style>

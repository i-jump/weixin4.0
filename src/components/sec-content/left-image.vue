<template>
  <!--左图片-->
  <div class="left ImgLeft images">
    <a href="javascript:;"><img class="headImg" :src="msg.headImage" alt=""></a>
    <img class="smallImg" :src="msg.imageArray.turl" alt="">
  </div>
</template>
<script>
    export default{
        data(){
            return {
                msg:this.leftImage
            }
        },
         props:['leftImage']
    }
</script>
<style>

</style>

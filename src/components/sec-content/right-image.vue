<template>
    <!--右图片-->
    <div class="right ImgRight images">
      <a href="javascript:;"><img class="headImg" :src="msg.headImage" alt=""></a>
      <img class="smallImg" :src="msg.imageArray.turl" alt="">
    </div>
</template>
<script>
    export default{
        data(){
          return {
            msg: this.rightImage
          }
        },
        props:['rightImage']
    }
</script>
<style>

</style>

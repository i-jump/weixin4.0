<template>
  <!--右文字-->
  <div class="right TextRight">
    <a href="javascript:;"><img class="headImg" :src="msg.headImage" alt=""></a>
    <p class="left-word">{{msg.content}}</p>
  </div>
</template>
<script>
    export default{
        data(){
            return {
                msg:this.rightText
            }
        },
      props:['rightText']
    }
</script>
<style>

</style>

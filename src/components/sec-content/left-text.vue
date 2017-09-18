<template>
    <div>
      <!--左文字-->
      <div class="left TextLeft">
        <a href="javascript:;"><img class="headImg" :src="msg.headImage" alt=""></a>
        <p class="left-word">{{msg.content}}</p>
      </div>
    </div>
</template>
<script>
    export default{
        data(){
            return {
                msg:this.leftText
            }
        },
        props:['leftText']
    }
</script>
<style>

</style>

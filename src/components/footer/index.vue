<template>
    <div id="footer">
      <a href="javascript:;" v-if="fln" @click="changes"><img class="footer-keyboard fImg" src="../../assets/imgs/wei_03.jpg" alt=""></a>
      <a href="javascript:;" v-else @click="changes"><img class="footer-keyboard fImg" src="../../assets/imgs/yuyin_03.png" alt=""></a>
      <span id="js-voice" class="footer-voice voices" v-if="fln">按住 说话</span>
      <input id="js-txt" class="footer-voice foces" type="text" v-else v-focus>
      <a href="javascript:;"><img class="footer-face fImg" src="../../assets/imgs/wei_005.jpg" alt=""></a>
      <a href="javascript:;"><img class="footer-more fImg" src="../../assets/imgs/wei_006.jpg" alt=""></a>
    </div>
</template>
<script>
    export default{
        data(){
            return {
                fln:true
            }
        },
      methods:{
            changes(){
                this.fln = !this.fln;
            }
      },
      directives:{
            focus:{
                inserted(el){
                    el.focus();
                }
            }
      }
    }
</script>
<style scoped lang="stylus">
    @import "../../assets/stylus/footer.styl";
</style>

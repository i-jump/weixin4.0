<template>
    <div id="main">
      <div v-for="item in lists">
          <left-text v-if="item.type === 'leftText'" :leftText="item"></left-text>
          <right-text v-if="item.type === 'rightText'" :rightText="item"></right-text>
          <left-Image v-if="item.type === 'leftImage'" :leftImage="item">  </left-Image>
          <right-Image v-if="item.type === 'rightImage'" :rightImage="item"> </right-Image>
          <left-sound v-if="item.type === 'leftSound'" :leftSound="item" @audio-play="audioPlay">   </left-sound>
          <right-sound v-if="item.type === 'rightSound'" :rightSound="item" @audio-play="audioPlay">  </right-sound>
      </div>
    </div>
</template>
<script>
  import leftText from "../../components/sec-content/left-text.vue";
  import rightText from "../../components/sec-content/right-text.vue";
  import leftSound from "../../components/sec-content/left-sound.vue";
  import rightSound from "../../components/sec-content/right-sound.vue";
  import leftImage from "../../components/sec-content/left-image.vue";
  import rightImage from "../../components/sec-content/right-image.vue";
  import axios from "axios";
  import $ from "jquery";
    export default{
        data(){
            return{
                lists:"",
                flag:true,
                timer:""
            }
        },
      components:{
        leftText,
        rightText,
        leftSound,
        rightSound,
        leftImage,
        rightImage
      },
      mounted(){
          this.renderList();
      },
      methods:{
          renderList(){
              axios.get("http://localhost:3000/communication").then(res=>{
                  res.data.end === "0" ? this.lists = res.data.posts : "";
              })
          },
          audioPlay(data,msg){
                var audios=data.target;
                var allco=$(audios).find('.co');
                var Ico=$(audios).find('.Ico');
                var nowAudio=$(audios).find('.audioPlay')[0];
                var allImg=$('.co');
                var allaudio=$('.audioPlay');
                if(this.flag){
                    for(var i=0;i<allaudio.length;i++){
                        allaudio[i].currentTime=0;
                    }
                    this.icoPlay(allco);
                    this.autoPlay(nowAudio);
                    allImg.removeClass('imgActive');
                    $('.Ico').addClass('imgActive');
                    //动态set   fla
                    if(typeof msg.fla === 'undefined'){
                      this.$set(msg,'fla',true);
                    }
                }else{
                    for(var i=0;i<allaudio.length;i++){
                      allaudio[i].pause();
                    }
                    clearTimeout(this.timer);
                    this.autoPause(nowAudio);
                    allImg.removeClass('imgActive');
                    $('.Ico').addClass('imgActive');
                }
                this.flag = !this.flag;

          },
          icoPlay(allco){
            var num=0;
            var _this=this;
            function set(){
              _this.timer=setTimeout(function () {
                num++;
                if(num>=allco.length){
                  num=0;
                }
                allco.eq(num).addClass('imgActive').siblings().removeClass('imgActive');
                set();
              },500);
            }
            set();
          },
          autoPlay(el){
              console.log(el);
              el.play();
          },
          autoPause(el){
              el.pause();
              el.currentTime=0;
          }

      }
    }
</script>
<style scoped lang="stylus">
    @import "../../assets/css/section.css";
</style>




















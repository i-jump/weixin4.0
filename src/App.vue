<template>
  <div id="app">
    <div id="wrap">
      <headers></headers>
      <sections></sections>
      <footers></footers>
    </div>
  </div>
</template>
<script>
  //引入组件
  import Headers from "./components/header/header";
  import Sections from "./components/section";
  import Footers from "./components/footer";
  export default {
    name: 'app',
    components:{
      Headers,
      Sections,
      Footers
    }
  }
</script>

<style lang="stylus">
  /*导入公共样式*/
  @import "assets/css/reset.css";
  @import "assets/stylus/app.styl";
</style>

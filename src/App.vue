<template>
  <div id="app" :class="{'app-experiment': isShowGrayBg}">
    <Header />
    <div class="main-content">
      <router-view/>
    </div>
    <Footer />
  </div>
</template>
<script>
import Header from './views/Header'
import Footer from './views/Footer'
export default {
  data () {
    return {
      isShowGrayBg: true
    }
  },
  watch: {
    '$route.name' () {
      this.isShowGrayBg = this.$route.name === 'experiment'
    }
  },
  mounted () {
    this.isShowGrayBg = this.$route.name === 'experiment'
  },
  components: {
    Header,
    Footer
  }
}
</script>>
<style lang="scss">
@import './styles/common.scss';

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  font-size: 14px;
  width: 100%;
  line-height: 1.5;
  font-family: PingFang SC,Tahoma,Helvetica,Arial,Hiragino Sans GB,Microsoft YaHei,Heiti SC,WenQuanYi Micro Hei,sans-serif;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100%;
  width: 100%;

  .main-content {
    display: flex;
    width: 960px;
    margin: 0 auto;
    min-height: 666px;
    padding-top: 25px;

    @media screen and (max-width: 960px) {
      width: 760px;
    }

    @media screen and (max-width: 760px) {
      flex-direction: column;
      height: auto;
      width: 100%;
      padding-top: 0;
    }
  }
}
.app-experiment {
  background-color: $expBg;
}
</style>

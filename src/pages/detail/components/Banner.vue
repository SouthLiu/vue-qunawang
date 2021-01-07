<template>
  <div>
    <div class="banner" @click="handleGalleryClick">
      <img class="banner-img" :src="this.bannerImg"/>
      <div class="banner-info">
        <div class="banner-title">
          {{sightName}}
        </div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe6e5;</span>
          {{this.bannerImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallery :imgs="bannerImgs" v-show="showGallery" @close="showGalleryClose"></common-gallery>
    </fade-animation>
  </div>
</template>

<script>
import Gallery from 'common/gallery/Gallery'
import Animation from 'common/animation/Animation'
export default {
  name: 'DetailBanner',
  data () {
    return {
      showGallery: false
    }
  },
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  methods: {
    handleGalleryClick () {
      this.showGallery = true
    },
    showGalleryClose () {
      this.showGallery = false
    }
  },
  components: {
    CommonGallery: Gallery,
    FadeAnimation: Animation
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      display: flex
      position: absolute
      left: 0
      right: 0
      bottom: 0
      line-height: .6rem
      color: #fff
      background: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8))
      .banner-title
        flex: 1
        font-size: .32rem
        padding: 0 .2rem
      .banner-number
        height: .32rem
        padding: 0 .4rem
        margin-top: .14rem
        line-height: .32rem
        border-radius: .2rem
        background: rgba(0, 0, 0 .8)
        font-size: .24rem
        .banner-icon
          font-size: .24rem
</style>

<template>
  <scroller class="scroller">
    <div class="mzui-demo">
        <title link="https://yanjiie.github.io/weex-flymeui/#/packages/fm-overlay/"></title>
        <category title="动画蒙版"></category>
        <fm-button class="btn" @buttonClicked="openOverlay" size="huge">有动画</fm-button>
        <category title="无动画蒙版"></category>
        <fm-button class="btn" @buttonClicked="openNoAniOverlay" size="huge">无动画</fm-button>
        <fm-overlay :show="show"
                    duration="300"
                    :hasAnimation="hasAnimation"
                    :timingFunction="timingFunction"
                    @fmOverlayBodyClicked="fmOverlayBodyClicked"
                    opacity="0.5">
                    <div class="test"></div>

                    </fm-overlay>
    </div>
  </scroller>
</template>

<style scoped>
.test {
  background-color: #198ded;
  width: 200px;
  height: 200px;
}
  .mzui-demo {
    align-items: center;
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: #ffffff;
  }
  .title {
    margin-top: 60px;
    margin-bottom: 30px;
    color: #aaaaaa;
  }
  .btn {
    margin: 30px;
  }
  .scroller {
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
  }
</style>

<script>
  import { FmButton, FmOverlay } from 'weex-flymeui'
  import Title from '@components/flyme/_mods/title.vue'
  import Category from '@components/flyme/_mods/category.vue'

  const modal = weex.requireModule('modal')

  export default {
    components: { Title, Category, FmButton, FmOverlay },

    data: () => ({
      show: false,
      hasAnimation: true,
      timingFunction: ['ease-in', 'ease-out']
    }),

    methods: {
      openOverlay () {
        this.hasAnimation = true
        this.show = true
      },
      openNoAniOverlay () {
        this.hasAnimation = false
        this.show = true
      },
      fmOverlayBodyClicked (e) {
        modal.toast({
          'message': '蒙版关闭回调',
          'duration': 1
        })
        this.show = false
      }
    }
  }
</script>

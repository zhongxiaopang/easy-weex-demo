<!-- CopyRight (C) 2017-2022 Alibaba Group Holding Limited. -->
<!-- Created by Tw93 on 16/10/26. -->

<template>
  <div class="wxc-demo">
    <wxc-result :type="type"
                padding-top="232"
                :custom-set="customSet"
                @wxcResultButtonClicked="resultButtonClick"
                :show="show"></wxc-result>
  </div>
</template>

<style scoped>
  .wxc-demo {
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: #ffffff;
  }
</style>

<script>
  import { WxcResult } from 'weex-ui'

  import { setTitle } from '@components/ui/_mods/set-nav'

  const modal = weex.requireModule('modal')

  export default {
    components: { WxcResult },
    data: () => ({
      show: true,
      type: 'noNetwork'
      // customSet:{
      //   errorPage: {
      //     button: '立即反馈',
      //     content: '亲，出错了',
      //     pic: 'https://gw.alicdn.com/tfs/TB1lgzNfBHH8KJjy0FbXXcqlpXa-320-320.png'
      //   }
      // }
    }),
    computed: {},
    created () {
      setTitle('Result')
    },
    methods: {
      resultButtonClick (e) {
        modal.toast({
          'message': `你点击了按钮`,
          'duration': 1
        })
      }
    }
  }
</script>

<template>
  <div class="zk-tab" :style="styles" component-path="core/zk-tab">
    <div class="">{{viewModel}}</div>
  </div>
</template>

<script>
  import { THEME_GETLINK_GET } from '@/service/api/apiUrl' 
  import { editSetting } from './property'
  export default {
    name: editSetting.key,
    props: ['widgetDataId'],
    data () {
      return {
        viewModel: '', // 数据模型
        styles: {} // 可视化编辑样式
      }
    },
    mounted () {
      this.init()
    },
    methods: {
      async  init () {
        this.viewModel = await this.$api.get(THEME_GETLINK_GET, this.widgetDataId)
      }
    }
  }
</script>

<style scoped lang="less">
  @import '~_style/index.less';
  .zk-tab {
  	font-size: @font-size-base;
  }
</style>


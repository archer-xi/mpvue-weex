<template>
  <div class="zk-foot" :style="styles">
    <div class="zkweb-footer">
      <div class="zkweb-tabbar">
        <a href="/pages/index" class="tabbar__item">
          <span style="display: inline-block; position: relative; height:20px">
            <x-icon src="zk-home" x-class="brand" size="20"></x-icon>
          </span>
          <p class="tabbar__label">
            首页
          </p>
        </a>
        <a href="/pages/product/class" class="tabbar__item">
          <span style="display: inline-block; position: relative; height:20px">
            <x-icon src="zk-classification" size="20"></x-icon>
          </span>
          <p class="tabbar__label">
            分类
          </p>
        </a>
        <a href="" class="tabbar__item">
          <span style="display: inline-block; position: relative; height:20px">
            <x-icon src="zk-cart" x-class="brand" size="20"></x-icon>
          </span>
          <p class="tabbar__label">
            购物车
          </p>
        </a>
        <a href="" class="tabbar__item">
          <span style="display: inline-block; position: relative; height:20px">
            <x-icon src="zk-me" x-class="brand" size="20"></x-icon>
          </span>
          <p class="tabbar__label">
            我的
          </p>
        </a>
      </div>
      <div class="footer-placeholder " :style="'height:46px'"></div>
    </div>
  </div>
</template>

<script>
  import { THEME_GETVALUE_GET } from '@/service/api/apiUrl'
  import { editSetting } from './property'
  export default {
    name: editSetting.key,
    data () {
      return {
        viewModel: '', // 数据模型
        styles: {} // 可视化编辑样式
      }
    },
    props: ['dataId'],
    mounted () {
      this.init()
    },
    methods: {
      async  init () {
        const para = {
          dataId: this.dataId,
          defaultId: '5b406cddfef00000a0000002'
        }
        this.viewModel = await this.$api.get(THEME_GETVALUE_GET, para)
        console.info('组件数据', this.viewModel)
      }
    }
  }
</script>

<style scoped lang="less">
  @import '~_style/index.less';
  .zkweb-footer {
  	font-size: 123px;
  	.zkweb-tabbar {
  		position: fixed;
  		bottom: 0;
  		left: 0;
  		z-index: 500;
  		width: 100%;
  		height: 46px;
  		background-color: #f7f7fa;
  		display: flex;
  		.tabbar__item {
  			display: block;
  			flex: 1;
  			padding: 5px 0 0;
  			font-size: 0;
  			color: #999999;
  			text-align: center;
  			-webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  			.tabbar__icon {
  				display: inline-block;
  				width: 27px;
  				height: 27px;
  			}
  			.tabbar__label {
  				text-align: center;
  				color: #999999;
  				font-size: 14px;
  				line-height: 1.8;
  			}
  		}
  	}
  	.zkweb-tabbar:before {
  		content: ' ';
  		position: absolute;
  		left: 0;
  		top: 0;
  		right: 0;
  		height: 1px;
  		border-top: 1px solid #c0bfc4;
  		color: #c0bfc4;
  		transform-origin: 0 0;
  		transform: scaleY(0.5);
  	}
  }
</style>


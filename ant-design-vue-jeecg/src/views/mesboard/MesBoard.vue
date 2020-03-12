<template>
  <div class="mes-board">
    <div>
      <a-button style="float: right" type="link" @click="screen"><span class="icon mesicon icon_exit"></span>{{isFullscreen?'退出':'全屏'}}</a-button>
      <span class="icon mesicon logo_wanlida" style="color: #b6392e"></span>
    </div>
    <a-tabs>
      <a-tab-pane tab="产品综合看板" key="1">
        <product-board>

        </product-board>
      </a-tab-pane>
      <a-tab-pane tab="制造综合看板" key="2">
        <fabricate-board>

        </fabricate-board>
      </a-tab-pane>
      <div slot="tabBarExtraContent">
        <div class="slot-item">
          <span class="icon mesicon index_icon_jihexunjian"></span>2020/03/12 16:42
        </div>
        <div class="slot-item">
          <span class="icon mesicon icon_xianbie"></span>车间/线别:
          <a-select size="small" defaultValue="lucy" style="width: 120px">
            <a-select-option value="jack">Jack</a-select-option>
            <a-select-option value="lucy">Lucy</a-select-option>
            <a-select-option value="disabled" disabled>Disabled</a-select-option>
            <a-select-option value="Yiminghe">yiminghe</a-select-option>
          </a-select>
          &nbsp;负责人:唐老鸭
        </div>
        <div class="slot-item">
          <a-button size="small" type="link" @click="screen"><span class="icon mesicon icon_lunbo_on"></span>轮播打开</a-button>
        </div>
      </div>
    </a-tabs>
  </div>
</template>

<script>
  import ACol from "ant-design-vue/es/grid/Col"
  import screenFull from 'screenfull'
  import ProductBoard from './ProductBoard'
  import FabricateBoard from './FabricateBoard'
  export default {
    name: "MesBoard",
    components: {
      ACol,
      ProductBoard,
      FabricateBoard
    },
    data() {
      return{
        //默认不全屏
        isFullscreen: false
      }
    },
    methods:{
      screen(){
        // 如果不允许进入全屏，发出不允许提示
        if (!screenFull.isEnabled) {
          return false
        }
        screenFull.toggle()
        this.isFullscreen = !this.isFullscreen
      }
    }
  }
</script>

<style lang="scss">
  .mes-board .ant-tabs{
    width: 100%;
  }
  .mes-board .ant-tabs-nav-container {
    font-size: 16px !important;
  }
  .mes-board .ant-tabs-extra-content {
    width: 50%;
    line-height: 24px;
    padding-top: 12px;
  }
</style>
<style lang="scss" scoped>
  .slot-item {
    float: right;
    padding: 0 20px;
    border-right: 1px solid #545456;;
  }
  .slot-item:first-child{
    border: none;
  }
</style>
<template>
  <div class="mes-board">
    <div>
      <a-button style="float: right" type="link" @click="screen"><span class="icon mesicon icon_exit"></span>{{fullscreen?'退出':'全屏'}}</a-button>
      <span class="icon mesicon logo_wanlida" style="color: #b6392e"></span>
    </div>
    <a-tabs v-model="activeKey" @tabClick="clickTab">
      <a-tab-pane tab="产品综合看板" key="1">
        <product-board :lineID = 'lineID'>

        </product-board>
      </a-tab-pane>
      <a-tab-pane tab="制造综合看板" key="2">
        <fabricate-board :lineID = 'lineID'>

        </fabricate-board>
      </a-tab-pane>
      <div slot="tabBarExtraContent">
        <div class="slot-item">
          <span class="icon mesicon index_icon_jihexunjian"></span>{{timeStr}}
        </div>
        <div class="slot-item">
          <span class="icon mesicon icon_xianbie"></span>车间/线别:
          <a-select v-model="lineID" size="small" style="width: 120px;color: #1890FF;font-weight: bold;" :getPopupContainer="popupContainer">
            <a-select-option value="jack">Jack</a-select-option>
            <a-select-option value="lucy">Lucy</a-select-option>
            <a-select-option value="disabled" disabled>Disabled</a-select-option>
            <a-select-option value="Yiminghe">yiminghe</a-select-option>
          </a-select>
          &nbsp;负责人:唐老鸭
        </div>
        <div class="slot-item">
          <a-button size="small" type="link" @click="openCarousel" v-if="!carousel"><span class="icon mesicon icon_lunbo_on"></span>轮播打开</a-button>
          <a-button size="small" type="link" @click="closeCarousel" v-if="carousel"><span class="icon mesicon icon_lunbo_off"></span>轮播关闭</a-button>
        </div>
      </div>
    </a-tabs>
  </div>
</template>

<script>
  import ACol from "ant-design-vue/es/grid/Col"
  import ProductBoard from './ProductBoard'
  import FabricateBoard from './FabricateBoard'
  import {formatDate} from "@/utils/util"
  export default {
    name: "MesBoard",
    components: {
      ACol,
      ProductBoard,
      FabricateBoard
    },
    data() {
      var self = this;
      window.addEventListener("resize", function() {
        var isFull = document.isFullScreen || document.mozIsFullScreen || document.webkitIsFullScreen;
        if (isFull === undefined) {
          isFull = false
        }
        if(isFull){
          self.fullscreen=true
        }else{
          self.fullscreen=false
        }
        return isFull
      });
      return{
        activeKey:'1',
        timer: null,
        //默认不全屏
        fullscreen: false,
        //默认不轮播
        carousel:false,
        lineID: 'lucy',
        timeSeconds:new Date(),
        timeStr:''
      }
    },
    created(){
      var seconds = this.timeSeconds.getSeconds()
      this.timeSeconds = this.timeSeconds.getTime()
      this.timeStr = formatDate(this.timeSeconds,'yyyy/MM/dd hh:mm')
      var self = this
      setTimeout(() => {
        self.timeSeconds += (60-seconds)*1000
        self.timeStr = formatDate(self.timeSeconds,'yyyy/MM/dd hh:mm')
        setInterval(() => {
          self.timeSeconds += 60000
          self.timeStr = formatDate(self.timeSeconds,'yyyy/MM/dd hh:mm')
        },60000)
      },(60-seconds)*1000)
    },
    methods:{
      //打开轮播
      openCarousel(){
        this.carousel = true
        var self = this
        this.timer = setInterval(() => {
          self.activeKey = parseInt(self.activeKey) == 2 ? '1' : String(parseInt(self.activeKey)+1)
        },3000)
      },
      //关闭轮播
      closeCarousel(){
        this.carousel = false
        clearInterval(this.timer)
      },
      //点击tab轮播重新计时
      clickTab(){
        if(this.carousel){
          this.closeCarousel();
          this.openCarousel();
        }
      },
      //处理全屏a-select下拉选项无法显示问题
      popupContainer(){
        return document.getElementsByClassName("mes-board")[0]
      },
      screen(){
        //放大的元素，如果整个系统放大，直接赋值 document.documentElement
        let element = document.getElementsByClassName("mes-board")[0];
        if (this.fullscreen) {
          if (document.exitFullscreen) {
            document.exitFullscreen()
          } else if (document.webkitCancelFullScreen) {
            document.webkitCancelFullScreen()
          } else if (document.mozCancelFullScreen) {
            document.mozCancelFullScreen()
          } else if (document.msExitFullscreen) {
            document.msExitFullscreen()
          }
        } else {
          if (element.requestFullscreen) {
            element.requestFullscreen()
          } else if (element.webkitRequestFullScreen) {
            element.webkitRequestFullScreen()
          } else if (element.mozRequestFullScreen) {
            element.mozRequestFullScreen()
          } else if (element.msRequestFullscreen) {
            element.msRequestFullscreen()
          }
        }
        if(!this.fullscreen){
          element.setAttribute('style','overflow-y:auto')
        }else{
          element.removeAttribute('style')
        }
        this.fullscreen = !this.fullscreen
      },
    }
  }
</script>

<style lang="scss">
  .mes-board{
    background: #121212;
    margin: -12px -12px 0;
    padding: 12px;
  }
  .mes-board .ant-tabs{
    width: 100%;
    color: #ccc;
  }
  .mes-board .ant-btn-link {
    color: #ccc;
  }
  .mes-board .ant-btn-link:hover {
    color: #fff;
  }
  .mes-board .ant-tabs-tab-prev.ant-tabs-tab-arrow-show, .mes-board .ant-tabs-tab-next.ant-tabs-tab-arrow-show {
    color: #ccc;
  }
  .mes-board .ant-tabs-bar {
    border-bottom: 1px solid #ccc;
  }
  .mes-board .ant-tabs-ink-bar {
    background-color: #fff;
  }
  .mes-board .ant-tabs-nav-container {
    font-size: 17px;
  }
  .mes-board .ant-tabs-extra-content {
    width: 60%;
    line-height: 24px;
    padding-top: 12px;
  }
  .mes-board .ant-table-thead > tr > th {
    background: #2c2c2c;
    color: #fff;
    font-size: 16px;
  }
  .mes-board .ant-table-tbody > tr > td {
    background: #2c2c2c;
    color: #ccc;
  }
  .mes-board .ant-table-tbody > tr:hover td{
    color: #000;
    background: #fff;
  }
  .mes-board .ant-tabs-nav .ant-tabs-tab-active {
    color: #fff;
  }
  .mes-board .ant-tabs-nav .ant-tabs-tab:hover {
    color: #fff;
  }
</style>
<style lang="scss" scoped>
  .slot-item {
    float: right;
    padding: 0 12px;
    border-right: 1px solid #545456;;
  }
  .slot-item:first-child{
    border: none;
  }
</style>
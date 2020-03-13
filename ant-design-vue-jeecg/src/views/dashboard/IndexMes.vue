<template>
  <div class="page-header-index-wide">
    <a-row :gutter="24">
      <a-col :sm="24" :md="12" :xl="8" :style="{ marginBottom: '24px' }">
        <div class="col-item top-item">
          <a-list :dataSource="data">
            <a-list-item slot="renderItem" slot-scope="item, index">
              <a-list-item-meta
                :description="item.message"
              >
                <span slot="title">{{item.title}}</span>
                <span
                  style="font-size: 80px;color: #1e88e5"
                  slot="avatar"
                  class="icon mesicon index_kanban_"
                ></span>
              </a-list-item-meta>
            </a-list-item>
          </a-list>
        </div>
      </a-col>
      <a-col :sm="24" :md="12" :xl="8" :style="{ marginBottom: '24px' }">
        <div class="col-item top-item">
          <a-list itemLayout="horizontal" :dataSource="data">
            <a-list-item slot="renderItem" slot-scope="item, index">
              <a-list-item-meta
                :description="item.message"
              >
                <span slot="title">{{item.title}}</span>
                <span
                  style="font-size: 80px;color: #7460ee"
                  slot="avatar"
                  class="icon mesicon index_icon_tongji_"
                ></span>
              </a-list-item-meta>
            </a-list-item>
          </a-list>
        </div>
      </a-col>
      <a-col :sm="24" :md="12" :xl="8" :style="{ marginBottom: '24px' }">
        <div class="col-item top-item">
          <a-list itemLayout="horizontal" :dataSource="data">
            <a-list-item slot="renderItem" slot-scope="item, index">
              <a-list-item-meta
                :description="item.message"
              >
                <span slot="title">{{item.title}}</span>
                <span
                  style="font-size: 80px;color: #26c7da"
                  slot="avatar"
                  class="icon mesicon index_icon_jihexunjian_"
                ></span>
              </a-list-item-meta>
            </a-list-item>
          </a-list>
        </div>
      </a-col>
    </a-row>

    <a-row :gutter="24">
      <a-col :sm="24" :md="16" :xl="16" :style="{ marginBottom: '24px' }">
        <div class="col-item">
          <a-list bordered :dataSource="messageData">
            <a-list-item slot="renderItem" slot-scope="item, index">
              <a-list-item-meta :description="item.message">

              </a-list-item-meta>
              <div><span style="margin-right: 4px;color: #979797" class="icon mesicon icon_time"></span>{{item.createTime}}</div>
            </a-list-item>
            <div slot="header" class="message-header">最近一周消息</div>
          </a-list>
        </div>
      </a-col>
      <a-col :sm="24" :md="8" :xl="8" :style="{ marginBottom: '24px' }">
        <div class="col-item message-setting">
          <a-list bordered :dataSource="messageSetting">
            <a-list-item slot="renderItem" slot-scope="item, index">
              <a-list-item-meta description="以站内形式通知">
                <span slot="title">{{item.typeName}}</span>
              </a-list-item-meta>
              <div>
                <a-switch :defaultChecked="item.checked" @change="settingChange(item.type,item.checked)" />
              </div>
            </a-list-item>
            <div slot="header" class="message-header">消息通知设置</div>
          </a-list>
        </div>
      </a-col>
    </a-row>
  </div>
</template>

<script>
  import ACol from "ant-design-vue/es/grid/Col"

  export default {
    name: "IndexMes",
    components: {
      ACol,
    },
    data() {
      return {
        data: [
          {
            id: 1,
            title: 'Racing car sprays burning fuel into crowd.',
            message: '3月11日 14:42'
          },
        ],
        messageData: [
          {
            id: 1,
            message: 'Racing car sprays burning fuel into crowd.',
            createTime: '3月11日 14:42'
          },
          {
            id: 1,
            message: 'Racing car sprays burning fuel into crowd.',
            createTime: '3月11日 14:42'
          },
          {
            id: 1,
            message: 'Racing car sprays burning fuel into crowd.',
            createTime: '3月11日 14:42'
          },
          {
            id: 1,
            message: 'Racing car sprays burning fuel into crowd.Racing car sprays burning fuel into crowd.Racing car sprays burning fuel into crowd.',
            createTime: '3月11日 14:42'
          },
        ],
        messageSetting: [
            {
              type: 1,
              typeName: '看板预警',
              checked:true
            },
            {
              type: 2,
              typeName: '稽核预警',
              checked:true
            },
            {
              type: 3,
              typeName: '系统通知',
              checked:false
            },
        ]
      }
    },
    created() {

    },
    methods: {
      settingChange(type,checked){
          this.$message.success(type)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .page-header-index-wide{
    text-align: center;
    [class^='ant-col-'] {
      background: transparent;
    }
  }
  .top-item {
    height: 135px;
    padding: 15px 10px;
  }
  .top-item h4{
    font-size: 18px;
    line-height: 40px;
  }
  .ant-list-item-meta-avatar {
    line-height: 80px;
  }
  .col-item {
    background: #fff;
    margin: 0;
  }
  .message-header{
    font-size: 18px;
    text-align: left;
    color: #333;
  }
  .ant-list{
    border: none !important;
  }
  .ant-list-item-meta-description {
    font-size: 16px;
    text-align: left;
  }
  .ant-list-item-content {
    flex: 1;
  }.ant-list-item-meta {
    flex: 4;
  }
  .ant-list-item-meta-title {
    text-align: left;
  }
  .message-setting .ant-list-item-meta-description{
    font-size: 14px;
  }
</style>
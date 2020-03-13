<template>
  <a-row :gutter="24">
    <a-col :sm="24" :md="8" :xl="8">
      <a-row type="flex" justify="space-between" :gutter="16">
        <a-col class="gutter-row" :span="12">
          <div class="gutter-box">
            <div>机型总数:</div>
            <div>8324</div>
          </div>
        </a-col>
        <a-col class="gutter-row" :span="12">
          <div class="gutter-box">
            <div>客户数:</div>
            <div>98</div>
          </div>
        </a-col>
        <a-col class="gutter-row" :span="12">
          <div class="gutter-box">
            <div>订单总数:</div>
            <div>9999</div>
          </div>
        </a-col>
        <a-col class="gutter-row" :span="12">
          <div class="gutter-box">
            <div>已出货:</div>
            <div>1682</div>
          </div>
        </a-col>
      </a-row>

      <div>
        <a-table :columns="columns0" :dataSource="data0" :pagination="false">
        </a-table>
      </div>
    </a-col>
    <a-col :sm="24" :md="16" :xl="16">
      <a-table :columns="columns" :dataSource="data" :pagination="false">
      </a-table>
    </a-col>
  </a-row>
</template>

<script>
  const columns0 = [
    {
      title: '前五大不良',
      dataIndex: 'name',
    },{
      title: '不良数',
      dataIndex: 'badNum',
    },{
      title: '不良原因',
      dataIndex: 'reason',
    }
  ];
  const columns = [
    {
      title: '机型',
      dataIndex: 'machine',
    },{
      title: '客户',
      dataIndex: 'customer',
    },{
      title: '订单数',
      dataIndex: 'orderNum',
    },{
      title: '投入数',
      dataIndex: 'input',
    },{
      title: '产出数',
      dataIndex: 'output',
    },{
      title: '达成率',
      dataIndex: 'radio',
    },{
      title: '不良数',
      dataIndex: 'bls',
    }
  ];
  const data0 = [
    {
      key: '1',
      name: '不开机',
      badNum: '100',
      reason: '设计不良',
    },{
      key: '2',
      name: '不开机',
      badNum: '100',
      reason: '设计不良',
    },{
      key: '3',
      name: '不开机',
      badNum: '100',
      reason: '设计不良',
    },{
      key: '4',
      name: '不开机',
      badNum: '100',
      reason: '设计不良',
    },{
      key: '5',
      name: '不开机',
      badNum: '100',
      reason: '设计不良',
    },
  ];
  const data = [
    {
      key: '1',
      machine: 'SMB-09',
      customer: 'DYSON',
      orderNum: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
    },{
      key: '2',
      machine: 'SMB-09',
      customer: 'DYSON',
      orderNum: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
    },{
      key: '3',
      machine: 'SMB-09',
      customer: 'DYSON',
      orderNum: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
    },{
      key: '4',
      machine: 'SMB-09',
      customer: 'DYSON',
      orderNum: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
    },
  ];
  export default {
    name: "ProductBoard",
    props: {
      lineID: {
        default: ''
      },
    },
    data() {
      return{
        columns0: columns0,
        data0: data0,
        columns: columns,
        data: data,
      }
    },
    created(){
      console.log(this.lineID+'====>init')
    },
    watch: {
      lineID(){
        console.log(this.lineID+'====>change')
      }
    }
  }
</script>

<style lang="scss" scoped>
  .ant-table-wrapper, .gutter-box {
    border-radius: 4px;
    background: #2c2c2c;
    color: #fff;
  }
  .gutter-box{
    margin-bottom: 16px;
    padding: 20px;
    font-size: 16px;
  }
  .gutter-box>div:last-child{
    text-align: center;
    line-height: 48px;
    margin-top: 10px;
    font-size: 18px;
    color: #68bbfe;
  }
</style>
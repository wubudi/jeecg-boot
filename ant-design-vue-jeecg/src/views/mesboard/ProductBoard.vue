<template>
  <a-row :gutter="24">
    <a-col :sm="24" :md="8" :xl="8">
      <div class="product-general">
        <div>
          <div>计划产量</div>
          <div>5000</div>
        </div>
        <div>
          <div>当前产量</div>
          <div>4500</div>
        </div>
        <div>
          <div>达成率</div>
          <div>95%</div>
        </div>
      </div>
      <div class="product-general product-last">
        <div>
          <div>机型</div>
          <div>5000</div>
        </div>
        <div>
          <div>投入数</div>
          <div>5000</div>
        </div>
        <div>
          <div>产出数</div>
          <div>95%</div>
        </div>
        <div>
          <div>直通率</div>
          <div>95%</div>
        </div>
      </div>
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
      title: '时段',
      dataIndex: 'time',
    },{
      title: '计划数',
      dataIndex: 'planNum',
    },{
      title: '投入',
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
    },{
      title: '直通率',
      dataIndex: 'ztl',
    },
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
      time: '08-09',
      planNUm: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
      ztl: '96.67%'
    },{
      key: '2',
      time: '08-09',
      planNUm: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
      ztl: '96.67%'
    },{
      key: '3',
      time: '08-09',
      planNUm: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
      ztl: '96.67%'
    },{
      key: '4',
      time: '08-09',
      planNUm: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
      ztl: '96.67%'
    },{
      key: '5',
      time: '08-09',
      planNUm: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
      ztl: '96.67%'
    },{
      key: '6',
      time: '08-09',
      planNUm: '3000',
      input: '3000',
      output: '2900',
      radio: '96.67%',
      bls: '1000',
      ztl: '96.67%'
    },
  ];
  export default {
    name: "ProductBoard",
    data() {
      return{
        columns0: columns0,
        data0: data0,
        columns: columns,
        data: data,
      }
    }
  }
</script>

<style scoped>
  .ant-table-wrapper,.product-general {
    border-radius: 4px;
    background: #fff;
  }
  .product-general {
    padding: 20px 30px;
    margin-bottom: 24px;
    text-align: center;
  }
  .product-general>div{
    display: inline-block;
    width: 33.33333333%;
    border-right: 1px solid #a7a7a7;
  }
  .product-general>div>div:first-child{
    font-size: 16px;
    line-height: 32px;
  }
  .product-general>div>div:last-child{
    font-size: 16px;
    line-height: 32px;
  }
  .product-general>div:last-child{
    border-right: none;
  }
  .product-last>div{
    display: inline-block;
    width: 25%;
  }
</style>
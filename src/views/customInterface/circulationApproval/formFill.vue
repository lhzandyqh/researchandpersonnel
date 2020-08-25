<template>
  <div class="app-container">
<!--    <el-table :data="tableData3" style="width: 100%">-->
<!--      <el-table-column width="120" prop="date"></el-table-column>-->
<!--      <el-table-column prop="name"  width="120">-->
<!--        <template slot-scope="scope">-->
<!--           <el-input type="text"></el-input>-->
<!--        </template>-->
<!--        <el-input type="text"></el-input>-->
<!--      </el-table-column>-->
<!--      <el-table-column label="地址">-->
<!--        <el-table-column prop="province" label="省份" width="120"></el-table-column>-->
<!--      </el-table-column>-->
<!--    </el-table>-->
<table border="1" cellspacing="0">
  <tr>
    <td colspan="2">附件上传/下载  在线浏览                      审批打印</td>
    <td> 操作选项</td>
  </tr>
  <tr>
    <th>审批内容</th>
    <td rowspan="2">

      <el-input/></td>
    <td rowspan="2"><el-button type="text">保存</el-button>
      <el-button type="text">提交</el-button></td>
  </tr>
  <tr>
    <th>审批流转</th>
  </tr>
  <tr>
    <th>部门意见</th>
    <td><el-input></el-input></td>
    <td><el-button type="text">提交</el-button>
      <el-button type="text">撤回</el-button></td>
  </tr>
  <tr>
    <th>部门意见</th>
    <td><el-input/></td>
    <td><el-button type="text">提交</el-button>
      <el-button type="text">撤回</el-button></td>
  </tr>
  <tr>
    <th>部门意见</th>
    <td><el-input/></td>
    <td><el-button type="text">提交</el-button>
      <el-button type="text">撤回</el-button>
    </td>
  </tr>
  <tr>
    <th>备注</th>
    <td><el-input/></td>
    <td></td>
  </tr>

</table>
    <table>
      <tr>
        <th>姓名</th>
        <th>年龄</th>
        <th>性别</th>
      </tr>
      <tr>
        <td class="first"></td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td></td>
        <td></td>
        <td></td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'FormFill',
  filters: {},
  data() {
    return {
      tableData3: [{
        date: '2016-05-03',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-04',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-01',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-08',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-06',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-07',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }]
    }
  },
  created() {},
  methods: {}
}
</script>

<style lang="scss">
  .el-table thead.is-group th {
    background: #fff;
  }

  .el-table thead.is-group tr:first-of-type th:first-of-type:before {
    content: '审批流转';
    text-align: center;
    position: absolute;
    width: 152px;
    height: 1px;
    bottom: 30px;
    right: 0;
  }

  .el-table thead.is-group tr:first-of-type th:first-of-type:after {
    content: '审批内容';
    text-align: center;
    position: absolute;
    width: 152px;
    top: 10px;
    left: 0;
  }

  .el-table thead.is-group tr:first-of-type th:first-of-type .cell {
    position: absolute;
    top: 0;
    left: 0;
    width: 152px;
    height: 1px;
    background-color: #EBEEF5;
    display: block;
    text-align: center;
    transform: rotate(36deg);
    transform-origin: top left;
    -ms-transform: rotate(36deg);
    -ms-transform-origin: top left;
    -webkit-transform: rotate(36deg);
    -webkit-transform-origin: top left;
  }
  table{
    border-collapse:collapse;
  }
  table,tr,td{
    border:1px solid black;
  }
  td{
    width:100px;/*这里需要自己调整，根据自己的需求调整宽度*/
    height:50px;/*这里需要自己调整，根据自己的需求调整高度*/
    position: relative;
  }
  td[class=first]:before{
    content: "";
    position: absolute;
    width: 1px;
    height:114px;/*这里需要自己调整，根据td的宽度和高度*/
    top:0;
    left:0;
    background-color: black;
    display: block;
    transform: rotate(-63deg);/*这里需要自己调整，根据线的位置*/
    transform-origin: top;
  }

</style>

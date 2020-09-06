<template>
  <div class="app-container">
    <el-table :data="scientificData" border fit highlight-current-row style="width: 70%">
      <el-table-column prop="number" align="center" label="审核编号" >
      </el-table-column>
      <el-table-column prop="sub" width="160" align="center" label="科研信息修改类型">
      </el-table-column>
      <el-table-column prop="applypeople" width="140" align="center" label="申请人">
      </el-table-column>
      <el-table-column prop="approvalpeople" width="140" align="center" label="审核人">
      </el-table-column>
      <el-table-column prop="subdate" width="160" align="center" label="提交时间">
      </el-table-column>
      <el-table-column prop="approvaldate" width="160" align="center" label="审核时间">
      </el-table-column>
      <el-table-column width="190" align="center" label="审核状态">
        <template slot-scope="scope">
          <el-tag  v-if="scope.row.approval==='通过'" type="success">审核通过</el-tag>
          <el-tag  v-if="scope.row.approval==='未通过'" type="danger">审核未通过</el-tag>
          <el-tag  v-if="scope.row.approval==='待通过'">审核待通过</el-tag>
        </template>
      </el-table-column>
    </el-table>
    <div class="fenye">
      <el-pagination
        :current-page="1"
        :page-sizes="[10, 20, 30]"
        :page-size="10"
        :total="10"
        style="margin-top:20px;"
        layout="total, sizes, prev, pager, next, jumper"
      />
    </div>
  </div>
</template>

<script>
  export default {
    name: 'scientificHistory',
    data(){
      return{
        zhuanyeVisible:false,
        workVisible:false,
        jibenVisible:false,
        scientificData:[
          {
            number:'1',
            sub:'非核心论文',
            applypeople:'刘老师',
            approvalpeople:'刘老师',
            subdate:'2019-9-2',
            approvaldate:'2020-1-2',
            approval:'通过',
          },
          {
            number:'2',
            sub:'三大检索论文',
            applypeople:'王老师',
            approvalpeople:'刘老师',
            subdate:'2017-9-2',
            approvaldate:'2018-1-2',
            approval:'未通过',
          },
          {
            number:'3',
            sub:'专著登记',
            applypeople:'赵老师',
            approvalpeople:'刘老师',
            subdate:'2019-4-2',
            approvaldate:'2019-5-2',
            approval:'通过',
          },
          {
            number:'3',
            sub:'专利申报',
            applypeople:'张老师',
            approvalpeople:'刘老师',
            subdate:'2019-4-2',
            approvaldate:'2019-5-2',
            approval:'未通过',
          },
        ]
      }
    }
  }
</script>

<style scoped>

</style>

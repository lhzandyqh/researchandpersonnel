<template>
  <div class="app-container">
    <el-table :data="projectData" border fit highlight-current-row style="width: 70%">
      <el-table-column prop="number" align="center" label="审核编号" width="80">
      </el-table-column>
      <el-table-column prop="sub" width="180" align="center" label="项目课题名称">
      </el-table-column>
      <el-table-column prop="applypeople" width="130" align="center" label="申请人">
      </el-table-column>
      <el-table-column prop="approvalpeople" width="130" align="center" label="审核人">
      </el-table-column>
      <el-table-column prop="subdate" width="150" align="center" label="提交时间">
      </el-table-column>
      <el-table-column prop="approvaldate" width="150" align="center" label="审核时间">
      </el-table-column>
      <el-table-column width="180" align="center" label="审核状态">
        <template slot-scope="scope">
          <el-tag  v-if="scope.row.approval==='通过'" type="success">审核通过</el-tag>
          <el-tag  v-if="scope.row.approval==='未通过'" type="danger">审核未通过</el-tag>
          <el-tag  v-if="scope.row.approval==='待通过'">审核待通过</el-tag>
        </template>
      </el-table-column>
      <el-table-column align="center" label="操作">
        <template slot-scope="scope">
          <el-button type="primary" size="small" icon="el-icon-zoom-in" @click="opendetail">查看</el-button>
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
    <el-dialog :visible.sync="projectVisible" title="审核详情">
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">论文名称：</span>
            </div>
            <div class="content">
              <span>大数据研究</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">是否第一作者：</span>
            </div>
            <div class="content">
              <span>是</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">发表刊物：</span>
            </div>
            <div class="content">
              <span></span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">出版社：</span>
            </div>
            <div class="content">
              <span></span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">发表时间：</span>
            </div>
            <div class="content">
              <span>2019.4.3</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">任现职以来担任学校工作：</span>
            </div>
            <div class="content">
              <span>科研</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">担任工作起始时间：</span>
            </div>
            <div class="content">
              <span>2003.3.3</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">担任工作结束时间：</span>
            </div>
            <div class="content">
              <span>2003.3.4</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-divider/>
      <div>
        <el-row style="padding-top: 10px">
          <span style="font-weight: bolder">审核原因</span>
        </el-row>
        <el-row style="padding-top: 10px">
          <el-input
            :rows="4"
            v-model="AuditingReason"
            :disabled="false"
            type="textarea"
            placeholder="请输入内容(审核通过无需输入)"/>
        </el-row>
      </div>
      <div class="foot">
        <span slot="footer" class="dialog-footer">
          <el-button type="success" size="small" plain>审核通过</el-button>
          <el-button type="danger" size="small" plain>审核未通过</el-button>
          <el-button type="primary" @click="zhuanyeVisible = false">关闭</el-button>
        </span>
      </div>
    </el-dialog>
  </div>
</template>

<script>
  export default {
    name: 'projectApproval',
    data(){
      return{
        projectVisible:false,
        workVisible:false,
        jibenVisible:false,
        projectData:[
          {
            number:'1',
            sub:'大数据产业',
            applypeople:'王老师',
            approvalpeople:'刘老师',
            subdate:'2019-9-2',
            approvaldate:'2020-1-2',
            approval:'待通过',
          },
          {
            number:'2',
            sub:'自然语言处理问答系统',
            applypeople:'张老师',
            approvalpeople:'刘老师',
            subdate:'2017-9-2',
            approvaldate:'2018-1-2',
            approval:'待通过',
          },
          {
            number:'3',
            sub:'教师评教评学系统',
            applypeople:'刘老师',
            approvalpeople:'刘老师',
            subdate:'2019-4-2',
            approvaldate:'2019-5-2',
            approval:'待通过',
          },
          {
            number:'3',
            sub:'专业智能知识库建设',
            applypeople:'刘老师',
            approvalpeople:'刘老师',
            subdate:'2019-4-2',
            approvaldate:'2019-5-2',
            approval:'待通过',
          },
        ]
      }
    },
    methods:{
      opendetail(){
        this.projectVisible = true;
      }
    }
  }
</script>

<style scoped>

</style>

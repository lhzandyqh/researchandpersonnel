<template>
  <div class="app-container">
    <el-table :data="projectData" style="width: 100%" stripe>
      <el-table-column prop="subdate" label="提交日期">
      </el-table-column>
      <el-table-column prop="applypeople" label="提交人">
      </el-table-column>
      <el-table-column prop="department" label="部门">
      </el-table-column>
      <el-table-column prop="number" label="审核类型">
      </el-table-column>
      <el-table-column prop="sub" label="审核名称">
      </el-table-column>
      <el-table-column label="审核状态">
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
    <div style="text-align: center">
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
              <span style="font-weight: bolder">项目名称：</span>
              <span>大数据产业</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">项目人数：</span>
              <span>3</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">项目级别：</span>
              <span>国家级</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">主管部门：</span>
              <span>计算机学院</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">项目负责人：</span>
              <span>王老师 </span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">项目预算：</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">项目方案：</span>
              <el-button type="text" >查看附件</el-button>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-divider/>
      <h4>部门意见</h4>
      <div>
        <el-row>
          <el-col :span="6">
            准予通过
          </el-col>
          <el-col :span="6">
            <span>审核时间：</span>
            <span>2019-12-04</span>
          </el-col>
          <el-col :span="6">
            <span>审核人：</span>
            <span>刘明至</span>
          </el-col>
          <el-col :span="5">
            <span>审核状态</span>
            <el-tag type="success" size="small">通过</el-tag>
          </el-col>
        </el-row>
      </div>
      <el-divider />
      <h4>系部意见</h4>
      <div>
        <el-row>
          <el-col :span="6">
            项目进度有待加强
          </el-col>
          <el-col :span="6">
            <span>审核时间：</span>
            <span>2019-12-04</span>
          </el-col>
          <el-col :span="6">
            <span>审核人：</span>
            <span>郭志</span>
          </el-col>
          <el-col :span="5">
            <span>审核状态</span>
            <el-tag type="success" size="small">通过</el-tag>
          </el-col>
        </el-row>
      </div>
      <el-divider />
      <div>
        <el-row style="padding-top: 10px">
          <span style="font-weight: bolder">科研处意见</span>
        </el-row>
        <el-row style="padding-top: 10px">
          <el-input
            :rows="4"
            v-model="AuditingReason"
            type="textarea"
            placeholder="请输入内容"/>
        </el-row>
      </div>
      <div class="foot">
        <span slot="footer" class="dialog-footer">
          <el-button type="success" size="small" plain @click="pass">审核通过</el-button>
          <el-button type="danger" size="small" plain @click="pass">审核未通过</el-button>
          <el-button type="primary" @click="zhuanyeVisible = false" size="small" plain>关闭</el-button>
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
        AuditingReason:'',
        projectVisible:false,
        workVisible:false,
        jibenVisible:false,
        projectData:[
          {
            number:'项目开题',
            sub:'大数据产业',
            applypeople:'王老师',
            approvalpeople:'刘老师',
            subdate:'2019-9-2',
            department:'计算机学院',
            approvaldate:'2020-1-2',
            approval:'待通过',
          },
          {
            number:'项目中期',
            sub:'自然语言处理问答',
            applypeople:'张老师',
            approvalpeople:'刘老师',
            subdate:'2017-9-2',
            department:'计算机学院',
            approvaldate:'2018-1-2',
            approval:'待通过',
          },
          {
            number:'项目结题',
            sub:'教师评教评学系统',
            applypeople:'刘老师',
            approvalpeople:'刘老师',
            subdate:'2019-4-2',
            department:'理学院',
            approvaldate:'2019-5-2',
            approval:'待通过',
          },
          {
            number:'项目中期',
            sub:'专业智能知识库建设',
            applypeople:'刘老师',
            approvalpeople:'刘老师',
            subdate:'2019-4-2',
            department:'工学院',
            approvaldate:'2019-5-2',
            approval:'待通过',
          },
        ]
      }
    },
    methods:{
      opendetail(){
        this.projectVisible = true;
      },
      pass(){
        this.$message({
            type: 'success',
            message: '审核成功',
          }
        )
      }
    }
  }
</script>

<style scoped>

</style>

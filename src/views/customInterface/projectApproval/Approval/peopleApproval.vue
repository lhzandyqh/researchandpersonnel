<template>
  <div class="app-container">
    <el-table :data="peopleData" border fit highlight-current-row style="width: 70%">
      <el-table-column prop="number" align="center" label="审核编号" width="80">
      </el-table-column>
      <el-table-column prop="sub" width="150" align="center" label="个人信息修改类型">
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
          <el-button type="primary" size="small" icon="el-icon-zoom-in" @click="jibenview(scope.row.sub)">查看</el-button>
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
    <el-dialog :visible.sync="jibenVisible" title="审核详情">
      <el-row :gutter="20">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">姓&#8195;&#8195;名：</span>
            </div>
            <div class="content">
              <span>王老师</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">性&#8195;&#8195;别：</span>
            </div>
            <div class="content">
              <span>女</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">民&#8195;&#8195;族：</span>
            </div>
            <div class="content">
              <span>汉</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">出生年月：</span>
            </div>
            <div class="content">
              <span>1980-3-2</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">籍&#8195;&#8195;贯：</span>
            </div>
            <div class="content">
              <span>北京</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">职&#8195;&#8195;别：</span>
            </div>
            <div class="content">
              <span>讲师</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">身份证号：</span>
            </div>
            <div class="content">
              <span>234445198xxxxxxxxx</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">政治面目：</span>
            </div>
            <div class="content">
              <span>党员</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">入党团时间：</span>
            </div>
            <div class="content">
              <span>2003-2-3</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">家庭住址：</span>
            </div>
            <div class="content">
              <span>北京市朝阳区xxxxxxxxxxxx</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">手机号码：</span>
            </div>
            <div class="content">
              <span>12345678943</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">Email：</span>
            </div>
            <div class="content">
              <span>222334424#ddd</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">任教学科：</span>
            </div>
            <div class="content">
              <span>计算机教学</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">部门：</span>
            </div>
            <div class="content">
              <span>计算机学院</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">参加工作时间：</span>
            </div>
            <div class="content">
              <span>2009.3.1</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">工作状态：</span>
            </div>
            <div class="content">
              <span>任职</span>
            </div>
          </div>
        </el-col>

        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">聘用合同起始时间：</span>
            </div>
            <div class="content">
              <span></span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">聘用合同终止时间：</span>
            </div>
            <div class="content">
              <span></span>
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
            :disabled="false"
            v-model="AuditingReason"
            type="textarea"
            placeholder="请输入内容(审核通过无需输入)"/>
        </el-row>
      </div>
      <div class="foot">
        <span slot="footer" class="dialog-footer">
          <el-button type="success" size="small" plain>审核通过</el-button>
          <el-button type="danger" size="small" plain>审核未通过</el-button>
          <el-button type="primary" @click="jibenVisible = false">关闭</el-button>
        </span>
      </div>
    </el-dialog>
    <el-dialog :visible.sync="zhuanyeVisible" title="审核详情">
      <el-row :gutter="20">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">职&#8195;&#8195;称：</span>
            </div>
            <div class="content">
              <span>教授</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">职称评定时间：</span>
            </div>
            <div class="content">
              <span>2013.5.4</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">岗位级别：</span>
            </div>
            <div class="content">
              <span>教授</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">荣誉称号：</span>
            </div>
            <div class="content">
              <span>名誉教授</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">荣誉称号取得时间：</span>
            </div>
            <div class="content">
              <span>2003.3.3</span>
            </div>
          </div>
        </el-col>
      </el-row>
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">专业发展称号：</span>
            </div>
            <div class="content">
              <span>学科带头人</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="single">
            <div class="biaoqian">
              <span style="font-weight: bolder">专业发展称号取得时间：</span>
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
    <el-dialog :visible.sync="workVisible" title="审核详情">
      <el-row :gutter="20" style="padding-top: 10px">
        <el-col :span="1">
          <span style="font-weight: bolder">xxx</span>
        </el-col>
        <el-col :span="4">
          <div class="biaoqian">
            <span style="font-weight: bolder">工作单位：</span>
          </div>
          <div class="content">
            <span>大学</span>
          </div>
        </el-col>
        <el-col :span="4">
          <div class="biaoqian">
            <span style="font-weight: bolder">担任职务：</span>
          </div>
          <div class="content">
            <span>讲师</span>
          </div>
        </el-col>
        <el-col :span="4">
          <div class="biaoqian">
            <span style="font-weight: bolder">开始时间：</span>
          </div>
          <div class="content">
            <span>2000</span>
          </div>
        </el-col>
        <el-col :span="4">
          <div class="biaoqian">
            <span style="font-weight: bolder">结束时间：</span>
          </div>
          <div class="content">
            <span>xxxxxx</span>
          </div>
        </el-col>
        <el-col :span="4">
          <div class="biaoqian">
            <span style="font-weight: bolder">证明人：</span>
          </div>
          <div class="content">
            <span>王老师</span>
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
    name: 'peopleApproval',
    data(){
      return{
        AuditingReason:'',
        zhuanyeVisible:false,
        workVisible:false,
        jibenVisible:false,
        peopleData:[
          {
            number:'1',
            sub:'基本信息',
            applypeople:'王老师',
            approvalpeople:'刘老师',
            subdate:'2019-9-2',
            approvaldate:'2020-1-2',
            approval:'待通过',
          },
          {
            number:'2',
            sub:'专业能力',
            applypeople:'张老师',
            approvalpeople:'刘老师',
            subdate:'2017-9-2',
            approvaldate:'2018-1-2',
            approval:'待通过',
          },
          {
            number:'3',
            sub:'工作经历',
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
      jibenview(sub){
        if(sub ==='基本信息'){
          this.jibenVisible = true;
        }else if(sub === '专业能力'){
          this.zhuanyeVisible = true;
        }else if(sub === '工作经历'){
          this.workVisible =true;
        }
      }
    }
  }
</script>

<style scoped>
.foot{
  text-align: center;
}
</style>

<template>
  <div class="app-container">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <div class="fisrt_layer">
          <div class="function_container">
            <h3>项目申报表</h3>
            <div class="function_items">
              <div style="float: left">
                <span>项目级别：</span>
                <el-select v-model="value1" style="width: 120px" placeholder="请选择">
                  <el-option
                    v-for="item in option1"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </div>
              <div class="option_container" style="float: left">
                <span>项目类型：</span>
                <el-select v-model="value2" style="width: 120px" placeholder="请选择">
                  <el-option
                    v-for="item in option2"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </div>
              <div class="option_container" style="float: left">
                <span>申报时间：</span>
                <el-date-picker
                  v-model="time"
                  style="width: 320px"
                  type="daterange"
                  range-separator="-"
                  start-placeholder="开始日期"
                  end-placeholder="结束日期"
                />
              </div>
              <div style="float: right">
                <el-upload
                  class="upload-demo"
                  action="https://jsonplaceholder.typicode.com/posts/"
                  :on-preview="handlePreview"
                  :on-remove="handleRemove"
                  :before-remove="beforeRemove"
                  multiple
                  :limit="3"
                  :on-exceed="handleExceed"
                  :file-list="fileList"
                >
                  <el-button size="small" type="primary">上传文件一键导入</el-button>
                  <!--                  <div slot="tip" class="el-upload__tip">只能上传jpg/png文件，且不超过500kb</div>-->
                </el-upload>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div>
        <div class="content_container">
          <div class="content_item">
            <h4>基本信息</h4>
            <el-row>
              <el-col :span="6">
                <span>申请人职称：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="8">
                <span>申请人所在学院：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="8">
                <span>申请人所在实验室：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
            </el-row>
          </div>
          <el-divider />
          <div class="content_item">
            <h4>项目信息</h4>
            <el-row>
              <el-col :span="6">
                <span>项目名称：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>主管部门：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>项目性质：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>项目时间：</span>
                <el-date-picker
                  v-model="time"
                  style="width: 200px;margin-top: 20px"
                  type="daterange"
                  range-separator="-"
                  start-placeholder="开始日期"
                  end-placeholder="结束日期"
                />
              </el-col>
            </el-row>
            <el-row style="margin-top: 20px;margin-top: 20px">
              <el-col :span="6">
                <span>项目预算：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>参与人员：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>项目负责人：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>申报单位：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
            </el-row>
            <el-row style="margin-top: 20px">
              <div style="margin-bottom: 10px"><span >项目方案：</span></div>
              <el-input
                v-model="textarea2"
                type="textarea"
                :autosize="{ minRows: 2, maxRows: 8}"
                placeholder="请输入内容"
              />
            </el-row>
            <el-row style="margin-top: 20px">
              <div style="margin-bottom: 10px"><span >技术指标：</span></div>
              <el-input
                v-model="textarea2"
                type="textarea"
                :autosize="{ minRows: 2, maxRows: 8}"
                placeholder="请输入内容"
              />
            </el-row>
            <el-divider />
            <h4>预算信息</h4>
            <el-row style="margin-top: 20px;margin-top: 20px">
              <el-col :span="6">
                <span>预算总额：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>设备费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>材料费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>测试化验加工费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
            </el-row>
            <el-row style="margin-top: 20px;margin-top: 20px">
              <el-col :span="6">
                <span>燃料动力费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>差旅费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>会议费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>国际合作与交流费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
            </el-row>
            <el-row style="margin-top: 20px;margin-top: 20px">
              <el-col :span="6">
                <span>资料费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>数据采集费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>印刷费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>知识产权事务费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
            </el-row>
            <el-row style="margin-top: 20px;margin-top: 20px">
              <el-col :span="6">
                <span>劳务费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>专家咨询费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>管理费：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
              <el-col :span="6">
                <span>其他费用：</span>
                <el-input v-model="input" style="width: 200px" placeholder="请输入内容" />
              </el-col>
            </el-row>
            <el-row style="margin-top: 20px">
              <el-upload
                class="upload-demo"
                action="https://jsonplaceholder.typicode.com/posts/"
                :on-preview="handlePreview"
                :on-remove="handleRemove"
                :before-remove="beforeRemove"
                multiple
                :limit="3"
                :on-exceed="handleExceed"
                :file-list="fileList"
              >
                <el-button size="small" type="primary">附件上传</el-button>
                <div slot="tip" class="el-upload__tip">只能上传word/PDF文件，且不超过500kb</div>
              </el-upload>
            </el-row>

          </div>
          <div class="button_container">
            <div style="float: right">
              <el-button size="small" type="success">重置</el-button>
              <el-button size="small" type="primary" @click="submitVisible = true">提交</el-button>
            </div>
          </div>
        </div>
      </div>
    </el-card>
    <el-dialog :visible.sync="submitVisible" title="提交信息">
      <div>
<!--        <el-row :gutter="5">-->
<!--          <el-col :span="4">-->
<!--              <span style="font-weight: bolder">选择提交部门：</span>-->
<!--          </el-col>-->
<!--          <el-col :span="6">-->
<!--            <div class="select">-->
<!--              <el-select v-model="type_select_department" placeholder="请选择提交部门" >-->
<!--                <el-option label="科研处" value="keyan"/>-->
<!--                <el-option label="财务处" value="caiwu"/>-->
<!--              </el-select>-->
<!--            </div>-->
<!--          </el-col>-->
<!--        </el-row>-->
        <el-row :gutter="5" style="margin-top: 5px">
          <el-col :span="4">
            <span style="font-weight: bolder">选择审核人：</span>
          </el-col>
          <el-col :span="6">
            <div class="select">
              <el-select v-model="type_select_people" placeholder="请选择审核人" >
                <el-option label="王老师" value="keyan"/>
                <el-option label="刘老师" value="keyan"/>
                <el-option label="张老师" value="keyan"/>
                <el-option label="赵老师" value="keyan"/>
                <el-option label="李老师" value="caiwu"/>
              </el-select>
            </div>
          </el-col>
        </el-row>
        <el-row style="padding-top: 10px">
          <span style="font-weight: bolder">备注</span>
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
          <el-button type="primary" size="small" plain @click="submit">确认提交</el-button>
          <el-button type="danger" size="small" plain @click="submitVisible = false">取消</el-button>
<!--          <el-button type="primary" @click="zhuanyeVisible = false" size="small" plain>关闭</el-button>-->
        </span>
      </div>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: 'FormFill',
  data() {
    return {
      // 修改
      value1: '',
      option1: [{
        value: '个人项目',
        label: '个人项目'
      }, {
        value: '集体项目',
        label: '集体项目'
      }],
      value2: '',
      option2: [{
        value: '院级课题',
        label: '院级课题'
      }, {
        value: '厅级课题',
        label: '厅级课题'
      }, {
        value: '省级课题',
        label: '省级课题'
      }, {
        value: '国家级课题',
        label: '国家级课题'
      }, {
        value: '教育厅课题',
        label: '教育厅课题'
      }],
      time: '',
      submitVisible:false,
      type_select_department:'',
      type_select_people:''
    }
  },
  methods: {
    submit() {
      this.submitVisible = false
      this.$message({
        type:'success',
        message:'提交成功'
      })
  }
  }
}
</script>

<style scoped>
  .option_container{
    float: left;
    margin-left: 30px;
  }
  .button_container{
    margin-bottom: 20px;
  }
  .foot{
    text-align: center;
    margin-top: 20px;
  }
</style>

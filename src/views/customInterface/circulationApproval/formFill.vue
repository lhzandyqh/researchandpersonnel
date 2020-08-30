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
              <span>项目方案：</span>
              <el-input
                v-model="textarea2"
                type="textarea"
                :autosize="{ minRows: 2, maxRows: 8}"
                placeholder="请输入内容"
              />
            </el-row>
            <el-row style="margin-top: 20px">
              <span>技术指标：</span>
              <el-input
                v-model="textarea2"
                type="textarea"
                :autosize="{ minRows: 2, maxRows: 8}"
                placeholder="请输入内容"
              />
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
              <el-button size="small" type="primary">提交</el-button>
            </div>
          </div>
        </div>
      </div>
    </el-card>
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
      time: ''
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

</style>

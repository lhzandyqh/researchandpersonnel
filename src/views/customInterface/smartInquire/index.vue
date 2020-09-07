<template>
    <div class="app-container">
      <el-card class="box-card">
        <el-row gutter="20">
          <el-col :span="8">
          </el-col>
        </el-row>
      </el-card>
      <div style="margin-bottom: 20px">
        <div style="margin-bottom: 20px;margin-left: 20px;font-weight: bold;font-size:18px">
          <span>精准查询</span>
        </div>
        <div style="float: left;margin-left:20px">
          <el-input v-model="inputsearch" style="width: 300px" placeholder="请输入教师姓名"/>
        </div>
        <el-select v-model="selectWord1" placeholder="选择所在学院" style="margin-left: 20px" >
          <el-option label="文学院" value="1"></el-option>
          <el-option label="理学院" value="2"></el-option>
          <el-option label="教育学院" value="3"></el-option>
          <el-option label="医学院" value="4"></el-option>
          <el-option label="商学院" value="5"></el-option>
          <el-option label="管理学院" value="6"></el-option>
          <el-option label="机械工程学院" value="7"></el-option>
          <el-option label="电子信息学院" value="8"></el-option>
          <el-option label="电气工程学院" value="9"></el-option>
        </el-select>
        <el-select v-model="selectWord2" placeholder="选择所在部门">
          <el-option label="校党委" value="1"></el-option>
          <el-option label="教务处" value="2"></el-option>
          <el-option label="科研处" value="3"></el-option>
          <el-option label="电教设备处" value="4"></el-option>
          <el-option label="审计处" value="5"></el-option>
          <el-option label="档案中心" value="6"></el-option>
        </el-select>
        <el-button type="primary" style="margin-left: 10px" >查询</el-button>

      </div>
      <div style="margin-left: 20px;margin-right: 20px">
        <el-card class="box-card">
          <div slot="header" class="clearfix">
          <span style="font-weight: bold">
            选择显示的字段（
            <span style="color: red">下列选中为默认显示方式</span>）
          </span>
          </div>
          <div>
            <!--          <el-checkbox :indeterminate="isIndeterminate" v-model="checkAll" @change="handleCheckAllChange">全选</el-checkbox>-->
            <el-checkbox-group v-model="checkList">
              <el-checkbox v-for="(item,index) in tableList" :key="index" :label="item.label" style="margin-top: 20px;margin-right: 10px;width: 150px">
                {{ item.value }}
              </el-checkbox>
            </el-checkbox-group>
          </div>
        </el-card>
      </div>
      <div style="margin-top: 20px">
        <div style="margin-bottom: 20px;margin-left: 20px;font-weight: bold;font-size:18px">
          <span>模糊查询</span>
        </div>
        <el-row>
          <span style="font-size: 16px;margin-left:15px;font-weight: bolder;"> 设置查询条件:</span>
          <el-select v-model="selectWord3" placeholder="选择学院" style="margin-left: 20px" >
            <el-option label="文学院" value="1"></el-option>
            <el-option label="理学院" value="2"></el-option>
            <el-option label="教育学院" value="3"></el-option>
            <el-option label="医学院" value="4"></el-option>
            <el-option label="商学院" value="5"></el-option>
            <el-option label="管理学院" value="6"></el-option>
            <el-option label="机械工程学院" value="7"></el-option>
            <el-option label="电子信息学院" value="8"></el-option>
            <el-option label="电气工程学院" value="9"></el-option>
          </el-select>
          <el-select v-model="selectWord4" placeholder="选择部门">
            <el-option label="校党委" value="1"></el-option>
            <el-option label="教务处" value="2"></el-option>
            <el-option label="科研处" value="3"></el-option>
            <el-option label="电教设备处" value="4"></el-option>
            <el-option label="审计处" value="5"></el-option>
            <el-option label="档案中心" value="6"></el-option>
          </el-select>
            <el-select v-model="projectsub" placeholder="选择项目类型" >
              <el-option
                v-for="item in options1"
                :key="item.value"
                :label="item.label"
                :value="item.value"/>
            </el-select>
          <el-select v-model="projectclass" placeholder="选择项目级别">
            <el-option
              v-for="item in options2"
              :key="item.value"
              :label="item.label"
              :value="item.value"/>
          </el-select>
          <el-button type="primary" style="margin-left: 10px" >查询</el-button>
        </el-row>
      </div>
    </div>
</template>

<script>
    export default {
        name: "index",
      data(){
          return{
            projectsub:'',
            projectclass:'',
            inputsearch:'',
            selectWord1: '',
            selectWord3: '',
            selectWord4: '',
            options1: [
              {
                value: '个人项目',
                label: '个人项目'
              },
              {
                value: '集体项目',
                label: '集体项目'
              }
            ],
            selectWord2: '',
            options2: [
              {
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
              }
            ],
            tableList: [
              { label: 'userinfo', value: '基本信息' },
              { label: 'zhuanye', value: '专业能力 ' },
              { label: 'work', value: '工作经历' },
              { label: 'academic', value: '科研成果' },
              { label: 'project', value: '项目信息' },
            ],
            checkList: [], // 选中展示的字段
            uncheckList: {}, // 控制隐藏的字段
          }
      }
    }
</script>

<style scoped>
  .box-card {
    width: 100%;
    height: 100%;
  }
  /deep/ .el-card__body{
    height: 100vh;
  }
</style>

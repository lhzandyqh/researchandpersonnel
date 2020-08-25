<template>
  <div class="app-container">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span style="font-weight: bolder;color:#409EFF">基本信息</span>
        <el-button style="float: right; padding: 3px 0;margin-right: 20px" type="text">修改</el-button>
        <el-button style="float: right; padding: 3px 0;margin-right: 15px" type="text">查看</el-button>
      </div>
      <el-form ref="form" :model="form" label-width="150px">
        <el-row>
          <el-col :span="10">
            <el-form-item label="姓名">
              <el-input v-model="form.name" style="width: 300px" />
            </el-form-item>
          </el-col>
          <el-col :span="12"><el-form-item label="年龄">
            <el-input v-model="form.name" style="width: 310px;" />
          </el-form-item></el-col>
        </el-row>
        <el-row>
          <el-col :span="10"><el-form-item label="民族">
            <el-input v-model="form.name" style="width: 300px" />
          </el-form-item></el-col>
          <el-col :span="12">
            <el-form-item label="性别">
              <el-select v-model="form.region" style="width: 310px" placeholder="请选择性别">
                <el-option label="男" value="shanghai" />
                <el-option label="女" value="beijing" />
              </el-select>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>

          <el-col :span="10">
            <el-form-item label="身份证号">
              <el-input v-model="form.name" style="width: 300px;" />
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="入党时间">
              <el-date-picker v-model="form.date1" type="date" placeholder="选择日期" style="width: 310px;" />
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col span="10">
            <el-form-item label="爱好">
              <el-cascader
                style="width: 300px"
                :options="options"
                :props="{ multiple: true }"
                clearable
              />
            </el-form-item>
          </el-col>
          <el-col span="12">
            <el-form-item label="上传附件">
              <el-upload
                ref="upload"
                class="upload-demo"
                action="https://jsonplaceholder.typicode.com/posts/"
                :on-preview="handlePreview"
                :on-remove="handleRemove"
                :file-list="fileList"
                :auto-upload="false"
              >
                <el-button slot="trigger" size="small" type="primary">选取文件</el-button>
                <el-button style="margin-left: 10px;background: #42b983" size="small" type="success" @click="submitUpload">上传</el-button>
              </el-upload>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <div style="padding-top: 20px;text-align: center;">
            <el-button>保存</el-button>
            <el-button type="primary" @click="onSubmit">提交</el-button>
          </div>
        </el-row>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'OneTimeCollection',
  data() {
    return {
      // fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}],
      options: [{
        value: 1,
        label: '东南',
        children: [{
          value: 2,
          label: '上海',
          children: [
            { value: 3, label: '普陀' },
            { value: 4, label: '黄埔' },
            { value: 5, label: '徐汇' }
          ]
        }, {
          value: 7,
          label: '江苏',
          children: [
            { value: 8, label: '南京' },
            { value: 9, label: '苏州' },
            { value: 10, label: '无锡' }
          ]
        }, {
          value: 12,
          label: '浙江',
          children: [
            { value: 13, label: '杭州' },
            { value: 14, label: '宁波' },
            { value: 15, label: '嘉兴' }
          ]
        }]
      }, {
        value: 17,
        label: '西北',
        children: [{
          value: 18,
          label: '陕西',
          children: [
            { value: 19, label: '西安' },
            { value: 20, label: '延安' }
          ]
        }, {
          value: 21,
          label: '新疆维吾尔族自治区',
          children: [
            { value: 22, label: '乌鲁木齐' },
            { value: 23, label: '克拉玛依' }
          ]
        }]
      }],
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      }
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!')
    },
    submitUpload() {
      this.$refs.upload.submit()
    },
    handleRemove(file, fileList) {
      console.log(file, fileList)
    },
    handlePreview(file) {
      console.log(file)
    }
  }
}

</script>

<style>
  .text {
    font-size: 14px;
  }

  .item {
    margin-bottom: 18px;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both
  }

  .box-card {
    width: 100%;
    height: 100%;
  }
</style>


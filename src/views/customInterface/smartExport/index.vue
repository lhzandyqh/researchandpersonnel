<template>
  <div class="app-container">
    <el-row>
      <el-tabs>
        <el-tab-pane label="个人信息">
          <el-table
            :data="tableData"
            border
            style="width: 100%">
            <el-table-column
              prop="name"
              align="center"
              label="表名"
              width="220">
            </el-table-column>
            <el-table-column
              prop="personname"
              align="center"
              label="审核人"
              width="220">
            </el-table-column>
            <el-table-column
              prop="indate"
              align="center"
              label="填写日期"
              width="220">
            </el-table-column>
            <el-table-column
              prop="lastdate"
              align="center"
              label="有效期"
              width="220">
            </el-table-column>
            <el-table-column
              label="操作"
              align="center"
            >
              <template slot-scope="scope">
                <el-button @click="openpdf" type="text" size="medium" style="margin-right: 15px">预览</el-button>
                <a href="../../static/test1.pdf" class="download" download="test.pdf" title="下载" style="color: #00a4ff">点击下载</a>
              </template>
            </el-table-column>
          </el-table>
        </el-tab-pane>
        <el-tab-pane label="科研信息">
          <el-table
            :data="tableData"
            border
            style="width: 100%">
            <el-table-column
              prop="name"
              label="表名"
              align="center"
              width="220">
            </el-table-column>
            <el-table-column
              prop="personname"
              align="center"
              label="审核人"
              width="220">
            </el-table-column>
            <el-table-column
              prop="indate"
              align="center"
              label="填写日期"
              width="220">
            </el-table-column>
            <el-table-column
              prop="lastdate"
              align="center"
              label="有效期"
              width="220">
            </el-table-column>
            <el-table-column
              label="操作"
              align="center"
            >
              <template slot-scope="scope">
                <el-button @click="openpdf" type="text" size="medium" style="margin-right: 15px">预览</el-button>
                <a href="../../static/test1.pdf" class="download" download="test1.pdf" title="下载" style="color: #00a4ff">点击下载</a>
              </template>
            </el-table-column>
          </el-table>
        </el-tab-pane>
        <el-tab-pane label="项目报批">
        </el-tab-pane>
        <el-tab-pane label="项目管理">
        </el-tab-pane>
      </el-tabs>
    </el-row>
    <div>
      <el-dialog :visible.sync="showpdf" title="显示pdf" width="80%" fullscreen="true" >
        <el-card class="pdfcard">
        <iframe :src="pathUr" width="100%" height="100%" style="position:static;left: 0px;top: 40px;" frameborder="0"></iframe>
        </el-card>
      </el-dialog>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data() {
    return {
      showpdf:false,
      pathUr: '',
      tableData: [{
        name: '科技项目申请表',
        personname:'王老师',
        indate:'2019-6-20',
        lastdate:'2022-6-20',
      }, {
        name: '项目申报表',
        personname:'刘老师',
        indate:'2019-6-20',
        lastdate:'2022-6-20',
      },]
    };
  },
    methods: {
      openpdf() {
        document.title = 'test1.pdf'
        let filePath = 'test1.pdf'
        this.pathUr = '../../static/pdfjs/web/viewer.html?file=' + filePath   //  根据自己的文件地址将viewe.html引进来
        this.showpdf = true;
      },
    }
  }
</script>

<style scoped>
  /deep/ .el-dialog__header{
    padding-top: 10px;
  }
  /deep/ .el-card__body{
    height: 100%;
  }
  .transfer-footer {
    margin-left: 20px;
    padding: 6px 5px;
  }
  .pdfcard{
    width: 100%;
    height: 700px;
  }
</style>

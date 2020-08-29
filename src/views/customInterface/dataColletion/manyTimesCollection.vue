<template>
  <div class="app-container">
    <el-tabs >
<!--      v-model="activeName" @tab-click="handleClick"-->
      <el-tab-pane label="中文核心论文登记">
        <h4 style="text-align: center;margin: 28px 0px 0px 0px; ">中文核心论文登记表</h4>
        <el-button @click="openDialog" style="float: right;margin-right: 15px" type="text">新增</el-button>
        <el-button style="float: right;margin-right: 15px" type="text">修改</el-button>
        <el-table
          :data="tableData"
          border
          style="width: 100%">
          <el-table-column
            prop="papername"
            align="center"
            label="论文名称"
            width="270"/>
          <el-table-column
            prop="isauthor"
            align="center"
            label="是否第一作者"
            width="110"/>
          <el-table-column
            prop="publication"
            align="center"
            label="发表刊物"
            width="220"/>
          <el-table-column
            prop="press"
            align="center"
            label="出版社"
            width="220"/>
          <el-table-column
            prop="pubtime"
            align="center"
            label="发表时间"
            width="120"/>
          <el-table-column
            prop="enclosure"
            align="center"
            label="附件"
            />
        </el-table>
      </el-tab-pane>
      <el-tab-pane label="三大检索论文登记">
          <h4 style="text-align: center;margin: 28px 0px 0px 0px;"> 三大检索论文登记表</h4>
          <el-button @click="openThreesDialog" style="float: right;margin-right: 15px" type="text">新增</el-button>
          <el-button style="float: right;margin-right: 15px" type="text">修改</el-button>
          <el-table
            :data="tableData"
            border
            style="width: 100%">
            <el-table-column
              prop="papername"
              align="center"
              label="论文名称"
              width="270"/>
            <el-table-column
              prop="isauthor"
              align="center"
              label="是否第一作者"
              width="110"/>
            <el-table-column
              prop="publication"
              align="center"
              label="发表刊物"
              width="220"/>
            <el-table-column
              prop="press"
              align="center"
              label="出版社"
              width="220"/>
            <el-table-column
              prop="pubtime"
              align="center"
              label="发表时间"
              width="120"/>
            <el-table-column
              prop="enclosure"
              align="center"
              label="附件"
            />
          </el-table>
      </el-tab-pane>
      <el-tab-pane label="非核心论文登记">
        <h4 style="text-align: center;margin: 28px 0px 0px 0px;">非核心论文登记表</h4>
        <el-button @click="openNoncoreDialog" style="float: right;margin-right: 15px" type="text">新增</el-button>
        <el-button style="float: right;margin-right: 15px" type="text">修改</el-button>
        <el-table
          :data="tableData"
          border
          style="width: 100%">
          <el-table-column
            prop="papername"
            align="center"
            label="论文名称"
            width="270"/>
          <el-table-column
            prop="isauthor"
            align="center"
            label="是否第一作者"
            width="110"/>
          <el-table-column
            prop="publication"
            align="center"
            label="发表刊物"
            width="220"/>
          <el-table-column
            prop="press"
            align="center"
            label="出版社"
            width="220"/>
          <el-table-column
            prop="pubtime"
            align="center"
            label="发表时间"
            width="120"/>
          <el-table-column
            prop="enclosure"
            align="center"
            label="附件"
          />
        </el-table>
      </el-tab-pane>
      <el-tab-pane label="专著登记">
        <h4 style="text-align: center;margin: 28px 0px 0px 0px;">专著登记表</h4>
        <el-button @click="openMonographsDialog" style="float: right;margin-right: 15px" type="text">新增</el-button>
        <el-button style="float: right;margin-right: 15px" type="text">修改</el-button>
        <el-table
          :data="tableData"
          border
          style="width: 100%">
          <el-table-column
            prop="papername"
            align="center"
            label="专著名称"
            width="270"/>
          <el-table-column
            prop="isauthor"
            align="center"
            label="专著类型"
            width="110"/>
          <el-table-column
            prop="publication"
            align="center"
            label="发表刊物"
            width="220"/>
          <el-table-column
            prop="press"
            align="center"
            label="出版社"
            width="220"/>
          <el-table-column
            prop="pubtime"
            align="center"
            label="发表时间"
            width="120"/>
          <el-table-column
            prop="enclosure"
            align="center"
            label="附件"
          />
        </el-table>
      </el-tab-pane>
      <el-tab-pane label="专利申报">
        <h4 style="text-align: center;margin: 28px 0px 0px 0px;">专利申报表</h4>
        <el-button @click="openPatentDialog" style="float: right;margin-right: 15px" type="text">新增</el-button>
        <el-button style="float: right;margin-right: 15px" type="text">修改</el-button>
        <el-table
          :data="tableData"
          border
          style="width: 100%">
          <el-table-column
            prop="papername"
            align="center"
            label="专利名称"
            width="250"/>
          <el-table-column
            prop="isauthor"
            align="center"
            label="专利编号"
            width="140"/>
          <el-table-column
            prop="publication"
            align="center"
            label="申请人(单位)"
            width="220"/>
          <el-table-column
            prop="press"
            align="center"
            label="通讯地址"
            width="220"/>
          <el-table-column
            prop="pubtime"
            align="center"
            label="申请时间"
            width="120"/>
          <el-table-column
            prop="enclosure"
            align="center"
            label="附件"
          />
        </el-table>
      </el-tab-pane>
    </el-tabs>
    <div>
      <el-dialog :visible.sync="dialogVisiblePatent" title="专利申报登记">
        <el-form ref="form" :model="form" label-width="100px">
          <el-form-item label="专利名称">
            <el-input v-model="form.patentname"/>
          </el-form-item>
          <el-form-item label="专利编号">
            <el-input v-model="form.patentnum"/>
          </el-form-item>
          <el-form-item label="申请人（单位）">
            <el-input v-model="form.applicant"/>
          </el-form-item>
          <el-form-item label="出版社">
            <el-input v-model="form.patentpress"/>
          </el-form-item>
          <el-form-item label="申请时间">
            <el-col :span="11">
              <el-date-picker v-model="form.patenttime" value-format=" yyyy-MM-dd " format="yyyy-MM-dd " type="date" placeholder="选择日期" style="width: 60%;"/>
            </el-col>
          </el-form-item>
          <el-form-item label="附件">
            <el-upload
              v-model="form.patentenclosure"
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
        </el-form>
        <div slot="footer" class="dialog-footer">
          <el-button @click="dialogVisiblePatent = false">取 消</el-button>
          <el-button type="primary" @click="addPatent">确 定</el-button>
        </div>
      </el-dialog>
    </div>
    <div>
      <el-dialog :visible.sync="dialogVisibleMonographs" title="专著登记">
        <el-form ref="form" :model="form" label-width="100px">
          <el-form-item label="专著名称">
            <el-input v-model="form.monographsname"/>
          </el-form-item>
          <el-form-item label="专著类型">
            <el-input v-model="form.monographsisauthor"/>
          </el-form-item>
          <el-form-item label="发表刊物">
            <el-input v-model="form.monographspublication"/>
          </el-form-item>
          <el-form-item label="出版社">
            <el-input v-model="form.monographspress"/>
          </el-form-item>
          <el-form-item label="发表时间">
            <el-col :span="11">
              <el-date-picker v-model="form.monographspubtime" value-format=" yyyy-MM-dd " format="yyyy-MM-dd " type="date" placeholder="选择日期" style="width: 60%;"/>
            </el-col>
          </el-form-item>
          <el-form-item label="附件">
            <el-upload
              v-model="form.monographsenclosure"
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
        </el-form>
        <div slot="footer" class="dialog-footer">
          <el-button @click="dialogVisibleMonographs = false">取 消</el-button>
          <el-button type="primary" @click="addMonographs">确 定</el-button>
        </div>
      </el-dialog>
    </div>
    <div>
      <el-dialog :visible.sync="dialogVisibleNoncore" title="非核心论文登记">
        <el-form ref="form" :model="form" label-width="100px">
          <el-form-item label="论文名称">
            <el-input v-model="form.noncorename"/>
          </el-form-item>
          <el-form-item label="是否第一作者">
            <el-select v-model="form.noncoreisauthor" style="width: 310px" placeholder="请选择">
              <el-option label="是" value="1"/>
              <el-option label="否" value="0"/>
            </el-select>
          </el-form-item>
          <el-form-item label="发表刊物">
            <el-input v-model="form.noncorepublication"/>
          </el-form-item>
          <el-form-item label="出版社">
            <el-input v-model="form.noncorepress"/>
          </el-form-item>
          <el-form-item label="发表时间">
            <el-col :span="11">
              <el-date-picker v-model="form.noncorepubtime" value-format=" yyyy-MM-dd " format="yyyy-MM-dd " type="date" placeholder="选择日期" style="width: 60%;"/>
            </el-col>
          </el-form-item>
          <el-form-item label="附件">
            <el-upload
              v-model="form.noncoreenclosure"
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
        </el-form>
        <div slot="footer" class="dialog-footer">
          <el-button @click="dialogVisibleNoncore = false">取 消</el-button>
          <el-button type="primary" @click="addNoncore">确 定</el-button>
        </div>
      </el-dialog>
    </div>
    <div>
      <el-dialog :visible.sync="dialogVisibleThrees" title="三大检索论文登记">
        <el-form ref="form" :model="form" label-width="100px">
          <el-form-item label="论文名称">
            <el-input v-model="form.threesname"/>
          </el-form-item>
          <el-form-item label="是否第一作者">
            <el-select v-model="form.threesisauthor" style="width: 310px" placeholder="请选择">
              <el-option label="是" value="1"></el-option>
              <el-option label="否" value="0"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="发表刊物">
            <el-input v-model="form.threespublication"/>
          </el-form-item>
          <el-form-item label="出版社">
            <el-input v-model="form.threespress"/>
          </el-form-item>
          <el-form-item label="发表时间">
            <el-col :span="11">
              <el-date-picker v-model="form.threespubtime" value-format=" yyyy-MM-dd " format="yyyy-MM-dd " type="date" placeholder="选择日期" style="width: 60%;"/>
            </el-col>
          </el-form-item>
          <el-form-item label="附件">
            <el-upload
              v-model="form.threesenclosure"
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
        </el-form>
        <div slot="footer" class="dialog-footer">
          <el-button @click="dialogVisibleThrees = false">取 消</el-button>
          <el-button type="primary" @click="addThrees">确 定</el-button>
        </div>
      </el-dialog>
    </div>
    <div>
      <el-dialog :visible.sync="dialogVisible" title="中文核心论文登记">
        <el-form ref="form" :model="form" label-width="100px">
          <el-form-item label="论文名称">
            <el-input v-model="form.papername"/>
          </el-form-item>
          <el-form-item label="是否第一作者">
            <el-select v-model="form.isauthor" style="width: 310px" placeholder="请选择">
              <el-option label="是" value="1"></el-option>
              <el-option label="否" value="0"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="发表刊物">
            <el-input v-model="form.publication"/>
          </el-form-item>
          <el-form-item label="出版社">
              <el-input v-model="form.press"/>
          </el-form-item>
          <el-form-item label="发表时间">
            <el-col :span="11">
              <el-date-picker v-model="form.pubtime" value-format=" yyyy-MM-dd " format="yyyy-MM-dd " type="date" placeholder="选择日期" style="width: 60%;"/>
            </el-col>
          </el-form-item>
          <el-form-item label="附件">
            <el-upload
              v-model="form.enclosure"
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
        </el-form>
        <div slot="footer" class="dialog-footer">
          <el-button @click="dialogVisible = false">取 消</el-button>
          <el-button type="primary" @click="addChinesePaper">确 定</el-button>
        </div>
      </el-dialog>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ManyTimesCollection',
  data() {
    return {
      // fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}],
      form: {
        papername: '',
        isauthor: '',
        publication: '',
        press:'',
        pubtime:'',
        enclosure:'',
        patentname:'',
        patentnum:'',
        applicant:'',
        patentpress:'',
        patenttime:'',
        patentenclosure:'',
        monographsname: '',
        monographsisauthor: '',
        monographspublication: '',
        monographspress:'',
        monographspubtime:'',
        monographsenclosure:'',
        threesname: '',
        threesisauthor: '',
        threespublication: '',
        threespress:'',
        threespubtime:'',
        threesenclosure:'',
        noncorename: '',
        noncoreisauthor: '',
        noncorepublication: '',
        noncorepress:'',
        noncorepubtime:'',
        noncoreenclosure:''
      },
      options: [{
        value: '1',
        label: '是'
      }, {
        value: '2',
        label: '否'
      }],
      value: '',
      value1: '',
      dialogVisiblePatent:false,
      dialogVisible:false,
      dialogVisibleMonographs:false,
      dialogVisibleNoncore:false,
      dialogVisibleThrees:false,
      tableData: [{
        papername: '大数据研究',
        isauthor: '是',
        publication: '中文核心刊物',
        press:'北京出版社',
        pubtime:'2020-8-20',
        enclosure:'证明材料.doc'
      }, {
        papername: '大数据研究',
        isauthor: '是',
        publication: '中文核心刊物',
        press:'北京出版社',
        pubtime:'2020-8-20',
        enclosure:'证明材料.doc'
      }, {
        papername: '大数据研究',
        isauthor: '是',
        publication: '中文核心刊物',
        press:'北京出版社',
        pubtime:'2020-8-20',
        enclosure:'证明材料.doc'
      }],

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
    },
    openDialog: function() {
      console.log('我点了')
      this.dialogVisible = true
    },
    addChinesePaper: function() {
      console.log('我点了')
      this.dialogVisible = false
    },
    addPatent: function() {
      console.log('我点了')
      this.dialogVisiblePatent = false
    },
    openPatentDialog: function() {
      console.log('我点了')
      this.dialogVisiblePatent = true
    },
    addMonographs: function() {
      console.log('我点了')
      this.dialogVisibleMonographs = false
    },
    openMonographsDialog: function() {
      console.log('我点了')
      this.dialogVisibleMonographs = true
    },
    addNoncore: function() {
      console.log('我点了')
      this.dialogVisibleNoncore = false
    },
    openNoncoreDialog: function() {
      console.log('我点了')
      this.dialogVisibleNoncore = true
    },
    addThrees: function() {
      console.log('我点了')
      this.dialogVisibleThrees = false
    },
    openThreesDialog: function() {
      console.log('我点了')
      this.dialogVisibleThrees = true
    },

  }
}
</script>

<style scoped>

</style>

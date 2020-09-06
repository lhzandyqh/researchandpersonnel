<template>
    <div class="app-container">
      <div class="filter-container">
        <el-row :gutter="1">
          <el-col :span="2">
            <div class="selector">
              <span style="font-size: 15px;font-weight: bolder;margin-left: 15px">项目类型:</span>
            </div>
          </el-col>
          <el-col :span="3">
            <el-select v-model="listQuery.qualification_type" placeholder="积分类型" clearable class="filter-item">
              <el-option label="个人项目" value="个人项目"/>
              <el-option label="集体项目" value="集体项目"/>
              <el-option label="教学建设" value="教学建设"/>
              <el-option label="学术科研" value="学术科研"/>
            </el-select>
          </el-col>
          <el-col :span="2" style="margin-left: 20px;margin-right: 0px">
            <div class="selector">
              <span style="font-size: 15px;font-weight: bolder;margin-left: 15px">项目级别:</span>
            </div>
          </el-col>
          <el-col :span="3">
            <div style="margin-left: 0px">
              <el-select v-model="value2" style="padding: 0px 0px 0px 0px" placeholder="项目级别">
                <el-option
                  v-for="item in option2"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value"
                />
              </el-select>
            </div>
          </el-col>
          <el-col :span="2" style="margin-left: 20px;margin-right: 0px">
            <div class="selector">
              <span style="font-size: 15px;font-weight: bolder;margin-left: 15px">积分类型:</span>
            </div>
          </el-col>
          <el-col :span="4">
            <div class="select">
              <el-select v-model="type_select_value" placeholder="请选择您的积分类型" >
                                      <el-option label="学术成果积分配置" value="xueshu"/>
                                      <el-option label="项目课题积分配置" value="yanjiuke"/>
                                      <el-option label="学术讲座与经验分享积分配置" value="jinyan"/>
                                      <el-option label="教育教学评比竞赛积分配置" value="jingsai"/>
                                      <el-option label="研究课积分配置" value="yanjiu"/>
                                      <el-option label="教育教学成果获奖积分配置" value="jiaoyu"/>
                                      <el-option label="教师指导学生参加学科比赛获奖情况积分配置" value="xueke"/>
                                      <el-option label="艺科体社团积分配置" value="yike"/>
                                      <el-option label="行政获奖积分配置" value="xinzheng"/>
                                      <el-option label="校本培训积分配置" value="xiaoben"/>
                </el-select>
            </div>
          </el-col>
          <el-col :span="6">
            <div class="add">
              <el-button class="filter-item" style="margin-left: 10px;float: right" type="primary" icon="el-icon-edit" @click="dialogPvVisible = true">新增积分</el-button>
            </div>
          </el-col>
        </el-row>
        <el-divider/>
        <el-table
          :data="projectData"
          border
          style="width: 70%">
          <el-table-column
            prop="projectname"
            label="项目名称"
            align="center"
            width="180">
          </el-table-column>
          <el-table-column
            prop="projectsub"
            label="项目类型"
            align="center"
            width="180">
          </el-table-column>
          <el-table-column
            prop="projectclass"
            label="项目级别"
            align="center"
            width="180">
          </el-table-column>
          <el-table-column
            prop="date"
            label="完成时间"
            align="center"
            width="180">
          </el-table-column>
          <el-table-column
            prop="score"
            label="分值"
            align="center"
            width="180">
          </el-table-column>
          <el-table-column
            align="center"
            label="操作">
          </el-table-column>
        </el-table>
      </div>
      <el-dialog :visible.sync="dialogPvVisible" title="新增积分">
        <el-form ref="form" label-width="150px" style="margin: 20px 0;">
          <el-form-item label="请选择您的积分项目">
            <el-select v-model="t_qualification_name" placeholder="请选择您的积分项目" >
              <el-option label="学术成果积分配置" value="xueshu"/>
              <el-option label="项目课题积分配置" value="xiangmu"/>
              <el-option label="学术讲座与经验分享积分配置" value="jinyan"/>
              <el-option label="教育教学评比竞赛积分配置" value="jingsai"/>
              <el-option label="研究课积分配置" value="yanjiu"/>
              <el-option label="教育教学成果获奖积分配置" value="jiaoyu"/>
              <el-option label="教师指导学生参加学科比赛获奖情况积分配置" value="xueke"/>
              <el-option label="艺科体社团积分配置" value="yike"/>
              <el-option label="行政获奖积分配置" value="xinzheng"/>
              <el-option label="校本培训积分配置" value="xiaoben"/>
            </el-select>
          </el-form-item>
        </el-form>
        <el-divider/>
        <el-row v-if="t_qualification_name==='xueshu'">
          <el-form ref="xueshuform" :model="xueshuform" label-width="200px">
            <el-form-item label="学术成果载体类型">
              <el-select v-model="xueshuform.type" placeholder="请选择学术成果载体类型" style="width: 60%;">
                <el-option label="论文" value="论文"/>
                <el-option label="专著" value="专著"/>
              </el-select>
            </el-form-item>
            <el-form-item label="是否第一作者">
              <el-select v-model="xueshuform.first" placeholder="请选择是否第一作者">
                <el-option label="是" value="是"/>
                <el-option label="否" value="否"/>
              </el-select>
            </el-form-item>
            <el-form-item label="刊物等级（出版社等级）">
              <el-select v-model="xueshuform.rank" placeholder="请选择刊物等级（出版社等级）">
                <el-option label="核心期刊" value="核心期刊"/>
                <el-option label="一般期刊" value="一般期刊"/>
                <el-option label="区级" value="区级"/>
                <el-option label="校级" value="校级"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="xueshuform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='xiangmu'">
          <el-form ref="yanjiukeform" :model="yanjiukeform" label-width="100px">
            <el-form-item label="课题级别">
              <el-select v-model="yanjiukeform.rank" placeholder="请选择课题级别">
                <el-option label="国家级" value="国家级"/>
                <el-option label="区级" value="区级"/>
                <el-option label="市级" value="市级"/>
                <el-option label="校级" value="校级"/>
              </el-select>
            </el-form-item>
            <el-form-item label="个人角色">
              <el-select v-model="yanjiukeform.role" placeholder="请选择个人角色">
                <el-option label="主持" value="主持"/>
                <el-option label="参与" value="参与"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="yanjiukeform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='jinyan'">
          <el-form ref="jinyanform" :model="jinyanform" label-width="100px">
            <el-form-item label="活动类型">
              <el-select v-model="jinyanform.type" placeholder="请选择活动类型">
                <el-option label="教育教学研讨会" value="教育教学研讨会"/>
                <el-option label="中科玉兰学术讲坛" value="中科玉兰学术讲坛"/>
                <el-option label="进修材料分析" value="进修材料分析"/>
                <el-option label="其他" value="其他"/>
              </el-select>
            </el-form-item>
            <el-form-item label="课题级别">
              <el-select v-model="jinyanform.rank" placeholder="请选择课题级别">
                <el-option label="国家级" value="国家级"/>
                <el-option label="区级" value="区级"/>
                <el-option label="市级" value="市级"/>
                <el-option label="校级" value="校级"/>
                <el-option label="教研组" value="教研组"/>
                <el-option label="年级组" value="年级组"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="jinyanform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='jingsai'">
          <el-form ref="jinsaiform" :model="jinsaiform" label-width="100px">
            <el-form-item label="竞赛类型">
              <el-select v-model="jinsaiform.type" placeholder="请选择获奖级别">
                <el-option label="论文案例" value="论文案例"/>
                <el-option label="现场课" value="现场课"/>
                <el-option label="说课" value="说课"/>
                <el-option label="基本功" value="基本功"/>
                <el-option label="其他" value="其他"/>
              </el-select>
            </el-form-item>
            <el-form-item label="获奖级别">
              <el-select v-model="jinsaiform.rank" placeholder="请选择获奖级别">
                <el-option label="国家级" value="国家级"/>
                <el-option label="区级" value="区级"/>
                <el-option label="市级" value="市级"/>
                <el-option label="校级" value="校级"/>
              </el-select>
            </el-form-item>
            <el-form-item label="获奖等级">
              <el-select v-model="jinsaiform.denji" placeholder="请选择获奖等级">
                <el-option label="一等奖" value="一等奖"/>
                <el-option label="二等奖" value="二等奖"/>
                <el-option label="三等奖" value="三等奖"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="jinsaiform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='yanjiu'">
          <el-form ref="yanjiuform" :model="yanjiuform" label-width="100px">
            <el-form-item label="研究课类型">
              <el-select v-model="yanjiuform.type" placeholder="研究课类型">
                <el-option label="公开课" value="公开课"/>
                <el-option label="主题课" value="主题课"/>
                <el-option label="观摩课" value="观摩课"/>
                <el-option label="班会展示" value="班会展示"/>
              </el-select>
            </el-form-item>
            <el-form-item label="展示级别">
              <el-select v-model="yanjiuform.rank" placeholder="请选择展示级别">
                <el-option label="国家级" value="国家级"/>
                <el-option label="区级" value="区级"/>
                <el-option label="市级" value="市级"/>
                <el-option label="校级" value="校级"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="yanjiuform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='jiaoyu'">
          <el-form ref="jiaoyuform" :model="jiaoyuform" label-width="100px">
            <el-form-item label="获奖级别">
              <el-select v-model="jiaoyuform.region" placeholder="请选择获奖级别">
                <el-option label="国家级" value="国家级"/>
                <el-option label="区级" value="区级"/>
                <el-option label="市级" value="市级"/>
                <el-option label="校级" value="校级"/>
              </el-select>
            </el-form-item>
            <el-form-item label="获奖等级">
              <el-select v-model="jiaoyuform.rank" placeholder="请选择获奖等级">
                <el-option label="一等奖" value="一等奖"/>
                <el-option label="二等奖" value="二等奖"/>
                <el-option label="三等奖" value="三等奖"/>
              </el-select>
            </el-form-item>
            <el-form-item label="获奖角色">
              <el-select v-model="jiaoyuform.role" placeholder="请选择获奖角色">
                <el-option label="参与" value="参与"/>
                <el-option label="主持" value="主持"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="jiaoyuform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='xueke'">
          <el-form ref="xuekeform" :model="xuekeform" label-width="100px">
            <el-form-item label="学科" style="width: 200px">
              <el-input v-model="xuekeform.subject"/>
            </el-form-item>
            <el-form-item label="获奖级别">
              <el-select v-model="xuekeform.region" placeholder="请选择获奖级别">
                <el-option label="国家级" value="国家级"/>
                <el-option label="区级" value="区级"/>
                <el-option label="市级" value="市级"/>
                <el-option label="校级" value="校级"/>
              </el-select>
            </el-form-item>
            <el-form-item label="获奖等级">
              <el-select v-model="xuekeform.rank" placeholder="请选择获奖等级">
                <el-option label="一等奖" value="一等奖"/>
                <el-option label="二等奖" value="二等奖"/>
                <el-option label="三等奖" value="三等奖"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="xuekeform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='yike'">
          <el-form ref="yikeform" :model="yikeform" label-width="100px">
            <el-form-item label="比赛类别">
              <el-select v-model="yikeform.type" placeholder="请选择比赛类别">
                <el-option label="艺术" value="艺术"/>
                <el-option label="科技" value="科技"/>
                <el-option label="体育" value="体育"/>
              </el-select>
            </el-form-item>
            <el-form-item label="获奖级别">
              <el-select v-model="yikeform.rank" placeholder="请选择获奖级别">
                <el-option label="一等奖" value="一等奖"/>
                <el-option label="二等奖" value="二等奖"/>
                <el-option label="三等奖" value="三等奖"/>
                <el-option label="其他" value="其他"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="yikeform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='xinzheng'">
          <el-form ref="xinzhengform" :model="xinzhengform" label-width="100px">
            <el-form-item label="获奖级别">
              <el-select v-model="xinzhengform.region" placeholder="请选择获奖级别">
                <el-option label="国家级" value="国家级"/>
                <el-option label="区级" value="区级"/>
                <el-option label="市级" value="市级"/>
                <el-option label="校级" value="校级"/>
              </el-select>
            </el-form-item>
            <el-form-item label="获奖等级">
              <el-select v-model="xinzhengform.rank" placeholder="请选择获奖等级">
                <el-option label="一等奖" value="一等奖"/>
                <el-option label="二等奖" value="二等奖"/>
                <el-option label="三等奖" value="三等奖"/>
              </el-select>
            </el-form-item>
            <el-form-item label="获奖形式">
              <el-select v-model="xinzhengform.form" placeholder="请选择获奖等级">
                <el-option label="团队" value="团队"/>
                <el-option label="个人" value="个人"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="xinzhengform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <el-row v-if="t_qualification_name==='xiaoben'">
          <el-form ref="xiaobenform" :model="xiaobenform" label-width="100px">
            <el-form-item label="培训类型">
              <el-select v-model="xiaobenform.type" placeholder="请选择培训类型">
                <el-option label="全校大会" value="全校大会"/>
                <el-option label="教研组会" value="教研组会"/>
                <el-option label="年级组会" value="年级组会"/>
                <el-option label="专题培训" value="专题培训"/>
              </el-select>
            </el-form-item>
            <el-form-item label="分值" style="width: 400px">
              <el-input v-model="xiaobenform.score"/>
            </el-form-item>
          </el-form>
        </el-row>
        <span slot="footer" class="dialog-footer">
        <el-button type="primary" @click="dialogPvVisible = false">关闭</el-button>
        <el-button type="success" >确定</el-button>
      </span>
      </el-dialog>
    </div>
</template>

<script>
    export default {
        name: "index",
      data(){
          return{
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
            projectData :[{
              projectname:'自然语言处理问答系统',
              projectsub:'个人项目',
              projectclass:'省级',
              date:'2019-9-8',
              score:'5'
            },
              {
                projectname:'专业智能知识库建设',
                projectsub:'教学建设',
                projectclass:'省级',
                date:'2020-3-4',
                score:'5'
              },
              {
                projectname:'NLP语言智能识别',
                projectsub:'学术科研',
                projectclass:'国家级',
                date:'2019-7-6',
                score:'10'
              },
              {
                projectname:'校园大数据中心建设',
                projectsub:'集体项目',
                projectclass:'厅级',
                date:'2020-4-5',
                score:'8'
              }],
            dialogPvVisible: false,
            listQuery: {
              qualification_type: '',
              department_level: '',
              qualification_level: ''
            },
            xueshuform: {
              type: '',
              first: '',
              rank: '',
              score: ''
            },
            yanjiukeform: {
              role: '',
              rank: '',
              score: ''
            },
            jinyanform: {
              type: '',
              rank: '',
              score: ''
            },
            jinsaiform: {
              type: '',
              rank: '',
              denji: '',
              score: ''
            },
            yanjiuform: {
              type: '',
              rank: '',
              score: ''
            },
            jiaoyuform: {
              region: '',
              rank: '',
              role: '',
              score: ''
            },
            xuekeform: {
              region: '',
              rank: '',
              score: '',
              subject: ''
            },
            yikeform: {
              type: '',
              rank: '',
              score: ''
            },
            xinzhengform: {
              region: '',
              rank: '',
              form: '',
              score: ''
            },
            xiaobenform: {
              type: '',
              score: ''
            },
            t_qualification_name: 'xueshu',
            type_select_value: 'xueshu',
          }
     }
    }
</script>

<style scoped>
.selector{
  margin-top: 10px;
}
</style>

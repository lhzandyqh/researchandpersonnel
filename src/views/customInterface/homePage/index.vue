<template>
  <div class="app-container">
    <div v-if="roles==='教师'">
      <el-card class="box-card">
        <div slot="header" class="clearfix">
          <!--          <span>卡片名称</span>-->
          <div class="main_container juli">
            <div class="item_content">
              <div class="item zi_border">
                <span>科研任务/项目进行数(个)</span>
                <div class="shuzi">2</div>
              </div>
              <div class="item lan_border">
                <span>科研任务/项目审批数(个)</span>
                <div class="shuzi">4</div>
              </div>
              <div class="item hong_border">
                <span>科研论文发表数(篇)</span>
                <div class="shuzi">12</div>
              </div>
              <div class="item lv_border">
                <span>科研任务/项目完成数(个)</span>
                <div class="shuzi">10</div>
              </div>
            </div>
            <div />
          </div>
        </div>
        <div>
          <el-row>
            <el-col :span="14">
              <chart-one />
            </el-col>
            <el-col :span="8">
              <chart-two />
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="14">
             <chart_three></chart_three>
            </el-col>

          </el-row>
        </div>
      </el-card>
    </div>
    <div v-if="roles==='科研主管'">
      <el-card class="box-card">
        <div slot="header" class="clearfix">
          <!--          <span>卡片名称</span>-->
          <div class="main_container juli">
            <div class="item_content">
              <div class="item zi_border">
                <span>校科研项目本年度总数（个）</span>
                <div class="shuzi">43</div>
              </div>
              <div class="item lan_border">
                <span>科研任务/论文待审批数(个)</span>
                <div class="shuzi">6</div>
              </div>
              <div class="item hong_border">
                <span>科研论文本年度发表数(篇)</span>
                <div class="shuzi">12</div>
              </div>
              <div class="item lv_border">
                <span>总科研经费（元）</span>
                <div class="shuzi">6650000</div>
              </div>
            </div>
            <div />
          </div>
        </div>
        <div>
          <el-row>
            <chart-four></chart-four>
          </el-row>
          <el-row>
            <el-col :span="14">
              <chart-five></chart-five>
            </el-col>
            <el-col :span="10">
              <chart-six></chart-six>
            </el-col>
          </el-row>
        </div>
      </el-card>
    </div>
    <div v-if="roles==='系部主管'">
      <el-card class="box-card">
        <div slot="header" class="clearfix">
          <!--          <span>卡片名称</span>-->
          <div class="main_container juli">
            <div class="item_content">
              <div class="item zi_border">
                <span>学院科研任务/项目进行数(个)</span>
                <div class="shuzi">37</div>
              </div>
              <div class="item lan_border">
                <span>科研任务/项目待审批数(个)</span>
                <div class="shuzi">6</div>
              </div>
              <div class="item hong_border">
                <span>学院科研论文发表数(篇)</span>
                <div class="shuzi">67</div>
              </div>
              <div class="item lv_border">
                <span>总科研经费（元）</span>
                <div class="shuzi">1200000</div>
              </div>
            </div>
            <div />
          </div>
        </div>
        <div>
          <el-row>
            <chart-seven></chart-seven>
          </el-row>
          <el-row>
            <el-col :span="14">
              <chart-eight></chart-eight>
            </el-col>
            <el-col :span="10">
              <chart-nine></chart-nine>
            </el-col>
          </el-row>
        </div>
      </el-card>
    </div>
  </div>
</template>

<script>
import chartOne from '@/views/customInterface/homePage/echart/chart_one'
import chartTwo from '@/views/customInterface/homePage/echart/chart_two'
import chartFour from '@/views/customInterface/homePage/echart/chart_four'
import chartFive from '@/views/customInterface/homePage/echart/chart_five'
import chartSix from '@/views/customInterface/homePage/echart/chart_six'
import chartSeven from '@/views/customInterface/homePage/echart/chart_seven'
import chartEight from '@/views/customInterface/homePage/echart/chart_eight'
import chartNine from '@/views/customInterface/homePage/echart/chart_nine'
import chart_three from './echart/chart_three'
export default {
  name: 'Index',
  components: {
    chartOne,
    chartTwo,
    chartFour,
    chart_three,
    chartFive,
    chartSix,
    chartSeven,
    chartEight,
    chartNine
  },
  computed:{
    roles() {
      return this.$store.getters.roles[0]
    }
  },
  data(){
    return{

    }
  }
}
</script>

<style scoped>
  .juli {
    margin-top: 15px;
  }
  .main_container {
    width: 100%;
    /*height: 650px;*/
    background-color: white;
  }
  .item_content {
    width: 100%;
    height: 130px;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    /*border-bottom-style: solid;*/
    /*border-bottom-color: #bcbcbc;*/
    /*border-bottom-width: 1px;*/
  }
  .item {
    margin-top: 15px;
    /*padding-top: 10px;*/
    height: 100px;
    width: 250px;
    border-style: solid;
    border-width: 1px;
    border-color: #d7d7d7;
  }
  .item span {
    display: block;
    height: 100px;
    line-height: 100px;
    float: left;
    margin-left: 10px;
    font-size: 14px;
  }
  .shuzi {
    display: block;
    height: 100px;
    line-height: 100px;
    float: right;
    margin-right: 25px;
    font-size: 25px;
  }
  .zi_border {
    border-top-width: 2px;
    border-top-color: #d45cf9;
  }
  .lan_border {
    border-top-width: 2px;
    border-top-color: #57d8f9;
  }
  .hong_border {
    border-top-width: 2px;
    border-top-color: #f93f49;
  }
  .lv_border {
    border-top-width: 2px;
    border-top-color: #85ec76;
  }
  .block {
    text-align: center;
  }
</style>

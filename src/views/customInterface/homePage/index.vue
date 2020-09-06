<template>
  <div class="app-container">
    <div>
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
        </div>
      </el-card>
    </div>
  </div>
</template>

<script>
import chartOne from '@/views/customInterface/homePage/echart/chart_one'
import chartTwo from '@/views/customInterface/homePage/echart/chart_two'
export default {
  name: 'Index',
  components: {
    chartOne,
    chartTwo
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

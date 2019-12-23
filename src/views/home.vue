<template>
  <div class="cover">
    <div class="topBanner">
      <span class="top_logo">HAD服务器资源管理系统</span>
      <ul class="handleArea">
        <li>
          <span class="top_span_bg"></span>
          <span>导入</span>
        </li>
        <li>
          <span class="top_span_bg"></span>
          <span>导出</span>
        </li>
        <li>
          <span class="top_span_bg"></span>
          <span>工具</span>
        </li>
        <li>
          <span class="top_span_bg"></span>
          <span>图表</span>
        </li>
        <li>
          <span class="top_span_bg"></span>
          <span>退出</span>
        </li>
      </ul>
    </div>
    <div class="centerInfo">
      <div class="ci_left" :class="{close:isClose}">
        <div class="cil_top">
          <span>查询数据</span>
          <el-divider direction="vertical"></el-divider>
          <span class="close" @click="closeSidebar">
            <i class="el-icon-d-arrow-left"></i> 隐藏
          </span>
        </div>
        <!-- 查询区域 -->
        <div class="queryArea">
          <div class="queryItem">
            <span class="queryTitle">按环境查询：</span>
            <el-select v-model="envirValue" placeholder="请选择">
              <el-option
                v-for="item in envirList"
                :key="item.value"
                :label="item.label"
                :value="item.value"
              ></el-option>
            </el-select>
          </div>
          <div class="queryItem">
            <span class="queryTitle">按录入时间查询：</span>
            <el-date-picker
              v-model="importDate"
              type="daterange"
              range-separator="至"
              start-placeholder="开始日期"
              end-placeholder="结束日期"
            ></el-date-picker>
          </div>
          <div class="queryItem">
            <span class="queryTitle">按所属部门查询：</span>
            <el-select v-model="sectionValue" placeholder="请选择">
              <el-option
                v-for="item in sectionList"
                :key="item.value"
                :label="item.label"
                :value="item.value"
              ></el-option>
            </el-select>
          </div>
          <div class="queryItem">
            <ul>
              <li>
                <el-checkbox v-model="showChoose">显示选中</el-checkbox>
                <span></span>
              </li>
              <li>
                <el-checkbox v-model="allChoose">全选</el-checkbox>
                <span></span>
              </li>
              <li>
                <el-checkbox v-model="deleteChoose">清除选中数据</el-checkbox>
                <span></span>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="ci_right" :class="{close:isClose}">
        <div class="showLeft" :class="{close:isClose}" @click="showSlideBar"><i class="el-icon-d-arrow-right"></i></div>
      </div>
    </div>
    <div class="bottomFoot">
      <div class="bf_left">
        <span>欢迎您，{{user.name}}</span>
        <span>今天是：{{currentDate}}</span>
      </div>
      <div class="bf_right">如有问题请及时联系{{linkMan}}</div>
    </div>
  </div>
</template>

<script type='text/ecmascript-6'>
export default {
  data() {
    return {
      user: {
        name: "方伟"
      },
      currentDate: "",
      linkMan: 13245671587,
      //   查询条件
      envirList: [
        {
          value: "1",
          label: "1"
        }
      ],
      envirValue: "",
      sectionList: [
        {
          value: "1",
          label: "1"
        }
      ],
      sectionValue: "",
      importDate: "",
      showChoose: "",
      allChoose: "",
      deleteChoose: "",
      isClose:false
    };
  },
  methods: {
    //   获取当前时间
    getCurrentDate: function(parm) {
      var date = new Date();
      var fullYear = date.getFullYear();
      var month = date.getMonth() + 1;
      var ms = month < 10 ? "-" + "0" + month : "-" + month;
      var day = date.getDate();
      var ds = day < 10 ? "-" + "0" + day : "-" + day;
      var rs = fullYear + ms + ds;
      //   var time = date.getHours();
      //   if (time < 10) {
      //     rs += " 0" + time;
      //   } else {
      //     rs += " " + time;
      //   }
      //   var minutes = date.getMinutes();
      //   var min = minutes < 10 ? ":0" + minutes : ":" + minutes;
      //   var seconds = date.getSeconds();
      //   var sed = seconds < 10 ? ":0" + seconds : ":" + seconds;
      //   rs += min + sed;
      return rs;
    },
    // 关闭侧边栏
    closeSidebar:function(){
        this.isClose = true
    },
    // 开启侧边栏
    showSlideBar:function() {
        this.isClose = false
    }
  },
  beforeMount: function() {
    this.currentDate = this.getCurrentDate();
  }
};
</script>

<style lang='less' scoped='' type='text/css'>
@import "../css/home.less";
</style>
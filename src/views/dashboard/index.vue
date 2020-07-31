<template>
  <div class="dashboard-container">
    <div class="search-box">
      <span class="title-text">请输入关键字：</span>
      <el-input
        v-model="ipt"
        clearable
        placeholder="请输入关键字,多个关键字用逗号隔开"
        style="width:350px;margin:0 20px 0 10px"
      >
      </el-input>
      <el-button type="primary" icon="el-icon-search">Search</el-button>
    </div>
    <el-divider></el-divider>
    <div class="content-box">
      <p class="each-item">
        赌注中国
        谁在做空中国概念股_科普_合肥：安徽人民出版社_2013.07_245_13318042.pdf
        <span class="each-item-icon">
          <el-button
            size="mini"
            type="primary"
            icon="el-icon-edit"
            @click="copy(123)"
            >复制文本</el-button
          >
        </span>
      </p>
      <p class="each-item">
        赌注中国
        谁在做空中国概念股_科普_合肥：安徽人民出版社_2013.07_245_13318042.pdf<span
          class="each-item-icon"
          ><el-button  class="btn" size="mini" type="primary" icon="el-icon-edit"
            >复制文本</el-button
          ></span
        >
      </p>
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "Dashboard",
  computed: {
    ...mapGetters(["name"])
  },
  data() {
    return{
      ipt: ""
    }
  },
  methods:{
    copy(value){
    const el = document.createElement(
        "textarea"
      );
      el.value = value;
      el.setAttribute("readonly", "");
      el.style.position = "absolute";
      el.style.left = "-9999px";
      document.body.appendChild(el);
      el.select();
      document.execCommand("copy");
      document.body.removeChild(el);
      this.$message.success(
        "已复制到剪切板",
        1.5
      );
    },
  }
};
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 18px;
    line-height: 46px;
  }
}
.search-box {
  margin: 0 auto;
  width: 60%;
}
.content-box {
  margin-top: 50px;
  overflow: hidden;
  overflow-y: auto;
}
.title-text {
  color: #666;
  font-size: 18px;
}
.each-item {
  width: 100%;
  padding-bottom: 5px;
  border-bottom: 1px solid #d7dae2;
}
.each-item-icon {
  margin-left: 42%;
  margin-top: -35px;
}
</style>

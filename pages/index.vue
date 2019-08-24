<template>
  <div class="container">
    <!-- 轮播图 -->
    <el-carousel :interval="3000" arrow="always">
      <el-carousel-item v-for="(item,index) in imgList" :key="index">
        <div
          class="barner-img"
          :style="`
            background:url(${$axios.defaults.baseURL + item.url}) center center no-repeat;
            background-size:contain contain; 
            `"
        ></div>
      </el-carousel-item>
    </el-carousel>
    <!-- 搜索区域 -->
    <div class="serch-content">
      <div class="serch-bar">
        <!-- 菜单 -->
        <div class="navs">
          <el-row type="flex" class="tab-btn">
            <span
              v-for="(item,index) in tabs"
              :key="index"
              :class="{ active: current === index }"
              @click="handlclick(index)"
            >
              <i>{{item.title}}</i>
            </span>
          </el-row>
        </div>
        <!-- 搜索 -->
        <el-row type="flex" align="middle" class="search-input">
          <input :placeholder="tabs[current].placeholder" />
          <i class="el-icon-search"></i>
        </el-row>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      // 轮播图
      imgList: [],
      //
      current: 0,
      // 搜索栏tabs
      tabs: [
        { title: "攻略", placeholder: "请输入搜索攻略" },
        { title: "酒店", placeholder: "请输入酒店名" },
        { title: "机票", placeholder: "" }
      ]
    };
  },
  // 方法
  methods: {
    handlclick(index) {
      if (index === 2) {
        this.$router.push("/air");
      }
      this.current = index;
    }
  },
  // 钩子函数
  mounted() {
    // 请求轮播图接口;
    this.$axios({
      url: "/scenics/banners"
    }).then(res => {
      console.log(res);
      // cdataonst  = res.data.data;
      this.imgList = res.data.data;
    });
  }
};
</script>

<style lang="less" scoped>
.container {
  min-width: 1000px;
  position: relative;
  /deep/ .el-carousel__container {
    height: 700px;
  }

  .barner-img {
    width: 100%;
    height: 100%;
  }
  // 搜索区域
  .serch-content {
    position: absolute;
    left: 50%;
    top: 45%;
    width: 1000px;
    z-index: 9;
    margin-left: -500px;
    border-top: 1px transparent solid;
    .serch-bar {
      width: 552px;
      margin: 0 auto;
      //tab
      .navs {
        .tab-btn {
          .active {
            &::after {
              background: #eee;
            }
            i {
              color: #333;
            }
          }
          span {
            width: 82px;
            height: 36px;
            display: block;
            position: relative;
            margin-right: 8px;
            cursor: pointer;

            i {
              position: absolute;
              z-index: 2;
              display: block;
              width: 100%;
              height: 100%;
              line-height: 30px;
              text-align: center;
              color: #fff;
            }
            &:after {
              width: 15px;
              height: 15px;
              position: absolute;
              left: 0;
              top: 0;
              display: block;
              content: "";
              width: 100%;
              height: 100%;
              border: 1px rgba(255, 255, 255, 0.2) solid;
              border-bottom: none;
              transform: scale(1.1, 1.3) perspective(0.7em) rotateX(2.2deg);
              transform-origin: bottom left;
              background: rgba(0, 0, 0, 0.5);
              border-radius: 1px 2px 0 0;
              box-sizing: border-box;
            }
          }
        }
      }
    }
    // 搜索input
    .search-input {
      width: 450px;
      height: 46px;
      background-color: #fff;
      border-radius: 0 4px 4px 4px;
      border: 1px rgba(255, 255, 255, 0.2) solid;
      border-top: none;
      box-sizing: unset;
      input {
        outline: none;
        border: 0;
        height: 20px;
        padding: 13px 15px;
        font-size: 16px;
      }
      .el-icon-search {
        margin-left: 100px;
        font-weight: 600;
        cursor: pointer;
        font-size: 22px;
        padding: 0 10px;
      }
    }
  }
}
</style>

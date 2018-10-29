<template>
  <section class="container">
    <div class='box'>
      <div class='header'>
        <div>
          <div class='left'>
            <el-autocomplete v-model="state4" :fetch-suggestions="querySearchAsync" placeholder="请输入内容" @select="handleSelect"></el-autocomplete>
          </div>
          <div class='right'>
            <el-button type="text">登录</el-button>
            <el-button type="text">注册</el-button>
          </div>
        </div>
      </div>

      <div class='nav'>
        <el-carousel indicator-position="outside">
          <el-carousel-item v-for="item in 4" :key="item">
            <h3>{{ item }}</h3>
          </el-carousel-item>
        </el-carousel>
      </div>

      <div class='content'>
        <div class='left'>

          <div v-for="(o, index) in 10" :key="o" class='book-list'>
            <el-card :body-style="{ padding: '0px' }">
              <img src="http://element-cn.eleme.io/static/hamburger.50e4091.png" class="image">
              <div style="padding: 14px;">
                <span>好吃的汉堡</span>
                <div class="bottom clearfix">
                  <div class="time">{{ currentDate }}</div>
                  <div class="time">浏览量：1000</div>
                </div>
              </div>
            </el-card>
          </div>

        </div>
        <div class='right'>

          <el-card class="box-card">
            <div slot="header" class="clearfix">
              <span>公告</span>
            </div>
            <div v-for="o in 4" :key="o" class="text item">
              {{'公告 ' + o }}
            </div>
          </el-card>
        </div>
      </div>

      <div class='footer'>

      </div>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  data() {
    return {
      state4: '',
      currentDate: new Date()
    }
  },
  methods: {
    querySearchAsync(queryString, cb) {
      // var restaurants = this.restaurants
      // var results = queryString
      //   ? restaurants.filter(this.createStateFilter(queryString))
      //   : restaurants
      // clearTimeout(this.timeout)
      // this.timeout = setTimeout(() => {
      //   cb(results)
      // }, 3000 * Math.random())
    },
    handleSelect(item) {
      console.log(item)
    }
  }
}
</script>


<style  lang='scss'>
.box {
  .header {
    height: 80px;
    background: #f2f2f2;
    border-bottom: 1px solid #e5e5e5;
    line-height: 80px;
    overflow: hidden;
    & > div {
      width: 1200px;
      margin: 0 auto;
      span {
        float: right;
      }
      .left {
        float: left;
      }
      .right {
        float: right;
      }
    }
  }

  .nav {
    .el-carousel__container {
      height: 400px;
    }
    .el-carousel__item h3 {
      color: #475669;
      font-size: 18px;
      opacity: 0.75;
      line-height: 300px;
      margin: 0;
    }

    .el-carousel__item:nth-child(2n) {
      background-color: #99a9bf;
    }

    .el-carousel__item:nth-child(2n + 1) {
      background-color: #d3dce6;
    }
  }

  .content {
    width: 1200px;
    margin: 0 auto;
    display: flex;
    .left {
      flex: 1;
      .book-list{
        height: 350px;
        width: 270px;
        float: left;
        margin: 0 20px 50px 0;
      }
      .time {
        font-size: 13px;
        color: #999;
        margin-bottom: 10px;
      }

      .bottom {
        margin-top: 13px;
        line-height: 12px;
      }


      .image {
        width: 100%;
        display: block;
      }

      .clearfix:before,
      .clearfix:after {
        display: table;
        content: '';
      }

      .clearfix:after {
        clear: both;
      }
    }
    .right {
      width: 300px;
    }
  }

  .footer {
    height: 300px;
    background: #f2f2f2;
    border-top: 1px solid #e5e5e5;
  }
}
</style>

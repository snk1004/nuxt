<template>
  <div class="mine">
    mine
  </div>
</template>

<script>

export default {
  data(){
    return {
      tabList: [
        {"name":"新人专享","id":0},
        {"name":"乳品","id":1},
        {"name":"熟食","id":2},
        {"name":"水果","id":3},
        {"name":"零食","id":4}
      ],
      tabBtn: 0,
      bannerList: [
        {"url":"//image.suning.cn/uimg/aps/material/155564639768157132.jpg?format=_is_1242w_610h","id":0},
        {"url":"//image.suning.cn/uimg/aps/material/155566537056226188.jpg?format=_is_1242w_610h","id":1},
        {"url":"//image.suning.cn/uimg/aps/material/155583237230800958.jpg?format=_is_1242w_610h","id":2},
      ]
    }
  },
  components: {
    
  },
  methods: {
    changeTab(ind){
      this.tabBtn = ind
    }
  }
}
</script>

<style>
/* 公共样式 */
.active{
  color: #f14f5e!important;
  border-bottom: 1.5px solid #f14f5e!important;
}
html,body,.wrap{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}
header{
  width: 100%;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  padding: 0 15px;
  box-sizing: border-box;
}
.head-left .country{
  color: #f14f5e;
  font-weight: bold;
}
.head-right{
  position: relative;
}
.head-right input{
  height: 30px;
  border-radius: 15px;
  border: 1px solid #ddd;
  padding-left: 30px;
}
.glass{
  position: absolute;
  top: 5px;
  left: 10px;
  color: #666;
}
.tab{
  width: 100%;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  padding: 0 15px;
  box-sizing: border-box;
}
.tab span{
  border-bottom: 1.5px solid #fff;
  height: 35px;
  line-height: 35px;
  display: inline-block;
}
/* 轮播 */
.banner{
  width: 100%;
}
.banner img{
  width: 100%;
}
.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n+1) {
  background-color: #d3dce6;
}
.sps{
  width: 100%;
  height: 50px;
  display: flex;
  align-items: center;
  font-size: 14px;
  color: #666;
  justify-content: space-around;
}
/* 优惠券 */
.coupon{
  width: 100%;
}
.coupon img{
  width: 100%;
}
/* 路由 */
footer{
  width: 100%;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 15px;
  box-sizing: border-box;
  position: fixed;
  bottom: 0;
}
</style>

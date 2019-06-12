<template>
  <div class="wrap">
    <header>
      <div class="head-left">
        <span class="country">全国送</span>
        <span>南阳人民...<i class="el-icon-arrow-down"></i></span>
      </div>
      <div class='head-right'>
        <span class="glass"><i class="el-icon-search"></i></span>
        <input type="text" placeholder="搜索">
      </div>
    </header>
    <section>
      <div class="tab">
        <span :class="tabBtn===item.id?'active':''" v-for="item in tabList" :key="item.id" @click="changeTab(item.id)">{{item.name}}</span>
        <span><i class="el-icon-arrow-down"></i></span>
      </div>
      <div class="banner">
        <div class="block">
          <el-carousel height="185px">
            <el-carousel-item v-for="item in bannerList" :key="item.id">
              <img :src="item.url" alt="">
            </el-carousel-item>
          </el-carousel>
        </div>
      </div>
      <div class="sps">
        <span><i class="el-icon-upload"></i>优鲜严选</span>
        <span><i class="el-icon-goods"></i>安心检测</span>
        <span><i class="el-icon-star-on"></i>赔付保障</span>
      </div>
      <div class="coupon">
        <img src="https://image3.suning.cn/uimg/cms/img/155582824561826142.jpg?from=mobile" alt="">
      </div>
      <div class="shop-box">
        <div class="shop" v-for="item in dataList" :key='item.goods_id'>
          <dd>
            <img :src="item.goods_image_url" alt="">
          </dd>
          <dt>
            <!-- <h3></h3> -->
            <p>{{item.goods_name}}</p>
            <li>
              <span style="color: #FF4500">￥{{item.goods_price}}<strike style="font-size:12px;color:#666;margin-left:5px">￥{{item.goods_marketprice}}</strike></span>
              <div class="cacul">
                <span>-</span>
                <span>{{item.is_own_shop}}</span>
                <span>+</span>
              </div>
            </li>
          </dt>
        </div>
      </div>
    </section>
    <Footer></Footer>
  </div>
</template>

<script>
import Footer from '@/components/footer'
import axios from 'axios'
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
      ],
      dataList: []
    }
  },
  components: {
    Footer
  },
  mounted(){
    this.getData()
  },
  methods: {
    changeTab(ind){
      this.tabBtn = ind
    },
    getData(){
      axios.get('https://www.taokubuy.com/mobile/index.php?act=goods&op=goods_list&b_id=401&page=10&curpage=1&b_id=401')
      .then((res)=>{
        this.dataList = res.data.datas.goods_list
      })
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
  background: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  padding: 0 15px;
  box-sizing: border-box;
  position: fixed;
  top: 0;
  z-index: 99;
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
section{
  width: 100%;
  height: 100%;
  margin: 50px 0;
}
.tab{
  width: 100%;
  height: 50px;
  background: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  padding: 0 15px;
  box-sizing: border-box;
  position: fixed;
  top: 50;
  z-index: 99;
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
  margin-top: 50px;
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
  background: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 35px;
  box-sizing: border-box;
  position: fixed;
  bottom: 0;
}
footer a{
  color: #666;
  text-decoration: none;
  font-size:  12px;
  text-align: center;
}
footer a img{
  width: 22px;
  height: 22px;
}
/* 商品 */
.shop-box{
  width: 100%;
  display: flex;
  flex-direction: column;
}
.shop{
  width: 100%;
  padding: 10px 15px;
  box-sizing: border-box;
  display: flex;
  border-bottom: 5px solid #eee;
}
.shop img{
  width: 100px;
}
.shop dt{
  margin-left: 15px;
  font-size: 14px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.shop dt p{
  font-weight: normal;
  font-size: 12px;
}
.shop dt li{
  display: flex;
  width: 180px;
  justify-content: space-between;
}
.cacul{
  width: 80px;
  height: 45px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.cacul span{
  border: 1px solid #ddd;
  width: 25px;
  height: 25px;
  text-align: center;
  line-height: 21px;
  border-radius: 50%;
  background: #f14f5e;
  color: #fff;
}
.cacul span:nth-child(2){
  background: #fff;
  border: 1px solid #fff!important;
  color: #000;

}
</style>

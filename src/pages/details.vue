<template>
  <div class="detail-wp">
    <div class="detail-left">
      <div class="product-board">
        <img :src="getUrl"  width="90" height="90">
        <ul>
        	<router-link active-class="active" :to="{path:'/details/' + nav.tag}" :key="index" tag="li"  v-for="(nav,index) in detailsNav">{{ nav.title }}</router-link>
        </ul>
      </div>
    </div>
    <div class="detail-right">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
  export default{
    name:"detail",
    data(){
      return{
        detailsNav:[
          {
            title:"数据统计",
            tag:"earth"
          },{
            title:"数据预测",
            tag:"loud"
          },{
            title:"流量分析",
            tag:"car"
          },{
            title:"广告发布",
            tag:"hill"
          }
        ],
        imgUrl: {
          "/details/earth":require("../assets/img/1.png"),
          "/details/loud":require("../assets/img/2.jpg"),
          "/details/car":require("../assets/img/3.jpg"),
          "/details/hill":require("../assets/img/4.jpg")
        }
      }
    },
    computed:{
      getUrl(){
        return this.imgUrl[this.$route.path];
      }
    }
  }
</script>

<style scoped>
.detail-wp{
  width: 1200px;
  margin: 0 auto;
  overflow: hidden;
  padding-top: 20px;
}
.detail-left{
  float: left;
  width: 200px;
  text-align: center;
}
.detail-right{
  float: left;
  width: 980px;
  margin-left: 20px;
}
.product-board{
  background-color: #fff;
  padding: 20px 0;
}
.product-board ul{
  margin-top: 20px;
}
.product-board li{
  text-align: left;
  padding: 10px 15px;
  cursor: pointer;
}
.product-board li.active,.product-board li:hover{
  background-color: #4FC08D;
  color: #fff;
}
.product-board li a{
  display: block;
}
/* .sales-board{
  background: #fff;
}
.sales-board-intro h2{
  font-size: 20px;
  padding: 20px;
}
.sales-board-intro p{
  background: #f7fcff;
  padding: 10px 20px;
  color: #999;
  line-height: 1.8;
}
.sales-board-form{
  padding: 30px 20px;
  font-size: 14px;
}
.sales-board-line{
  clear: both;
  padding-bottom: 20px;
}
.sales-board-line-left{
  display: inline-block;
  width: 100px;
}
.sales-board-line-right{
  display: inline-block;
  width: 75%;
}
.sales-board-des{
  border-top: 20px solid #f0f2f5;
  padding: 15px 20px;
}
.sales-board-des p{
  line-height: 1.6;
}
.sales-board-des h2{
  font-size: 20px;
  padding-bottom: 15px;
}
.sales-board-des h3{
  font-size: 18px;
  font-weight: bold;
  padding: 20px 0 10px 0;
}
.sales-board-des li{
  padding: 5px 0;
}
.sales-board-table{
  width: 100%;
  margin-top: 20px;
}
.sales-board-table th{
  background: #4FC08D;
  color: #fff;
}
.sales-board-table td{
  border: 1px solid #f0f2f5;
  padding: 15px;
} */
</style>

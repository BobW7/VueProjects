<template>
  <div class="sales-board">
    <div class="sales-board-intro">
      <h2>流量分析</h2>
      <p>是指在获得网站访问量基本数据的情况下对有关数据进行统计、分析，从中发现用户访问网站的规律，并将这些规律与网络营销策略等相结合，从而发现目前网络营销活动中可能存在的问题，并为进一步修正或重新制定网络营销策略提供依据。
      当然这样的定义是站在网络营销管理的角度来考虑的，如果出于其他方面的目的，对网站流量分析会有其他相应的解释。</p>
    </div>
    <div class="sales-board-form">
      <div class="sales-board-line">
        <div class="sales-board-line-left">
          购买数量：
        </div>
        <div class="sales-board-line-right">
          <!-- 注意：on-change不可以转换为驼峰 -->
          <!-- <vcounter @on-change="onParamChange('buyNum',$event)"></vcounter> -->
          <Counter @counter="getGoodInfo('counter',$event)" :max="Counter.max" :min="Counter.min"/>
        </div>
      </div>

       <div class="sales-board-line">
        <div class="sales-board-line-left">
          产品类型：
        </div>
        <div class="sales-board-line-right">
          <DownMenu @downmenu="getGoodInfo('downmenu',$event)" :DownData="DownMenu" />
        </div>
      </div>

      <div class="sales-board-line">
        <div class="sales-board-line-left">
          有效时间：
        </div>
        <div class="sales-board-line-right">
          <Radios @radios="getGoodInfo('radios',$event)" :RadiosContent="Radios" />
        </div>
      </div>

      <div class="sales-board-line">
        <div class="sales-board-line-left">
          总价：
        </div>
        <div class="sales-board-line-right">
           {{ getTotalPrice }} 元
        </div>
      </div>

      <div class="sales-board-line">
        <div class="sales-board-line-left">

        </div>
        <div class="sales-board-line-right">
           <a class="button" href="#">立即购买</a>
           <a class="button" href="#">加入购物车</a>
        </div>
      </div>
    </div>
    <div class="sales-board-des">
      <h2>产品说明</h2>
      <p>每一个电子商务网站都有一定的内容。那么，到底什么是网站内容呢？从本质上讲，内容是一个网站包含的所有的东西——为用户提供的所有文字、图片以及这个网站上的一切可供用户充分利用的东西。
      像很多网站提供的数据（如产品说明、股票行情）或列表（如连接的入口列表）或可供下载的文件及对这些文件的描述性文字和图片都是内容。</p>
      <h3>用户行为指标</h3>
      <ul>
      	<li>在现实操作中，我们一般会遇到三种情况。第一种，图像本身就是内容必不可少的组成部分，但该类图片一般都是大文件，在设计页面时</li>
      	<li>不可在一个页面上放置多幅图片，可用新开图片窗口的办法解决</li>
      	<li>言万语，所以图像对站点的设计具有重要</li>
      	<li>言万语，所以图像对站点的设计具有重要</li>
      	<li>给广大的计算机用户带来了简单易用的图形界面</li>
      </ul>
      <h3>浏览网站方式</h3>
      <ul>
      	<li>第三方软件或是内置的浏览器程序</li>
      	<li>The Extensible HyperText Markup Language(可扩展</li>
      	<li>言，XHTML是一个基于XML的置</li>
      	<li>所以，本质上说，XHTML是一个</li>
      	<li>了部分XML的强大功能及大多数HTML的简单特性</li>
      </ul>

    </div>
  </div>
</template>

<script>
  import Counter from './components/counter'
  import DownMenu from './components/downMenu'
  import Radios from './components/radios'

  export default{
    name:"car",
    data(){
      return{
        totalPrice:0,
        counter:1,
        downmenu:1,
        radios:1,
        Counter:{
          min:1,
          max:10
        },
        DownMenu:[
          {
          name: '初级版',
          value: 1
          },
          {
          name: '中级版',
          value: 2
          },
          {
          name: '高级版',
          value: 3
          }
        ],
        Radios:[
          {
            title:"1个月",
            value:1
          },{
            title:"3个月",
            value:3
          },{
            title:"半年",
            value:6
          },{
            title:"年费",
            value:12
          }
        ]
      }
    },
    components:{
      Counter,
      DownMenu,
      Radios
    },
    methods: {
     /* getCountNum(data) {
        console.log(data)
      },
      getDownMenu(data) {
        console.log(data)
      },
      getRadios(data) {
        console.log(data)
      } */
      getGoodInfo(key,value){
        // console.log(key,value)
        // console.log(this)
        //this 指向当前组件
        this[key] = value;
        var readyData={
          "counter":this.counter, //默认5元
          "downmenu":this.downmenu, //默认2元
          "radios":this.radios //10元
        };
        // console.log(readData)
        // this.totalPrice = readData.counter * 5 + readData.downmenu * 2 + readData.radios*10;
      }
    },
    computed: {
      getTotalPrice() {
        this.$store.dispatch("updatePrice",this.counter * 5 + this.downmenu * 2 + this.radios*10);
        return this.$store.getters.getTotalPrice;
      },
      getOrder(){
        return this.$store.getters.getOrder;
      }
    }
  }
</script>

<style scoped>
  .buy-dialog-title{
    font-size: 16px;
    font-weight: bold;
  }
  .buy-dialog-btn{
    margin-top: 20px;
  }
  .buy-dialog-table{
    width:100%;
    margin-bottom: 20px;
  }
  .buy-dialog-table td,.buy-dialog-table-th{
    border: 1px solid #e3e3e3;
    text-align: center;
    padding: 5px 0;
  }
  .buy-dialog-table th{
    background: #4FC08D;
    color: #fff;
    border: 1px solid #4FC08D;
  }


  .sales-board{
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
  }
  .button{
    background-color: #4FC08D;
    color: #fff;
    display: inline-block;
    padding: 10px 20px;
    cursor: pointer;
  }
</style>

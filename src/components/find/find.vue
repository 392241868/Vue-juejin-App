<template>
  <div id="find">
    <div class="find-head" @click="selectSearch()">
        <div class="search-container">
          <div class="searchBox">
            <i class="iconfont search_img">&#xe669;</i>
            搜索
          </div>
        </div>
    </div>
    <search ref="search"></search>
    <div class="content-wrapper" ref="contentWrapper">
        <div class="recommend">
        <div class="recommend-content">
            <div v-if="recommends.length" class="slider-wrapper">
                <slider>
                    <div v-for="item in recommends">
                        <a :href="item.linkUrl">
                            <img :src="item.picUrl">
                        </a>
                    </div>
                </slider>
            </div>
        </div>
    </div>
    <div class="hot">
        <div class="hot_item">
            <i class="hot_ic week"></i>
            <span>本周最热</span>
        </div>
        <div class="hot_item">
            <i class="hot_ic collect"></i>
            <span>收藏集</span>
        </div>
        <div class="hot_item">
            <i class="hot_ic activity"></i>
            <span>线下活动</span>
        </div>
        <div class="hot_item">
            <i class="hot_ic zhuanlan"></i>
            <span>专栏</span>
        </div>
    </div>
    <div class="boil">
        <div class="boil_tit" @click="selectBoil()">
            <i class="boil_tit_img"></i>
            沸点
            <div class="right_img"><i class="iconfont">&#xe687;</i></div>
        </div>
        <div class="boil_img">
            <ul id="wp">
                <li @click="selectboildetail(item)" class="boil_img_1" v-for="item in find.boildetail"><img :src="item.image"><span><p>{{item.title}}</p></span></li>
                <!-- <li class="boil_img_2"><span>沸点：你是怎么打发睡前时间的？</span></li>
                <li class="boil_img_3"><span>沸点：程序员最常说的谎言有哪些？</span></li>
                <li class="boil_img_4"><span>沸点：2017 年已经过去一半了，用一句话总结一下上半年</span></li>
                <li class="boil_img_5"><span><p>沸点：你在学习开发的过程中走过哪些弯路？前三名送📚</p></span></li> -->
                <span class="view_all" @click="selectBoil()">查看全部</span>
            </ul>
        </div>
        <boildetail :boildetails="selectedboil" ref="boildetail"></boildetail>
    </div>
    <boil ref="boil"></boil>
    <div class="content">
        <div class="content_head">
            <div class="head_left">热门文章</div>
            <div class="head_right"><i class="iconfont">&#xe77e;</i>定制热门</div>
        </div>
        <div class="content_list">
            <ul>
                <li @click="selectlist(item)" class="cont_list_item" v-for="item in find.content">
                    <div class="list_item_container">
                        <p>{{item.title}}</p>
                        <span>{{item.like}}人喜欢·{{item.author}}·{{item.time}}前</span>
                        <img :src="item.image">
                    </div>
                </li>
            </ul>
        </div>
        <listdetail :list="selectedlist" ref="listdetail"></listdetail>
    </div>
    </div>


  </div>
</template>

<script>
  import Slider from 'base/slider/slider'
  import {getRecommend} from 'api/recommend'
  import {ERR_OK} from 'api/config'
  import BScroll from 'better-scroll'
  import listdetail from 'base/listdetail/listdetail'
  import search from 'base/search/search'
  import boil from 'base/boil/boil'
  import boildetail from 'base/boildetail/boildetail'

  export default {
    data() {
      return {
        recommends: [],
        find: {
          type: Object
        },
        selectedlist: {},
        selectedboil: {}
      };
    },
    props: {

    },
    created() {
      this._getRecommend(),
      this.$http.get('./api/find').then((response) => {
          response = response.body;
          if (response.errno === ERR_OK) {
            this.find = response.data;
          }
      });
    },
    methods: {
      _getRecommend() {
        getRecommend().then((res) => {
          if (res.code === ERR_OK) {
            this.recommends = res.data.slider
          }
        })
      },
      selectlist(item) {
        this.selectedlist = item;
        this.$refs.listdetail.show();
      },
      selectSearch() {
        this.$refs.search.show();
      },
      selectBoil() {
        this.$refs.boil.show();
      },
      selectboildetail(item) {
        this.selectedboil = item;
        this.$refs.boildetail.show()
      }
    },
    components: {
      Slider,
      listdetail,
      search,
      boil,
      boildetail
    }
  }
</script>

<style>
#find {
    overflow: hidden;
    padding-bottom: 48px;
}
.find-head {
    position: relative;
    width: 100%;
    height: 40px;
    background-color: #fff;
    text-align: center;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB;
}
.search-container {
    width: 95%;
    height: 30px;
    padding-top: 5px;
    padding-left: 2.5%;
}
.searchBox {
    width: 100%;
    height: 30px;
    line-height: 30px;
    background-color: #E0E1E5;
    border-radius: 5px;
}
.search_img {
    font-size: 20px;
}
.recommend {
    width: 100%;
    top: 40px;
    bottom: 0;
}
.recommend .recommend-content {
    height: 100%;
    overflow: hidden;
}
.recommend .recommend-content .slider-wrapper {
    position: relative;
    width: 100%;
    overflow: hidden;
}
.hot {
    display: flex;
    width: 100%;
    height: 90px;
    line-height: 100px;
    margin-top: 10px;
    background: #fff;
    color: #2E3135;
}
.hot .hot_item {
    flex: 1;
    text-align: center;
}
.hot_ic {
    display: block;
    height: 50px;
    padding-top: 13px;
}
.hot .hot_item span {
    display: block;
    height: 25px;
    line-height: 20px;
}
.week {
    background: url('./image/hot_1.png') center center no-repeat;
    background-size: 35%;
}
.collect {
    background: url('./image/hot_2.png') center center no-repeat;
    background-size: 35%;
}
.activity {
    background: url('./image/hot_3.png') center center no-repeat;
    background-size: 40%;
}
.zhuanlan {
    background: url('./image/hot_4.png') center center no-repeat;
    background-size: 30%;
}
.boil {
    height: 160px;
    width: 100%;
    margin-top: 10px;
    background-color: #fff;
}
.boil .boil_tit {
    height: 45px;
    line-height: 45px;
    color: #000;
    font-size: 15px;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB;
}
.boil_tit_img {
    display: block;
    float: left;
    width: 24px;
    height: 100%;
    margin-left: 12px;
    margin-right: 5px;
    background: url('./image/boil_point.png') left center no-repeat;
    background-size: 70%;
}
.right_img {
    float: right;
    width: 18px;
    height: 100%;
    margin-right: 10px;
}
.boil .boil_img {
    width: auto;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
}
::-webkit-scrollbar {
    display: none;
}
.boil .boil_img ul {
    height: 130px;
    width: 1050px;
    padding-left: 10px;
    overflow-x: auto;
}
.boil .boil_img ul li {
    position: relative;
    display: inline-block;
    float: left;
    height: 90px;
    width: 180px;
    border-radius: 5px;
    margin: 10px;
    margin-left: 0;
}
.boil .boil_img ul li span {
    position: absolute;
    display: block;
    width: 180px;
    height: 90px;
    border-radius: 5px;
    color: #fff;
    font-size: 15px;
    box-shadow: inset 180px 10px 5px rgba(0,0,0,.4);
}
.boil .boil_img ul li span p {
    position: absolute;
    width: 145px;
    padding-left: 20px;
    padding-right: 15px;
    padding-top: 25px;
    font-size: 15px;
    line-height: 18px;
    overflow:hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 2;
}
.boil_img_1 {
    /* background-image: url(./image/boil_item_1.png); */
    background-repeat: no-repeat;
    background-position: 50%;
    background-size: cover;
}
.boil_img_1 img{
    position: absolute;
    top: 0;
    left: 0;
    height: 90px;
    width: 180px;
    border-radius: 5px;
}
/* .boil_img_2 {
    background-image: url(./image/boil_item_2.png);
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}
.boil_img_3 {
    background-image: url(./image/boil_item_3.png);
    background-repeat: no-repeat;
    background-size: cover;
}
.boil_img_4 {
    background-image: url(./image/boil_item_4.png);
    background-repeat: no-repeat;
    background-size: cover;
}
.boil_img_5 {
    background-image: url(./image/boil_item_5.png);
    background-repeat: no-repeat;
    background-size: cover;
} */
.view_all {
    display: inline-block;
    height: 68px;
    line-height: 95px;
    text-align: center;
    width: 90px;
    padding-top: 20px;
    margin-top: 10px;
    color: #53AAFF;
    font-size: 15px;
    border: 0.5px solid #ccc;
    border-radius: 5px;
    background: url(./image/right3.png) center 12px no-repeat;
    background-size: 40%;
}
.content {
    height: auto;
    background-color: #FFF;
    margin-top: 10px;
}
.content .content_head {
    height: 45px;
    line-height: 45px;
    font-size: 15px;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB;
}
.content .content_head .head_left {
    float: left;
    width: 30%;
    color: #000;
    padding-left: 40px;
    background: url(./image/hot_red.png) 12px center no-repeat;
    background-size: 11%;
}
.content .content_head .head_right {
    float: right;
    width: 30%;
    text-align: right;
    padding-right: 12px;
}
.content .content_head .head_right i{
    margin-right: 5px;
}

.content_list ul{
    display: block;
    height: auto;
}
.content_list .cont_list_item {
    position: relative;
    display: block;
    height: 80px;
    padding-top: 20px;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB;
}
.content_list .cont_list_item .list_item_container {
    padding-left: 12px;
}
.list_item_container p {
    width: 70%;
    color: #000;
    font-size: 16px;
    line-height: 18px;
    padding-top: 2px;
    padding-bottom: 10px;
}
.list_item_container span {
    font-size: 14px;
}

.content_list .cont_list_item  img {
    position: absolute;
    height: 60px;
    width: 60px;
    top: 50%;
    margin-top: -30px;
    right: 12px;
}

</style>

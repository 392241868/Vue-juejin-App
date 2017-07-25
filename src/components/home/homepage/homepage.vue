<template>
  <div class="homepage">
    <div class="hot-recommend">
        <div class="hot-recommend-head">
            <div class="left"><i class="iconfont">&#xe67c;</i>热门推荐</div>
            <div class="right"><i class="iconfont refresh">&#xe6d3;</i><i class="iconfont">&#xe6bf;</i></div>
        </div>
        <div v-for="item in home.recommend">
            <div class="hot-recommend-list" @click="selectlist(item)">
                <div class="recommend-infor">
                    <p>{{item.title}}</p>
                    <div class="recommend-infor-ic">
                        <span><i class="iconfont">&#xe641;</i>{{item.like}}</span>
                        <span><i class="iconfont">&#xe631;</i>{{item.author}}</span>
                        <span><i class="iconfont">&#xe603;</i>{{item.time}}前</span>
                    </div>
                </div>
                <div class="recommend-img">
                    <img :src="item.image">
                </div>
            </div>
        </div>
        <listdetail :list="selectedlist" ref="listdetail"></listdetail>
    </div>
    <newslist ref="newslist"></newslist>
  </div>
</template>

<script>
  import {ERR_OK} from 'api/config'
  import newslist from 'base/newslist/newslist'
  import listdetail from 'base/listdetail/listdetail'

  export default {
    data() {
        return {
          find: {
            type: Object
          },
          home: {
            type: Object
          },
          selectedlist: {}
        };
    },
    props: {

    },
    created() {
      this.$http.get('./api/find').then((response) => {
          response = response.body;
          if (response.errno === ERR_OK) {
            this.find = response.data;
          }
      });
      this.$http.get('./api/home').then((response) => {
          response = response.body;
          if (response.errno === ERR_OK) {
            this.home = response.data;
          }
      });
    },
    methods: {
      selectlist(item) {
        this.selectedlist = item;
        this.$refs.listdetail.show();
      }
    },
    components: {
      newslist,
      listdetail
    }
  }
</script>

<style>
  .homepage {
    height: auto;
    margin-top: 50px;
    overflow: hidden;
  }
  .hot-recommend {
    width: 100%;
    height: auto;
    background: #fff;
    margin-bottom: 10px;
  }
  .hot-recommend .hot-recommend-head {
    width: 100%;
    height: 37px;
    line-height: 37px;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB;
  }
  .hot-recommend-head .left {
    float: left;
    color: #007AFF;
    font-size: 15px;
    padding-left: 10px;
  }
  .hot-recommend-head .left i{
    padding-right: 5px;
    font-size: 15px;
  }
  .hot-recommend-head .right {
    float: right;
    padding-right: 10px;
  }
  .hot-recommend-head .right i {
    padding: 8px 5px 8px 10px;
    font-size: 20px;
    font-weight: 600;
    color: #E0E0E0;
  }
  .hot-recommend .hot-recommend-list {
    position: relative;
    height: 100px;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB;

  }
  .hot-recommend-list .recommend-infor {
    float: left;
    width: 70%;
    padding-top: 20px;
    padding-left: 12px;
  }
  .recommend-infor-ic {
    padding-top: 5px;
  }
  .recommend-infor-ic span {
    display: inline-block;
    height: 14px;
    line-height: 14px;
    padding-right: 5px;
    font-size: 10px;
    color: #E0E0E0;
  }
  .recommend-infor-ic span i {
    font-size: 14px;
  }
  .recommend-infor p {
    color: #000;
    line-height: 20px;
  }
  .hot-recommend-list .recommend-img {
    position: absolute;
    width: 60px;
    height: 60px;
    right: 12px;
    top: 20px;
  }
  .hot-recommend-list .recommend-img img {
    width: 60px;
    height: 60px;
  }
  .hot-recommend-list-2 {
    margin-top: 10px;
  }
</style>

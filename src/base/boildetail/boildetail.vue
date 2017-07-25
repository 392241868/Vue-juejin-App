<template>
  <transition name="move">
    <div v-show="showFlag" class="boildetail">
      <div class="boildetail-head-bg">
        <img :src="boildetails.image">
        <div class="box-shadow-bg"></div>
        <div class="boildetail-head">
          <div class="boildetail-Btn-back" @click="hide"><i class="iconfont">&#xe607;</i></div>
          <div class="boildetail-author-infor">
            <div class="author-img"><img :src="boildetails.author_img" ></div>
            <span>{{boildetails.author}}</span>
          </div>
          <div class="boildetail-fenxiang"><i class="iconfont">&#xe65d;</i></div>
        </div>
        <div class="attend">
          <ul>
              <li class="attend-num"><span><i class="iconfont">&#xe601;</i>{{boildetails.number}}人参加</span></li>
              <li class="attend-img"><img src="./image/1.png"></li>
              <li class="attend-img"><img src="./image/2.png"></li>
              <li class="attend-img"><img src="./image/3.png"></li>
              <li class="attend-img"><img src="./image/4.png"></li>
              <li class="attend-img"><img src="./image/5.png"></li>
              <li class="attend-img"><img src="./image/6.png"></li>
              <li class="attend-img"><img src="./image/7.png"></li>
              <li class="attend-img"><img src="./image/8.png"></li>
              <li class="attend-img"><img src="./image/9.png"></li>
              <li class="attend-img"><img src="./image/10.png"></li>
              <li class="attend-img"><img src="./image/11.png"></li>
              <li class="attend-img"><img src="./image/12.png"></li>
          </ul>
        </div>
      </div>
      <div class="boildetail-main">
        <div class="boildetail-title">{{boildetails.title}}</div>
        <div class="boildetail-content">{{boildetails.content}}</div>
        <div class="boildetail-main-ic">
          <span><i class="iconfont">&#xe603;</i>{{boildetails.time}}前</span>
          <span><i class="iconfont">&#xe666;</i>{{boildetails.read}}</span>
        </div>
      </div>
      <div class="discuss">
        <div class="discuss-head"><span class="left">30条回答</span><span class="zui">最热</span><span class="zui">最新</span></div>
        <div class="discuss-section">
          <div class="discuss-list">
            <div class="discuss-list-head">
              <div class="profile-img"><img src="./image/5.png"></div>
              <div class="profile-name"><p>AlexCheung</p><span>16小时前</span></div>
              <div class="praise"><i class="iconfont">&#xe634;</i>5</div>
            </div>
            <div class="discuss-main">
              可以穿体恤衫了， 可以下河游泳了，可以去捉泥鳅了，可以去偷瓜吃了，可以捉知了喂狼狗了，可以去我姨家吃葡萄了，可以去河边捉蛇玩了，四更天可以捉刚破壳的知了，可以到椿树捉椿蹦蹦，可以看西游记了，可以看还珠格格了，又能尿尿和泥玩了！
            </div>
            <div class="discuss-fx"><i class="iconfont">&#xe6c5;</i><i class="iconfont">&#xe65d;</i></div>
          </div>
        </div>
        <div class="discuss-section">
          <div class="discuss-list">
            <div class="discuss-list-head">
              <div class="profile-img"><img src="./image/3.png"></div>
              <div class="profile-name"><p>大豆比</p><span>8小时前</span></div>
              <div class="praise"><i class="iconfont">&#xe634;</i>4</div>
            </div>
            <div class="discuss-main">
              大家好，我是孙悟空，正在大闹地府，给我打20块，我把你名字从生死簿上划掉，觉得我是骗子的别来。
            </div>
            <div class="discuss-fx"><i class="iconfont">&#xe6c5;</i><i class="iconfont">&#xe65d;</i></div>
          </div>
        </div>
        <div class="discuss-section">
          <div class="discuss-list">
            <div class="discuss-list-head">
              <div class="profile-img"><img src="./image/5.png"></div>
              <div class="profile-name"><p>放下那只猫</p><span>5小时前</span></div>
              <div class="praise"><i class="iconfont">&#xe634;</i>3</div>
            </div>
            <div class="discuss-main">
              不和40℃以下城市的人交朋友，不熟
            </div>
            <div class="discuss-fx"><i class="iconfont">&#xe6c5;</i><i class="iconfont">&#xe65d;</i></div>
          </div>
        </div>
      </div>
      <div class="discuss-input">
        <div class="discuss-input-ic"><i class="iconfont">&#xe65f;</i></div>
        <input type="text" name="" placeholder="我有话说">
        <span>发送</span>
      </div>
    </div>
  </transition>
</template>

<script type="text/ecmascript-6">
  export default {
    data() {
      return {
        showFlag: false
      }
    },
    props: {
      boildetails: {
        type: Object
      }
    },
    watch: {

    },
    methods: {
      show() {
        this.showFlag = true;
      },
      hide() {
        this.showFlag = false;
      }
    },
    components:{
    }
  };
</script>

<style>
.boildetail {
  z-index: 1500;
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  bottom: 0;
  margin-bottom: 50px;
  background: #efeff4;
  overflow-y: auto;
  -webkit-overflow-scrolling: touch;
}
.boildetail-head-bg {
  position: relative;
  width: 100%;
  height: 160px;
}
.boildetail-head-bg img {
  width: 100%;
  height: 160px;
}
.boildetail-head-bg .box-shadow-bg {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 160px;
  box-shadow: inset 15px 160px 5px rgba(0,0,0,.4);
}

.boildetail .boildetail-head {
    position: absolute;
    display: flex;
    top: 0;
    width: 100%;
    height: 40px;
    line-height: 40px;
    /* background-color: #f5f5f7;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB; */
    color: #000;
  }
  .boildetail-head .boildetail-Btn-back {
    float: left;
    height: 100%;
    width: 50px;
    text-align: center;
  }
  .boildetail-Btn-back i {
    transform:rotate(180deg);
    color: #fff;
    font-size: 25px;
    font-weight: 500;
  }
  .boildetail-fenxiang {
    float: right;
    width: 40px;
    height: 100%;
    color: #fff;
  }
  .boildetail-fenxiang i {
    font-size: 25px;
    font-weight: 400;
  }

  .boildetail-author-infor {
    flex: 1;
  }
  .boildetail-author-infor .author-img {
    float: left;
    width: 40px;
    height: 40px;
    line-height: 40px;
  }
  .boildetail-author-infor .author-img img{
    display: block;
    width: 30px;
    height: 30px;
    margin-top: 5px;
    border-radius: 50%;
  }
  .boildetail-author-infor span {
    float: left;
    display: inline-block;
    width: 70px;
    font-size: 15px;
    color: #fff;
  }
  .attend {
    position: absolute;
    bottom: 20px;
    height: 30px;
    width: 100%;
    /* background: #fff; */
  }
  .attend ul {
    font-size: 0;
    padding-right: 22px;
  }
  .attend .attend-num {
    display: inline-block;
    height: 30px;
    width: 120px;
    border-radius: 50px;
    background-color: #FD8306;
    margin-left: 15px;
    color: #fff;
    font-size: 14px;
  }
  .attend .attend-num span {
    position: absolute;
    height: 30px;
    width: 100px;
    line-height: 30px;
    text-align: right;
    color: #fff;
  }
  .attend .attend-num span i {
    padding-right: 8px;
  }
  .attend ul .attend-img {
    display: inline-block;
    height: 30px;
    width: 30px;
    border-radius: 50%;
    background: red;
    margin-left: -12px;
  }
  .attend ul .attend-img  img{
    display: block;
    height: 30px;
    width: 30px;
    border-radius: 50%;
  }
  .boildetail-main {
    padding: 20px 15px;
    background: #fff;
  }
  .boildetail-main .boildetail-title {
    color: #000;
    font-size: 18px;
    line-height: 22px;
    font-weight: 600;
    padding-bottom: 15px;
  }
  .boildetail-main .boildetail-content {
    font-size: 14px;
    line-height: 16px;
    padding-bottom: 15px;
  }
  .boildetail-main-ic span {
    font-size: 12px;
    color: #D5D1D1;
    padding-right: 15px;
  }
  .discuss {
    margin-top: 10px;
    background: #fff;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB;
  }
  .discuss .discuss-head {
    height: 40px;
    line-height: 40px;
    width: 100%;
    box-shadow: inset 0px -1px 1px -1px #A7A7AB;
  }
  .discuss .discuss-head .left {
    float: left;
    margin-left: 15px;
    font-size: 15px;
  }
  .discuss .discuss-head .zui {
    float: right;
    margin-right: 15px;
  }
  .discuss-section {
    padding: 20px 15px 15px;
  }
  .discuss-list .discuss-list-head {
    height: 40px;
  }
  .discuss-list .discuss-list-head .profile-img {
    float: left;
    height: 40px;
    width: 40px;
  }
  .discuss-list .discuss-list-head .profile-img img {
    display: block;
    width: 100%;
    height: 100%;
  }
  .discuss-list .discuss-list-head .profile-name {
    float: left;
    margin-left: 10px;
    height: 40px;
  }
  .discuss-list-head .profile-name p {
    color: #0A0E7E;
    line-height: 22px;
  }
  .discuss-list-head .profile-name span {
    font-size: 14px;
    color: #D5D1D1;
  }
  .discuss-list-head .praise {
    float: right;
    height: 40px;
    line-height: 40px;
    width: 60px;
    background: #E2F4F7;
    color: #1DA6EB;
    text-align: center;
  }
  .discuss-list-head .praise i {
    padding-right: 5px;
  }
  .discuss-list .discuss-main {
    padding: 10px 0px 15px 50px;
    color: #000;
  }
  .discuss-list .discuss-fx {
    padding-left: 50px;
  }
  .discuss-list .discuss-fx i {
    font-size: 20px;
    padding-right: 40px;
  }
  .discuss-input {
    z-index: 1550;
    position: fixed;
    display: flex;
    bottom: 0;
    background: #fff;
    width: 100%;
    height: 50px;
    line-height: 50px;
    box-shadow: inset 0px 1px 1px -1px #A7A7AB;
  }
  .discuss-input .discuss-input-ic {
    float: left;
    height: 100%;
    width: 50px;
    text-align: center;
  }
  .discuss-input .discuss-input-ic i {
    color: #ACA9A9;
    font-size: 20px;
  }
  .discuss-input input {
    flex: 1;
    height: 36px;
    margin-top: 7px;
    border: 0.5px solid #DEDCDC;boildetail-main
    border-radius: 5px;
  }
  .discuss-input span {
    display: block;
    float: right;
    width: 50px;
    text-align: center;
    color: #2375E3;
  }
</style>
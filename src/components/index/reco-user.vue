<template>

  <!--右侧推荐关注组件-->
  <div class="attention">
    <!--title-->
    <span class="attention-title">推荐关注</span>
    <!--推荐用户介绍-->
    <div class="attention-user">
      <!--用户列表-->
      <div class="user-list" v-for="(username,index) in usernames">
        <div class="list-left">
          <a class="left-user" href="">{{username}}</a>  <!--用户名 -->
          <a class="left-text" href="">{{introductions[index]}}</a>  <!-- 用户观点-->
        </div>
        <div class="list-right">
          <a href="">
            <img :src="avatars[index]" alt="" class="right-img"> <!-- 用户头像-->
            <div class="img-mask"></div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: '',
    data() {
      return {
        usernames: '',
        introductions: '',
        avatars: ''
      }
    },
    mounted() {
      let that = this;
      let arr1 = [];
      let arr2 = [];
      let arr3 = [];
//      axios.get('api/web_reco_users').then(function (response) {
        axios.get('api/web_reco_users.json').then(function(response){
        let temp = response.data.reco_users;
        for (let i = 0; i < temp.length; i++) {
          arr1.push(temp[i].username);
          arr2.push(temp[i].introduction);
          arr3.push(temp[i].avatar);
        }
        that.usernames = arr1;
        that.introductions = arr2;
        that.avatars = arr3;
      })
    }
  }
</script>

<style scoped>
  @import '../../common/style/marx.min.css';

  a {
    text-decoration: none;
  }

  .attention{
    margin-top: 30px;
  }

  .attention-title{
    font-size: 14px;
    font-weight: 500;
    color: #272c2f;
  }

  .attention-user{
      margin-top: 8px;

  }

  .user-list{
    overflow: hidden;
    border-bottom: 1px solid #e4e4e5;
    padding: 10px 0;
  }

  .list-left{
    float: left;
    width:146px;
  }

  .list-left a{
    display: block;
    font-size: 12px;
  }

  .list-left a:nth-child(1){
    font-weight: 500;
    color: #535557;
  }

  .list-left a:nth-child(2){
    padding-top: 5px;
    line-height: 18px;
    color: #999a9a
  }

  .list-right{
    float:right;
    position: relative;
  }

  .list-right img{
    width: 40px;
    border:1px solid #e4e4e5;
    border-radius:4px;
  }

  .img-mask{
    height: 40px;
    position: absolute;
    top:0;
    left:0;
    bottom:0;
    right:0;
    background-color: rgba(0,0,0,0.3);
    border-radius: 4px;
    display: none;
  }
  .list-right a:hover .img-mask{
    display: block;
  }

  .list-left .left-user:hover{
    color: #999a9a;
  }

  .list-left .left-text:hover{
    color:#535557;
  }





</style>

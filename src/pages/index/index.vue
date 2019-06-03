<template>
<div @click="clickHandle">
<i-notice-bar icon="systemprompt" loop>
今日菜谱!
</i-notice-bar>
<i-grid i-class="no-border">
<i-grid-item @click="goList(item.url)" i-class="no-border" v-for="item in grids" :key="item">
<i-grid-icon>
<image :src="item.img"/>
</i-grid-icon>
<i-grid-label>{{item.type}}</i-grid-label>
</i-grid-item>
</i-grid>
<i-grid i-class="no-border">
<i-row>
<i-grid-item @click="goList(item.url)" i-class="no-border" v-for="item in grids2" :key="item">
<i-grid-icon>
<image :src="item.img"/>
</i-grid-icon>
<i-grid-label>{{item.type}}</i-grid-label>
</i-grid-item>
</i-row>
</i-grid>
<i-panel title="最近更新">
<view class="top-padding">
<view v-for="item in shops" :key='item' class="top-padding">
<i-card :title="item.name" :extra="item.sce" :thumb="item.image">
<view slot="content">{{item.introduction}}</view>
<view slot="footer">{{item.address}}</view>
</i-card>
</view>
</view>
</i-panel>
</div>
</template>

<script>
import card from '@/components/card'

export default {
data () {
return {
grids:[//鲁菜,苏菜
{type:'川菜',img:'/static/grid/1.png',"url":'../list/main?type=1'},
{type:'粤菜',img:'/static/grid/2.png',"url":'../list/main?type=2'},
{type:'鲁菜',img:'/static/grid/3.png',"url":'../list/main?type=3'},
{type:'苏菜',img:'/static/grid/4.png',"url":'../list/main?type=4'},
],
grids2:[
{type:'浙菜',img:'/static/grid/5.png',"url":'../list/main?type=5'},
{type:'闽菜',img:'/static/grid/6.png',"url":'../list/main?type=6'},
{type:'徽菜',img:'/static/grid/7.png',"url":'../list/main?type=7'},
{type:'湘菜',img:'/static/grid/8.png',"url":'../list/main?type=8'},
],
shops:[],
motto: 'Hello miniprograme',
userInfo: {
nickName: 'mpvue',
avatarUrl: 'http://mpvue.com/assets/logo.png'
}
}
},

components: {
card
},

methods: {
goList (url) {
mpvue.navigateTo({ url })
},
goType (type) {
let url = '../list/main?type=' + type
mpvue.navigateTo({ url })
},
created () {
}
},
created () {
const db = wx.cloud.database({ env: 'edux-3d5095' })
db.collection('asx').get().then(
res => {
console.log(res.data)
this.shops = res.data
}
)
}
}
</script>

<style scoped>
div >>> .no-border {
border-width: 0pt;
}
.top-padding {
padding-top: 50rpx;
}
.userinfo {
display: flex;
flex-direction: column;
align-items: center;
}

.userinfo-avatar {
width: 128rpx;
height: 128rpx;
margin: 20rpx;
border-radius: 50%;
}

.userinfo-nickname {
color: #aaa;
}

.usermotto {
margin-top: 150px;
}

.form-control {
display: block;
padding: 0 12px;
margin-bottom: 5px;
border: 1px solid #ccc;
}
.all{
width:7.5rem;
height:1rem;
background-color:blue;
}
.all:after{
display:block;
content:'';
clear:both;
}
.left{
float:left;
width:3rem;
height:1rem;
background-color:red;
}

.right{
float:left;
width:4.5rem;
height:1rem;
background-color:green;
}
</style>

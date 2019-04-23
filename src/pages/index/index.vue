<template>
  <div @click="clickHandle">
    <i-notice-bar icon="systemprompt" loop>
    今日菜谱有重大更新，谢谢光临！
    </i-notice-bar>
    <i-grid i-class="no-border">
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/1.png" />
        </i-grid-icon>
        <i-grid-label>川菜</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/2.png" />
        </i-grid-icon>
        <i-grid-label>粤菜</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/3.png" />
        </i-grid-icon>
        <i-grid-label>鲁菜</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/4.png" />
        </i-grid-icon>
        <i-grid-label>苏菜</i-grid-label>
    </i-grid-item>
    </i-grid>
    <i-grid>
    <i-row>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/5.png" />
        </i-grid-icon>
        <i-grid-label>浙菜</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/6.png" />
        </i-grid-icon>
        <i-grid-label>闽菜</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/7.png" />
        </i-grid-icon>
        <i-grid-label>徽菜</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/8.png" />
        </i-grid-icon>
        <i-grid-label>湘菜</i-grid-label>
    </i-grid-item>
    </i-row>
</i-grid>
    <i-panel title="最近更新">
      <view class="top-padding">
      <view v-for="item in shops" :key='item' class="top-padding">
      <i-card title="{{item.name}}" extra="{{item.sce}}" thumb="cloud://edux-3d5095.6564-edux-3d5095/店铺 (1).png">
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
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
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

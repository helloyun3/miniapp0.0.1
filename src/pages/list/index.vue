<template>
  <div>
    <i-panel title="菜品推荐">
      <view>
        <i-card i-class="split" v-for="item in recommand" :key="item" :extra="item.name" :thumb="item.img">
            <view slot="content">{{item.remark}}</view>
            <view slot="footer">{{item.address}}</view>
        </i-card>
      </view>
    </i-panel>
  </div>
</template>
<script>
import card from '@/components/card'
export default {
  data () {
    return {
      recommand: []
    }
  },
  components: {
card
},
  onLoad (option){
    console.log(option.type)
    this.recommand = require('@/data/' + option.type + '.json')
  },
  created () {
  }
}
</script>

<style scoped>
div >>> .split {
  margin-bottom: 10pt;
}
</style>
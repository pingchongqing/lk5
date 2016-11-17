<template>
  <li class="hr_coupon hr_drawn">
    <p class="hr_drawn_mask" id="lotteryContainer" @mousedown="drawBegin"  @touchstart="drawBegin">
      <span class="hr_txt"></span>
    </p>
    <p class="hr_draw_tips">
      <span class="hr_txt">{{msg}}</span>
    </p>
  </li>
</template>

<script>
import Lottery from '../../static/js/Lottery.js'
export default {
  name: 'draw',
  data () {
    return {
      msg: '刮开神秘奖券'
    }
  },
  mounted: function () {
    var lottery = new Lottery('lotteryContainer', 'rgba(81,81,81,1)', 'color', 211, 85)
    lottery.init(getRandomStr(2), 'text')
    function getRandomStr (len) {
      var text = ''
      var possible = '123456789'
      for (var i = 0; i < len; i++) {
        text += possible.charAt(Math.floor(Math.random() * possible.length))
      }
      return text
    }
  },
  methods: {
    drawBegin: function () {

    }
  }
}
</script>

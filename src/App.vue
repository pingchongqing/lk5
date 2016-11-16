<template>
  <div id="app">
    <!--TIPS:
        要显示第1关，需添加class：hr_l1_1

        要显示第3关，需添加class：hr_l3_1

        要显示第4关第1步，需添加class：hr_l4_1（播放“宝箱展示动画”，并显示“领券界面”）
        要显示第4关第2步，需添加class：hr_l4_2（直接显示“领券界面”）

        要显示“登录”首页，需添加class：hr_login
        要显示“微信扫码进入”首页，需添加class：hr_scan
        要显示“风险用户”首页，需添加class：hr_risk

        要隐藏“剩余奖金”，需添加class：hr_hide_money
    -->
    <div class="hr_wrap con hr_show_in" v-bind:class="wrapcls" id="hr_wrap">
        <!--start:公用-->
        <p class="hr_img11 hr_logo"></p>
        <p class="hr_img0 cover hr_bg"></p>
        <p class="hr_img0 hr_banner_bg"></p>
        <p class="hr_img1 hr_tree_l"></p>
        <p class="hr_img1 hr_tree_r"></p>
        <p class="hr_img3 hr_out_banner"></p>
        <div class="hr_img6 hr_banner">
            <div class="hr_content hr0">
                <p class="hr_img9 hr_title hr0"></p>
            </div>
            <div class="hr_content hr1">
                <p class="hr_title hr1">至少要邀请1位好友帮忙哦</p>
            </div>
            <div class="hr_content hr2">
                <p class="hr_title hr2">宝箱成功打开，点击领取神券</p>
            </div>
        </div>

        <!--TIPS:
            默认为“播放”状态，
            要显示“静音”状态，需添加class：hr_off
        -->
        <a class="hr_img2 hr_sound " id="hr_sound"></a>
        <!--end:公用-->

        <!--start:第1关-->
        <div class="cover hr_l1" id="hr_l1">
            <p class="hr_img13 hr_box">
                <span class="hr_img14 cover hr_dark"></span>
            </p>
            <p class="hr_img11 hr_money" style="display: none">
                <span class="hr_val" id="rmnMoney"></span>
            </p>
            <p class="hr_img12 cover hr_mask"></p>
            <p class="hr_img11 hr_risk_tips"></p>
            <a class="hr_img11 hr_btn hr0" v-on:click="hr0clk">
                <span class="hr_img11 hr_btn_txt"></span>
            </a>
            <a class="hr_img11 hr_btn hr1">
                <span class="hr_img11 hr_btn_txt"></span>
            </a>
            <a class="hr_img11 hr_btn hr2">
                <span class="hr_img11 hr_btn_txt"></span>
            </a>
        </div>
        <!--end:第1关-->

        <!--start:第2关-->
        <div class="cover hr_l2" id="hr_l2">
            <div class="cover hr_map_con" id="hr_l2_map_con">
                <div class="hr_img17 hr_map" id="hr_l2_map" >
                    <span class="hr_img15 hr_uav"></span>
                    <a class="hr_img15 hr_map_box" data-id="0" v-on:click="boxclk"></a>
                    <a class="hr_img15 hr_map_box" data-id="1" v-on:click="boxclk"></a>
                    <span class="hr_img15 hr_light1"></span>
                    <span class="hr_img15 hr_light3"></span>
                    <span class="hr_img15 hr_light4"></span>
                    <span class="hr_img15 hr_light5"></span>
                    <span class="hr_img15 hr_balloon0"></span>
                    <a class="hr_img15 hr_map_box" data-id="2" v-on:click="boxclk"></a>
                    <span class="hr_img15 hr_light2"></span>
                    <span class="hr_img15 hr_balloon1"></span>
                    <span class="hr_img15 hr_balloon2"></span>
                    <a class="hr_img15 hr_map_box" data-id="3" v-on:click="boxclk"></a>
                    <span class="hr_img15 hr_snow"></span>
                    <span class="hr_img15 hr_balloon3"></span>
                    <span class="hr_img15 hr_fire"></span>
                    <a class="hr_img15 hr_map_box" data-id="4" v-on:click="boxclk"></a>
                    <span class="hr_img15 hr_snowman"></span>
                    <span class="hr_img15 hr_light0"></span>
                    <span class="hr_img15 hr_ice"></span>
                    <span class="hr_img15 hr_crab"></span>
                    <a class="hr_img15 hr_map_box" data-id="5" v-on:click="boxclk"></a>
                    <span class="hr_img15 hr_balloon5"></span>
                    <span class="hr_img15 hr_balloon6"></span>
                    <span class="hr_img15 hr_balloon4"></span>
                    <a class="hr_img15 hr_map_box" data-id="6" v-on:click="boxclk"></a>
                    <span class="hr_img15 hr_water"></span>
                    <span class="hr_img15 hr_cloud0"></span>
                    <span class="hr_img15 hr_cloud1"></span>
                    <a class="hr_img15 hr_map_box" data-id="7" v-on:click="boxclk"></a>
                    <div class="cover hr_tips" id="hr_l2_map_tips" style="display:none;">
                        <p class="overlay"></p>
                        <p class="hr_img15 middle hr_icon"></p>
                    </div>
                </div>
            </div>
            <div class="hr_box_count" id="hr_l2_box_count">
                <p class="hr_img15 hr_icon"></p>
                <p class="flex_l hr_txt">
                    <span class="hr_times_sign"></span>
                    <span class="hr_val" id="hr_l2_box_count_val"></span>
                </p>
            </div>

            <!--start:第1关奖励弹框-->
                <transition name="fade">
                  <div class="hr_popup hr0" id="hr_l2_popup0" v-show="lev1Show">
                      <p class="overlay"></p>
                      <div class="hr_img16 hr_content">
                          <p class="hr_title">&nbsp;<span id="hr_l2_popup0_title_val">5</span>元启动资金到手！</p>
                          <div class="flex_c hr_coupon">
                              <p class="hr_val_wrap">
                                  <span class="hr_unit">¥</span>
                                  <span class="hr_val" id="hr_l2_popup0_coupon_val">5</span>
                              </p>
                              <p class="hr_tips_wrap">
                                  <span class="hr_cate" id="hr_l2_popup0_coupon_cate">全品类</span>
                                  <span class="hr_cond">满<span id="hr_l2_popup0_coupon_cond_val">20</span>元可用</span>
                              </p>
                          </div>
                          <p class="hr_img15 hr_subtitle"></p>
                          <a class="hr_img11 hr_btn" id="hr_l2_popup0_btn" v-on:click="hrL2clk">
                              <span class="hr_img15 middle hr_btn_txt"></span>
                          </a>
                      </div>
                  </div>
                </transition>

            <!--end:第1关奖励弹框-->

            <!--start:第2关奖励弹框-->
            <transition name="fade">
              <div class="hr_popup hr1" id="hr_l2_popup1" v-show="lev2Show">
                  <p class="overlay"></p>
                  <div class="hr_img16 hr_content">
                      <p class="hr_title">&nbsp;<span id="hr_l2_popup1_title_val">100</span>元奖励金到手！</p>
                      <div class="flex_c hr_coupon">
                          <p class="hr_val_wrap">
                              <span class="hr_unit">¥</span>
                              <span class="hr_val" id="hr_l2_popup1_coupon_val">100</span>
                          </p>
                          <p class="hr_tips_wrap">
                              <span class="hr_cate" id="hr_l2_popup1_coupon_cate">全品类</span>
                              <span class="hr_cond">满<span id="hr_l2_popup1_coupon_cond_val">100</span>元可用</span>
                          </p>
                      </div>
                      <p class="hr_img15 hr_subtitle"></p>
                      <a class="hr_img11 hr_btn" id="hr_l2_popup1_btn" v-on:click="collectBoxes">
                          <span class="hr_img15 middle hr_btn_txt"></span>
                      </a>
                  </div>
              </div>
            </transition>
            <!--end:第2关奖励弹框-->

            <!--start:找到宝箱动画-->
            <transition name="fade">
              <p class="cover hr_big_box_wrap" id="hr_l2_big_box_wrap" v-show="findBox" >
                  <span class="hr_img18 middle hr_big_light" id="hr_l2_big_light"></span>
                  <span class="hr_img9 middle hr_box hr_big_box" id="hr_l2_big_box"></span>
              </p>
            </transition>
            <!--end:找到宝箱动画-->

        </div>
        <!--end:第2关-->

        <!--start:第3关-->
        <div class="hr_l3" id="hr_l3">
            <div class="hr_scene">
                <div class="cover hr_boxes">
                    <p class="hr_img10 hr_circle"></p>
                    <p class="hr_img9 hr_box hr0"></p>
                    <p class="hr_img9 hr_box hr1"></p>
                    <p class="hr_img9 hr_box hr2"></p>
                    <p class="hr_img9 hr_box hr3"></p>
                    <p class="hr_img9 hr_box hr4"></p>
                </div>
            </div>
            <p class="hr_btn_wrap">
                <a class="hr_img9 hr_btn" v-on:click="hrL3clk">
                    <span class="hr_img9 hr_btn_txt" id="shareF"></span>
                </a>
            </p>
        </div>
        <!--end:第3关-->

        <!--start:第4关（领券）-->
        <div class="hr_pack hr_l4">
            <div class="hr_content">
                <ul class="hr_coupons" id="hr_coupons">
                  <li class="flex_c hr_coupon">
                      <p class="hr_border"></p>
                      <p class="hr_val_wrap">
                          <span class="hr_unit">¥</span>
                          <span class="hr_val" id="hr_l2_popup0_coupon_val">5</span>
                      </p>
                      <p class="hr_tips_wrap">
                          <span class="hr_cate" id="hr_l2_popup0_coupon_cate">全品类</span>
                          <span class="hr_cond">满<span id="hr_l2_popup0_coupon_cond_val">20</span>元可用</span>
                      </p>
                  </li>
                  <li class="hr_coupon">
                    <p class="hr_border"></p>
                    <p class="hr_val_wrap">
                      <span class="hr_unit">¥</span>
                      <span class="hr_val">100</span>
                    </p>
                    <p class="hr_tips_wrap">
                      <span class="hr_cate">全品类</span>
                      <span class="hr_cond">满100可用</span>
                    </p>
                    <p class="hr_drawn_mask">
                      <a class="hr_txt">hr_drawn_mask</a>
                    </p>
                  </li>
                  <li class="hr_coupon hr_drawn">
                    <p class="hr_drawn_mask">
                      <span class="hr_txt"></span>
                    </p>
                      <p class="hr_draw_tips">
                        <span class="hr_txt">刮开神秘奖券</span>
                      </p>
                  </li>
                </ul>
                <p class="hr_img7 hr_pack_f"></p>
                <p class="hr_img7 hr_rope"></p>
                <a class="hr_img7 hr_use_btn"></a>
            </div>
        </div>
        <!--end:第4关（领券）-->

        <!--start:微信扫码进入-->
        <div class="hr_out">
            <p class="hr_img4 hr_waterlemon"></p>
            <p class="hr_img5 hr_bubble"></p>

            <!--start:“去京东赢好礼”按钮-->
            <a class="hr_img5 hr_btn hr6" id="hr_l1_btns" v-on:click="hrL1clk">
                <span class="hr_img5 hr_btn_txt"></span>
            </a>
            <!--end:“去京东赢好礼”按钮-->
        </div>
        <!--end:微信扫码进入-->

        <!--start:好友列表-->
        <div class="hr_friends_wrap">
            <p class="hr_title">
                已有<span id="fLength">0</span>位好友帮忙
            </p>
            <ul class="hr_friends" id="fiends"></ul>
        </div>
        <!--end:好友列表-->

        <!--start:我的战利品按钮-->
        <p class="hr_prize_btn_wrap">
            <a class="hr_prize_btn">我的战利品</a>
        </p>
        <!--end:我的战利品按钮-->

        <!--start:广告位-->
        <ul class="hr_ads" id="hr_ads"></ul>
        <!--end:广告位-->

        <a class="hr_rule_btn" id="rule">活动规则</a>

        <div class="con hr_rule" style="display:none;" id="ruleContent"><!--start:活动规则-->

<p class="overlay"></p>
<div class="hr_rule_bg">
    <a class="hr_close_rule_btn"></a>
    <div class="hr_rule_content">
        <p class="hr_rule_title">活动规则</p>
        <ol class="hr_rule_list">
            <li>活动时间：2016年11月2日00:00:00-2016年11月12日23:59:59，红包总量有限，抢完即止；抢券成功以优惠券到账为准，优惠券有效期以券面显示为准，逾期券将作废；</li>
            <li>活动方式：用户从手机京东相关入口进入活动。参与活动可获得一张优惠券；在地图中成功找到5个宝箱，可再获得一张优惠券及一个神券礼包；分享活动至微信或朋友圈，分享链接被1位及以上好友点击后，即可打开神券礼包。在微信或朋友圈中帮助好友打开神券礼包也可获得一张优惠券。</li>
            <li>查看红包：
                <ol>
                    <li>1）手机号已绑定京东账号的用户，可在手机京东登录参与活动手机号对应的京东账号，在我的 &gt;优惠券中查看所有优惠券；</li>
                    <li>2）未注册或手机号未绑定京东账号用户，需用领券手机号注册或绑定京东账号，下载/打开手机京东，登录查看获得的优惠券（需在优惠券有效期内用领取红包手机号注册或绑定京东账号，逾期优惠券作废）；</li>
                </ol>
            </li>
            <li>手机号绑定京东账户方法：手机京东&gt;登录&gt;我的&gt;账户管理&gt;账户安全&gt;手机验证；</li>
            <li>优惠券使用规则：红包中优惠券均为京东满减券，购买全品类或限品类商品可用，每张订单仅限使用一张，具体使用规则遵守京东优惠券使用的相关规则；</li>
            <li>修改手机号：在当前页面修改手机号后，页面显示的是旧手机号对应的结果页，再次参与本活动抢到的红包将放入新手机号对应的京东账户中，每个用户每天至多可修改1次手机号；</li>
            <li>其他说明：活动所发红包总量有限，先到先得，抢完为止。活动期间，用户如果出现违规行为（如作弊领取、恶意套取等），京东平台将取消该用户获得红包的资格；</li>
            <li>活动中有任何疑问，可在2016年11月2日00:00:00-2016年11月12日23:59:59登录手机京东--个人中心--在线客服咨询反馈。</li>
            <li>京东保留在法律规定的范围内对上述规则进行解释的权利。</li>
        </ol>
    </div>
</div>

<!--end:活动规则--></div>
    </div>

    <!--start:loading-->
    <p class="loading" id="loading" style="display:none;">
        <span></span>
    </p>
    <!--end:loading-->

    <!--start:toast-->
    <p class="toast" id="toast" style="display:none;">网络开小差啦</p>
    <!--end:toast-->

    <!--start:重试弹框-->
    <div class="retry" style="display:none;" id="retryCon">
        <p class="retry_overlay"></p>
        <div class="retry_content">
            <p class="retry_img0 retry_icon"></p>
            <p class="retry_txt">网络开小差了，重试一下</p>
            <p class="retry_btn_wrap">
                <a class="retry_img0 retry_btn" id="retry_btn">
                    <span class="retry_btn_txt">重试</span>
                </a>
            </p>
        </div>
    </div>
    <!--end:重试弹框-->

    <div id="toastTips" style="display: none;" class="toastTips"></div>
  </div>
</template>

<script>
import Hello from './components/Hello'

export default {
  name: 'app',
  components: {
    Hello
  },
  data: function () {
    return {
      wrapcls: 'hr_scan',
      lev1Show: false,
      lev2Show: false,
      findBox: false,
      boxnum: 0
    }
  },
  methods: {
    hr0clk: function () {
      this.wrapcls = 'hr_l2_2'
      this.lev1Show = true
    },
    hrL1clk: function () {
      this.wrapcls = 'hr_l1_1'
    },
    hrL2clk: function () {
      this.lev1Show = false
    },
    boxclk: function (e) {
      this.findBox = true
      e.target.className = 'hr_img15 hr_map_box hr_hide'
      setTimeout(() => {
        this.findBox = false
      }, 1500)
      this.boxnum++
      if (this.boxnum === 5) {
        this.lev2Show = true
      }
    },
    collectBoxes: function () {
      this.lev2Show = false
      this.wrapcls = 'hr_l3_1'
    },
    hrL3clk: function () {
      this.wrapcls = 'hr_l4_1'
      setTimeout(() => {
        this.wrapcls = 'hr_l4_2'
      }, 1000)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

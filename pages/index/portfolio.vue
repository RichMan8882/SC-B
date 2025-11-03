<script lang="ts" setup>
const { t } = useI18n()
const siteStore = useSiteStore()
const router = useRouter()
</script>

<template>
  <div class="cont">
    <headerTop></headerTop>
    <div class="portfolio">
      <div class="left">
        <div class="scontent">
          <h6>600+</h6>
          <p>次 IPO 及并购退出</p>
        </div>
      </div>
      <div class="right">
        <div class="portfolio-banner">
          <h2 class="title">被投企业</h2>
        </div>
        <div class="portfolio-content">
          <div class="front-block">
            <h2>投资领域</h2>
            <p>我们的投资主要集中在以下最具活力与成长性的行业：</p>
            <div class="sectors">
              <div class="box tmt"><span>消费科技</span></div>
              <div class="box healthcare"><span>大健康</span></div>
              <div class="box consumer"><span>消费</span></div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <FooterBottom></FooterBottom>
  </div>
</template>

<style scoped lang="sass">
.portfolio
    position: relative
    margin-top: 96px
    .left
        position: absolute
        top: 0
        width: 300px
        bottom: 0
        background-color: #333333
        h6
            font-weight: 100
            padding-bottom: 1px
            font-size: 3.75em
            line-height: 120%
            text-align: center
            margin-top: 59px
            color: #fff
            border-bottom: 1px solid #222
        p
            font-size: 1em
            line-height: 150%
            text-align: center
            margin: 10px 0
            color: #bcbcbc
    .right
        padding-left: 300px
        .portfolio-banner
            height: 300px
            transition: background-image 0.3s ease
            position: relative
            background-size: cover
            background-position: right center
            background-repeat: no-repeat
            background-image: url(@/assets/images/portfolio/portfolio-1600.jpg)
            h2.title
                padding-left: 8%
                padding-right: 8%
                text-align: left
                font-weight: normal
                padding-top: 80px
                color: #fff
                font-size: 3.75em
                line-height: 120%
                text-shadow: 0 3px 2px rgba(0, 0, 0, 0.25)
                margin-bottom: 10px
                text-transform: none
        .portfolio-content
            padding: 30px 8% 60px
            min-height: 400px
            .front-block
                padding-top: 30px
                h2
                    margin-bottom: 30px
                    color: #2d292a
                    font-size: 1em
                    line-height: 150%
                    padding-bottom: 10px
                    position: relative
                    font-weight: bold
                    &::after
                        width: 46px
                        display: block
                        background: #bc171d
                        overflow: hidden
                        content: ""
                        height: 2px
                        position: absolute
                        bottom: 0
                        left: 0
</style>

<script lang="ts" setup>
const { t } = useI18n()
const siteStore = useSiteStore()
const router = useRouter()
const toUrl = (url) => {
  window.open(url)
}
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
              <div class="box tmt"><img src="@/assets/images/portfolio/pf1.svg" alt=""><span>消费科技</span></div>
              <div class="box healthcare"><img src="@/assets/images/portfolio/pf2.svg" alt=""><span>大健康</span></div>
              <div class="box consumer"><img src="@/assets/images/portfolio/pf3.svg" alt=""><span>消费</span></div>
            </div>
            <br>
            <br>
            <h2>部分被投企业</h2>

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
    margin-top: 74px
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
                padding-top: 0px
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
                p
                  color: rgb(102, 102, 102)
                  font-size: 14px
                .sectors
                  display: flex
                  background-color: #f4f6f7
                  .box
                    display: flex
                    align-items: center
                    height: 100px
                    padding: 18px
                    gap:18px
                    font-size: 14px
                    flex: 1
                    &:nth-child(2)
                      border-inline: 1px solid rgba(0, 0, 0, 0.1)
                      
                    img
                      max-width: 100px
                      height: 100%
                      object-fit: cover

.section4-content
  margin: 0 auto 100px
  @media (max-width: 1200px)
    width: 100%
    padding: 0 20px
  .section4-content-title
    margin-bottom: 40px
    text-align: center
    opacity: 0
    transform: scale(.5)
    transition: all .6s ease-in-out
    h2
      font-size: 38px
      font-weight: 600
      line-height: 40px
      margin-bottom: 20px
    p
      font-size: 14px
      line-height: 1.5
  .section4-content-items
    margin-top: 45px
    display: grid
    grid-template-columns: repeat(4, 1fr)
    background-color: #eaebed
    gap: 1px
    justify-content: space-between
    @media (max-width: 1200px)
      grid-template-columns: repeat(3, 1fr)
    @media (max-width: 768px)
      grid-template-columns: repeat(1, 1fr)
    .item
      position: relative
      overflow: hidden
      padding: 1rem 1rem
      transition: all .3s ease-in-out
      background-color: #f5f6f8
      &:hover
        // background: #7354ff
        background-color: #edeef0
        .icon
          fill: #fff
      .icon
        margin: 0 auto
        width: 3.75rem
        height: 3.75rem
        // fill: #7354ff
      img
        width: 66px
        height: 66px
        object-fit: cover
        margin-bottom: 10px
        border-radius: 5px

      h3
        font-size: 18px
        font-weight: 600
        margin-block: 10px
@media (max-width: 768px)
  .left
    display: none
  .right
    padding-inline-start: 0 !important
    .portfolio-content
      padding: 40px 20px !important
      .section4-content
        margin-bottom: 0
        padding: 0
  .sectors
    flex-direction: column
    .healthcare
      border-inline: none !important
      border-block: 1px solid rgba(0, 0, 0, 0.1) !important
</style>

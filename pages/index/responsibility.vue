<script lang="ts" setup>
const { t } = useI18n()
const siteStore = useSiteStore()
const router = useRouter()
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue'

// Import Swiper styles
import 'swiper/css'

import 'swiper/css/scrollbar'

// import required modules
import { Scrollbar, Autoplay } from 'swiper/modules'

const modules = [Scrollbar, Autoplay]
</script>

<template>
  <div class="cont">
    <headerTop></headerTop>
    <div class="portfolio">
      <div class="right">
        <div class="portfolio-banner">
          <h2 class="title">企业责任</h2>
        </div>
        <div class="portfolio-content">
          <div class="front-block">
            <h2>愿景</h2>

            <div class="sectors">
              <h4>通过投资环境、社会及治理，提升人们的生活质量。</h4>
              <p>自 1993 年扎根中国以来，我们一直坚信社会责任投资是确保 IDG 资本可以实现长期价值创造的前提。</p>
            </div>
            <br>
            <br>
            <h2>新能源投资的社会贡献</h2>
            <div class="portfolio-list">
              <div class="esg-gx-top">
                <div class="esg-gx-top-left"><img alt="" src="@/assets/images/responsibility/esg-img1.jpg"></div>
                <div class="esg-gx-top-right">
                  <ul>
                    <li>
                      <h4><span>20</span> 年</h4>
                      <p>深耕新能源领域</p>
                    </li>
                    <li>
                      <h4><span>180</span> 亿</h4>
                      <p>在新能源领域已投资约 180 亿人民币<br>
                        （截止至 2024 年 12 月）</p>
                    </li>
                  </ul>
                </div>
              </div>
              <div class="esg-gx-bottom">
                <swiper :modules="modules" class="mySwiper" :autoplay="{
                  delay: 3000,
                  disableOnInteraction: false
                }" :slides-per-view="2">
                  <swiper-slide>
                    <div class="esg-list">
                      <div class="year current">2024 <span><img alt=""
                            src="@/assets/images/responsibility/icon-up.svg"></span></div>
                      <h4><span>2147</span> 万吨</h4>
                      <div class="info">二氧化碳减排</div>
                    </div>
                    <div class="esg-section">
                      <h3>这些碳排放相当于：</h3>
                      <div class="esg-section-list">
                        <ul>
                          <li><img alt="" src="@/assets/images/responsibility/icon-tree.svg"><span>39
                              亿株樟子松每年所减少的碳排放量</span></li>
                          <li><img alt="" src="@/assets/images/responsibility/icon-dian.svg"><span>3749
                              万人年生活用电量的碳排放量</span></li>
                        </ul>
                      </div>
                    </div>
                  </swiper-slide>
                  <swiper-slide>
                    <div class="esg-list">
                      <div class="year">2023</div>
                      <h4><span>1509</span> 万吨</h4>
                      <div class="info">二氧化碳减排</div>
                    </div>
                    <div class="esg-section">
                      <h3>这些碳排放相当于：</h3>
                      <div class="esg-section-list">
                        <ul>
                          <li><img alt="" src="@/assets/images/responsibility/icon-tree.svg"><span>27
                              亿株樟子松每年所减少的碳排放量</span></li>
                          <li><img alt="" src="@/assets/images/responsibility/icon-dian.svg"><span>2738
                              万人年生活用电量的碳排放量</span></li>
                        </ul>
                      </div>
                    </div>
                  </swiper-slide>
                  <swiper-slide>
                    <div class="esg-list">
                      <div class="year">2022</div>
                      <h4><span>1153</span> 万吨</h4>
                      <div class="info">二氧化碳减排</div>
                    </div>
                    <div class="esg-section">
                      <h3>这些碳排放相当于：</h3>
                      <div class="esg-section-list">
                        <ul>
                          <li><img alt="" src="@/assets/images/responsibility/icon-tree.svg"><span>2117
                              万人年生活用电量的碳排放量</span></li>
                          <li><img alt="" src="@/assets/images/responsibility/icon-dian.svg"><span>437
                              万辆乘用车一年的碳排放量</span></li>
                        </ul>
                      </div>
                    </div>
                  </swiper-slide>
                  <swiper-slide>
                    <div class="esg-list">
                      <div class="year">2021</div>
                      <h4><span>647</span> 万吨</h4>
                      <div class="info">二氧化碳减排</div>
                    </div>
                    <div class="esg-section">
                      <h3>这些碳排放相当于：</h3>
                      <div class="esg-section-list">
                        <ul>
                          <li><img alt="" src="@/assets/images/responsibility/icon-tree.svg"><span>21
                              亿株樟子松每年减少的碳排放量</span></li>
                          <li><img alt="" src="@/assets/images/responsibility/icon-dian.svg"><span>北京每年近 16.4%
                              用电的碳排放量</span></li>
                        </ul>
                      </div>
                    </div>
                  </swiper-slide>
                </swiper>

                <div class="esg-section gray-box">
                  <h3>计算方法：</h3>
                  <p>我们选取新能源领域，包括太阳能发电、新能源车、燃料电池、储能等行业的公司，深入分析其参与贡献的避免碳排放量。调查显示，新能源领域的投资组合公司以及其整个价值链的避免碳排放量从 2021年的
                    647
                    万吨 CO2e 增加至 2024年的2147万吨 CO2e，期间CAGR达到近 50%。上述显著增长主要归因于投资组合企业业绩表现的提升及经营规模的扩大。</p>
                </div>
              </div>
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
    margin-top: 74px
    .right
        .portfolio-banner
            height: 300px
            transition: background-image 0.3s ease
            position: relative
            background-size: cover
            background-position: right center
            background-repeat: no-repeat
            background-image: url(@/assets/images/responsibility/rp-bg.jpg)
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
                  background: url(@/assets/images/responsibility/rpsby.jpg) no-repeat center / 100% 100%
                  h4
                    color: #fff
                  h4,p
                    padding: 40px 20px
                  p
                    text-align: right
                  @media (max-width: 768px)
                    background: #fdf6f7
                    h4
                      color: #fff
                      background-color: #d62434
                    h4,p
                      padding: 15px 20px
                      text-align: left
                    
            .portfolio-list
              background-color: #f5f6f8
.esg-gx 
    background-color: #f5f6f8

.esg-gx-top 
    overflow: hidden
    display: flex

.esg-gx-top-left 
    max-width: 56%
    flex: 0 0 56%
    overflow: hidden

.esg-gx-top-right 
    max-width: 44%
    flex: 0 0 44%
    padding: 0 40px
    display: flex
    flex-direction: column
    justify-content: space-between

.esg-gx-top-right ul 
    height: 100%
    list-style: none
    display: flex
    flex-direction: column

.esg-gx-top-right li 
    flex: 1
    display: flex
    align-items: center
    border-bottom: 1px solid rgba(151,151,151,0.3)

.esg-gx-top-left img 
    width: 100%
    float: left

.esg-gx-top-right li p 
    margin: 0
    font-size: 1em
    line-height: 150%

.esg-gx h4 
    font-size: 14px

.esg-gx h4 span 
    font-size: 3.75em
    line-height: 100%

.esg-gx-top-right h4 
    width: 130px

.esg-list 
    display: flex
    list-style: none
    align-items: center
    gap: 20px

.esg-list .year 
    background-color: #e2e4e8
    height: 30px
    line-height: 30px
    font-size: 1.25em
    padding: 0 10px
    color: #333
    font-weight: 600

.esg-list .year.current 
    background-color: #d62434
    color: #fff

.esg-gx-bottom 
    background: url(@/assets/images/responsibility/esg-bg2.jpg) no-repeat right top
    background-size: cover
    padding: 50px

.info 
    color: #666
    position: relative
    top: 15px
    font-size: 14px

.esg-section 
    padding: 40px 0

.esg-section.gray-box 
    background: rgba(208,211,216,0.08)

.esg-section-list 
    display: flex
    align-items: flex-start

.esg-section-list ul 
    list-style: none
    height: 201px
    width: 100%
    background: url(@/assets/images/responsibility/line.svg) no-repeat left center
    display: flex
    flex-direction: column
    justify-content: flex-end
    padding-left: 60px
    gap: 20px

.esg-section-list li 
    display: flex
    align-items: center
    font-size: 1em
    color: #333
    gap: 0px

.esg-section-list li:first-of-type 
    padding-left: 85px

.esg-container .swiper-pagination-bullets 
    text-align: center

.esg-section h3 
    font-size: 1em
    color: #666
    padding: 0

.esg-section p 
    font-size: 0.875em
    color: #999
    line-height: 180%

.doling-list 
    display: flex
    align-items: center
    padding: 36px 90px 36px 0

.doling-list:first-of-type 
    padding-top: 0

.doling-list h3 
    font-weight: 600
    color: #d62434
    font-size: 1.5em
    width: 220px
    text-align: center
    position: relative
    padding-bottom: 20px

.doling-list h3::after 
    content: ""
    display: block
    width: 30px
    height: 6px
    position: absolute
    bottom: 0px
    left: 50%
    margin-left: -15px
    background-color: #f5f6f8

.doling-list ul 
    list-style: none
    flex: 1
    display: flex
    flex-direction: column
    gap: 20px

.doling-list ul li 
    font-size: 16px
    color: #666
    position: relative
    padding-left: 20px
    line-height: 180%

.doling-list ul li::before 
    content: ""
    width: 6px
    height: 6px
    position: absolute
    left: 0
    top: 12px
    background-color: #d62434


@media screen and (max-width: 767px) 
    .front-block 
        padding-top:40px
    
    .main-content 
        min-height: inherit
    
    .sectors .box span,.services .box 
        padding: 0 0 0 100px
        background-position: 20px center
    
    .box 
        padding-top: 40px
    
    .container .box h2 
        margin-bottom: 30px
    
    .esg-yj 
        height: auto
        background: none
    
    .esg-yj-top 
        padding: 15px 20px
        height: auto
        width: 100%
        background-color: #d62434
    
    .esg-yj-bottom 
        margin: 0
        height: auto
        padding: 15px 20px
        background: rgb(214,36,52,0.04)
    
    .esg-gx-top 
        display: block
    
    .esg-gx-top-left,.esg-gx-top-right 
        width: 100%
        flex: none
        max-width: inherit
    
    .esg-gx-top-right 
        padding: 20px
    
    .esg-gx-top-right li 
        flex-direction: row
        align-items: center
        justify-content: flex-start
        padding: 10px 0
    
    .esg-gx-top-right h4 
        width: 100px
    
    .esg-gx-bottom 
        padding: 20px
    
    .esg-section-list ul 
        padding: 0
        background: none
        height: auto
        gap: 0
    
    .esg-section-list li:first-of-type 
        padding-left: 0
    
    .doling-list 
        display: block
        margin-bottom: 10px
        padding: 0
    
    .doling-list h3 
        width: auto
        text-align: left
    
    .doling-list h3::after 
        margin-left: 0
        left: 0
    
    .esg-report 
        padding: 20px
        margin-bottom: 50px
    
    .esg-report h3 
        font-size: 18px
    
    .esg-report li a.pdf 
        font-size: 14px
    
    .esg-report ul 
        margin-bottom: 20px
    
    .doling-list ul li 
        font-size: 13px
    
    .mission .flex 
        flex-direction: column
        gap: 20px
    
    .mission-list h3 
        font-size: 16px
    
    .mission-list p 
        font-size: 12px
    
    .ann70th 
        width: 45px
        height: 45px
    
    .content 
        padding: 0 15px
    
    .search-content 
        padding: 15px
    
    .gallery-wrapper .article 
        position: static
    
    .overview 
        padding-top: 40px
    
    #toolbar 
        display: none
    
    .main-right .page-banner h2.title 
        padding-left: 3%
    
    .news .article 
        margin-bottom: 15px
        padding-bottom: 20px
    
    .header 
        height: 60px
    
    .header .content 
        height: 100%
    
    .header #logo img 
        height: 24px
    
    #btn-menu 
        top: 19px
        padding-top: 19px
    
    #logo 
        padding-top: 19px
    
    #btn-menu i 
        height: 2px
    
    .container 
        margin-top: 60px
    
    .container p.big 
        font-size: 14px
    
    .theater .swiper-pagination span.swiper-pagination-bullet 
        height: 3px
        width: 30px
    
    #mobileDeviceAlert 
        display: block
    
    .container h2 
        margin-bottom: 20px
    
    .container .theater h2.title 
        font-size: 2em
        padding-top: 0px
    
    .container .page-banner h2.title 
        padding-top: 50px
    
    #frontBanner .swiper-pagination 
        bottom: 20px
        left: 15px
    
    .main-content 
        padding: 20px
    
    .tablet 
        display: none !important
    
    .phone 
        display: block !important
    
    footer td 
        width: 50%
        display: inline-block
    
    footer h3 
        margin-top: 30px
    
    .theater 
        height: 150px
    
    .front .theater,#home .theater 
        height: 200px
    
    .theater .swiper-slide .content 
        padding-top: 20px
    
    .container .theater p 
        width: 100%
        max-width: 100%
        font-size: 14px
    
    .theater .fx-slides > div > div 
        height: 400px
    
    .theater .fx-list 
        margin-top: -50px
    
    .firm 
        padding: 30px 0
        height: auto
    
    .advantage 
        padding: 30px 0
    
    .advantage .swiper-slide 
        height: auto
        padding-bottom: 60px
    
    .swiper-pagination 
        left: 15px
    
    .advantage-right 
        width: 100%
        padding: 0
        height: 200px
        position: static
        clear: both
    
    .advantage .swiper-slide .content 
        height: auto
        clear: both
    
    .advantage-left 
        width: 100%
    
    .swiper-btn-left,.swiper-btn-right 
    
    .advantage-left h3 
        font-size: 1.5em
        margin-bottom: 15px
    
    .flower 
        padding-top: 0px
    
    .flower .column 
        width: 100% !important
        background: none
    
    .flower .column:first-of-type ul 
        height: 100px
    
    .flower .column:first-of-type li,.flower .column:first-of-type li a 
        height: 100px
        color: #fff
    
    .flower .column:first-of-type li:last-of-type 
        border-right: 0
    
    .flower .column:first-of-type 
        height: auto
    
    .flower .img 
        height: 200px
    
    .flower ul 
        display: flex
        background: #f4f6f7
    
    .flower li 
        flex: 0 33.33%
    
    .flower .column:last-of-type 
        height: auto
        padding: 20px 0
    
    .flower .column:last-of-type ul 
        width: 100%
        flex-direction: row
        padding: 0
        background: none
        justify-content: space-between
    
    .flower h4 
        font-size: 2em
        text-align: center
    
    .portfolio-section-first .sectors .box 
        justify-content: flex-start
    
    .flower .column:last-of-type li 
        justify-content: flex-start
    
    .flower label,.flower p 
        margin-bottom: 5px
    
    .portfolios .content 
        padding: 20px 15px
    
    .portfolios .swiper-container 
        margin-bottom: 20px
    
    .news-right 
        width: 100%
        height: 200px
        padding: 0
        clear: both
        position: static
    
    .news .swiper-container 
    
    .container p 
        line-height: 150%
    
    .news-left .date 
        margin-bottom: 20px
    
    .news .content 
        clear: both
    
    .news-left 
        width: 100%
        float: none
    
    .news .swiper-slide 
        height: auto
        padding-bottom: 60px
    
    .news .swiper-pagination 
        bottom: 50px
    
    .news .column 
        width: 100% !important
        padding-left: 0 !important
        padding-right: 0 !important
        border-right: 0 !important
    
    .news-main 
        padding-bottom: 20px
    
    .news-main-left 
        width: 100%
        padding: 0 0 20px
        border-bottom: 1px solid #dedede
        float: none
    
    .news-main-right 
        float: none
        width: 100%
        padding: 20px 0 0
        border: none
    
    .news-main-right .news-list li 
        margin-bottom: 20px
        padding-bottom: 20px
        border-bottom: 1px solid #f5f5f5
    
    .news-main-right .news-list li a 
        background: url(/sites/all/themes/idgcapital/images/go.svg) no-repeat 100% bottom
    
    .portfolio-top-bar 
        margin-top: 0
        height: 80px
        padding: 5px 0
    
    .offices .select 
    
    .search-portfolio 
        top: 5px
    
    .flower .column:first-of-type li a:before 
        transform: translate3d(0,0,0)
    
    .feeds-front .media-list 
        width: 100%
        margin: 0 0 20px !important
        float: none
    
    .media-list a span.title 
        bottom: 25px
    
    .media-list a span.date,.media-list a span.date-display-single 
        bottom: 0
    
    .footer-blocks .block:last-of-type 
        float: left
    
    .news 
        padding: 20px 0
    
    .timeline 
        height: 360px
    
    .timeline-logo 
        width: 176px
        margin: 30px 0px 30px 15px
    
    .timeline-wrapper 
        padding: 0 15px
        height: 240px
    
    .timeline .swiper-slide 
        float: left
        width: 240px
        height: 120px
        background-size: 100% 100%
        margin-left: -130px
        padding: 10px 20px 0 30px
    
    .timeline .swiper-slide:nth-of-type(2n) 
        background-size: 100% 100%
    
    .timeline .swiper-slide:nth-of-type(2n) 
        margin-top: 120px
    
    h1 
        bottom: 40px
    
    .top ul li 
        font-size: 3em
        padding: 20px 0
    
    .services 
        margin-bottom: 40px
    
    .history 
        padding-bottom: 40px
    
    .top,.bio 
        padding: 40px 0
    
    .top ul 
        margin-top: 40px
    
    .team ul li 
        width: calc((100% - 20px) / 2)
        margin-right: 20px
        margin-bottom: 0
    
    .team ul li:nth-of-type(2n) 
        margin-right: 0
    
    .bio dl 
        display: block
    
    .bio dt 
        margin: 0
        padding: 0
        width: 100%
    
    .bio dd 
        width: 100%
        padding-top: 20px
    
    .node-content 
        padding: 0 15px
    
    .media-list 
        width: 100%
        margin: 0 0 20px !important
        float: none
    
    .news-tab 
        margin-bottom: 20px
    
    .team .alphabet 
        display: none !important
    
    .sector .sectors .box 
        width: 100%
        border-right: 0 !important
    
    .sector .sectors .box:nth-last-of-type(-n + 2) 
        border-bottom: 1px solid #d9dee1
    
    .sector .sectors .box:last-of-type 
        border-bottom: 0
    
    .sector .sectors 
        margin-bottom: 40px
    
    .investment 
        padding-bottom: 40px
    
    .casestudies .casestudy .content 
        padding: 30px 0
    
    .casestudies .casestudy .column 
        width: 100% !important
        padding-left: 0 !important
        padding-right: 0 !important
        border-left: 0 !important
    
    .portfolios .fx-accordion .column 
        width: 100% !important
        border-left: 0 !important
        padding-right: 0 !important
        padding-left: 0 !important
        margin: 20px 0
    
    #news .news .column 
        width: 100% !important
        padding-left: 0 !important
        padding-right: 0 !important
        border-right: 0 !important
    
    #news .news 
        padding: 40px 0 0 0
    
    #contact .affiliates 
        padding-bottom: 40px
    
    .offices .fx-slider h6,#contact .affiliates .fx-slider h6 
        font-size: 2em
    
    .contact ul 
        display: block
    
    .contact ul li 
        border-right: 0
        border-bottom: 1px solid #d8dcdc
    
    .contact ul li:last-of-type 
        border-bottom: 0
    
    #contact #map1,#contact #map2 
        margin-top: 40px !important
    
    .timeline .fx-right-arrow span,.timeline .fx-left-arrow span 
        display: none
    
    .footer-blocks 
        float: none
        width: 100%
        padding-top: 20px
    
    .timeline .pointer 
        display: none
    
    .news-block .article 
        width: 100%
        border: none
        padding: 0
    
    .news-block .article:after 
        display: none
    
    .portfolio-item 
        width: 50%
    
    .offices .contain 
        width: 100%
        float: none
        padding-bottom: 20px
        min-height: inherit
        position: relative
        z-index: 11
    
    .address-list 
        height: auto
        min-height: inherit
        padding-bottom: 47px
    
    .offices .photos 
        width: 100%
        height: 240px
        float: none
        clear: both
        padding-left: 0
    
    .news .fx-list 
        margin: 0 0 20px
    
    .casestudies 
        padding-bottom: 20px
    
    .casestudies .ab 
        top: -10px
    
    .casestudies dt 
        height: 48px
        line-height: 48px
    
    .casestudies dt:after 
        width: 48px
        height: 48px
        background-size: 20px
    
    .casestudies dl.fx-on dt 
        padding-left: 10px
    
    .casestudies dd 
        padding: 0 10px
    
    .casestudy 
        padding: 20px 0
    
    .casestudy img 
        max-height: 60px
        margin-bottom: 15px
    
    .btn-all 
        padding: 7px 10px
        background: #d62334
        font-size: 14px
        line-height: 20px
    
    .item-list .pager li 
        padding: 0
    
    .flower label,.flower p 
        padding: 0
        text-align: center
    
    .search-wrapper .block-search 
        width: 85%
    
    .search-content .search-form 
        height: auto
    
    .search-content .search-form .form-item-keys 
        width: 100%
        float: none
        display: block
        height: auto
        margin-bottom: 10px
    
    .search-content .search-form .form-item-keys label 
        float: none
        clear: both
        margin-right: 0
        width: 100%
    
    .search-content .search-form .form-item-keys .form-text 
        width: 100%
    
    .pop-right 
        top: 40%
        margin: 0
        right: 15px
        width: 30px
        position: fixed
        left: inherit
    
    .pop-right a.shengming-icon 
        width: 30px
        height: 80px
        background: url(/sites/all/themes/idgcapital/images/shengming-m.png) no-repeat
        background-size: 100%
    
    .pop-right .join-icon 
        display: block
        width: 65px
        height: 60px
        position: relative
        margin-left: -15px
        margin-top: 104px
    
    .announcement-dialog 
        width: 92%
        padding: 30px 4%
    
    .title-bar 
        font-size: 18px
        margin-bottom: 20px
    
    .title-bar span 
        display: block
        width: 100%
        text-align: center
        padding: 0 0 56px
        background: url(/sites/all/themes/idgcapital/images/logo.svg) no-repeat bottom center
        background-size: auto 36px
    
    .announcement-dialog a.close 
        right: 4%
        top: 10px
    
    .announcement-content 
        max-height: 400px
    
    .announcement-content-inner::after 
        position: static
        margin-top: -170px
        width: 120px
        margin-left: 40%
    
    .announcement-content p 
        font-size: 12px
        line-height: 180%
    
    .pop-form 
        padding: 40px
        height: auto
    
    .pop-form h2 
        margin-bottom: 20px
    
    .pop-form .form-item label 
        width: 36px
    
    .flower .column:first-of-type li 
        height: 68px
        border-bottom: 1px solid #dcdfe0
    
    .flower .column:first-of-type li:hover span 
        color: #656c6e
    

@media screen and (max-width: 480px) 
    .view-portfolio,.sector,.contact 
        padding-top:20px
    
    .info 
        top: 0
    
    .flower .column:first-of-type ul 
        height: auto
    
    .flower .column:first-of-type li:before,.flower .column:first-of-type li:after 
        display: none
    
    .item-list ul li 
        margin: 0
        line-height: 200%
    
    .item-list .pager li 
        padding: 0.2em
    
    .content 
        padding: 0 15px
    
    .front .portfolios,#home .portfolios 
        padding: 0
    
    .portfolios .select 
        width: 50%
    
    .search-portfolio 
        width: 50%
    
    .main-content 
        padding: 0 15px
    
    h1 
        font-size: 4em
    
    footer td 
        width: 100%
        display: block
    
    .theater h1 
        font-size: 3em
    
    .theater .fx-list 
        margin-top: -40px
    
    .theater .fx-nav 
        width: 50px
    
    .flower ul 
        display: block !important
    
    .flower .column:first-of-type li 
        border-width: 1px
    
    .flower .column:last-of-type li 
        display: block
        padding: 10px 0
    
    .front-block 
        padding-top: 30px
    
    .front-block.portfolio-section-second,.front-block.portfolio-section-first 
        padding-top: 30px
        margin-top: 0
    
    .sectors,.services 
        flex-direction: column
    
    .sectors .box,.services .box 
        width: 100%
        flex: none
        border-right: 0 !important
        max-width: inherit
        padding: 0 20px 0 120px
        background-size: 65px auto
        background-position: 30px center
    
    .sectors .box 
        padding-left: 0
        border-bottom: 1px solid #d9dee1
    
    .services .box:nth-last-of-type(-n + 2) 
        border-bottom: 1px solid #d9dee1
    
    .services .box:last-of-type 
        border-bottom: 0
    
    .history 
        padding-top: 0
    
    .timeline .fx-nav 
        font-size: 3em
    
    .swiper-container-horizontal > .swiper-pagination-bullets .swiper-pagination-bullet 
        margin: 0
    
    .timeline .fx-right-arrow,.timeline .fx-left-arrow 
        display: none
    
    .top ul 
        display: block
    
    .top ul li 
        border-right: 0
        border-bottom: 1px solid #d8dcdc
    
    .top ul li:last-of-type 
        border-bottom: 0
    
    .team ul li 
        width: 100%
        float: none
        display: block
        padding-bottom: 10px !important
        margin: 0 0 10px !important
    
    .bio .btn-close 
        right: inherit
        left: 50%
        margin-left: -16px
        top: -20px
    
    .offices .fcontent > .column,#contact .affiliates .fcontent > .column 
        width: 100%
        padding-right: 0
    
    .offices .photos > .fx-slides > div > div,#contact .affiliates .photos > .fx-slides > div > div 
        height: 200px
    
    .offices #map1,#contact .affiliates #map1,.offices #map2,#contact .affiliates #map2 
        height: 300px
    
    .news svg 
        transform: scale(0.85)
    
    .news .fx-nav 
        margin-right: 0
    
    .footer-blocks .block 
        width: 100%
        float: none
        padding-left: 0
        margin-bottom: 20px
    
    .portfolio-item 
        width: 100%
    
    .offices .photos 
        width: 100%
        height: 180px
        padding-left: 0
    
    .portfolio-detail 
        padding: 0
    
    .portfolio-detail .column 
        width: 100%
        float: none
        max-width: 100%
    
    .portfolio-detail .column:first-of-type 
        padding-right: 0
    
    .portfolio-detail .column:last-of-type 
        padding: 0
        border: none
    
    @keyframes height0 
        to 
            height: auto
            padding: 20px 0
            opacity: 1
        
    
    .portfolio-detail h4:after 
        margin: 0 0 20px
    
    .casestudies dd 
        padding: 0 15px
    
    .casestudy 
        padding: 15px 0
    
    .portfolio-top-bar 
        height: 60px
        padding: 0
        margin-top: 0
    
    .portfolios .select 
        width: 100%
        clear: both
    
    .portfolios .select ul 
        width: 100%
    
    .search-portfolio 
        width: 100%
        clear: both
        position: relative
        top: 5px
    

@media screen and (max-height: 500px) and (orientation:portrait) 

@media screen and (max-height: 500px) 
    .disclaimer-exit 
        top:18px
    
    .biggerSp 
        margin-top: 18px
        padding-bottom: 18px
        margin-bottom: 16px
    
    #weChatQRActual 
        height: calc(100% - 120px)
        margin-bottom: 7px
    

.swiper-pagination 
    text-align: left
    padding: 0
    left: 80px
    bottom: 60px
    position: absolute

  
.swiper-pagination span.swiper-pagination-bullet 
    width: 40px
    height: 4px
    display: inline-block
    text-indent: -9999px
    border-radius: 0
    background: #817775
    transition: background-color 0.5s
    opacity: 0.4
    margin: 0 10px 0 0
    cursor: pointer

::deep(.swiper-scrollbar)
    width: 300px
    .swiper-scrollbar-drag
      background: #bc171d !important
      opacity: 1

@media screen and (max-width: 768px) 
  .portfolio-content
    padding: 30px 20px !important
    .esg-list
      flex-direction: column
    .esg-section
      .esg-section-list
        font-size: 12px
</style>

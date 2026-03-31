<script setup>
import Lenis from "@studio-freight/lenis"
import { ref, onMounted, onUnmounted } from 'vue'

// 聯絡人數據
const contacts = [
    { region: '北美洲', email: 'NAPress@baincapital.com' },
    { region: '歐洲', email: 'EMEAPress@baincapital.com' },
    { region: '印度', email: 'IndiaPress@baincapital.com' },
    { region: '中國', email: 'ChinaPress@baincapital.com' },
    { region: '日本', email: 'JapanPress@baincapital.com' },
    { region: '澳洲', email: 'AUSPress@baincapital.com' },
]

// 重新整理後的 10 條完整新聞數據
const newsList = [
    {
        tag: '創投',
        date: '2026年2月5日',
        title: '貝恩資本創投公司的薩尼亞·奧賈與TITV主持人阿卡什·帕斯里查探討了Alphabet高達1750億美元的資本支出計劃。',
        source: '刊登於《資訊報》',
        url: 'https://www.theinformation.com/titv/tupxx'
    },
    {
        tag: '創投',
        date: '2026年2月3日',
        title: '認識創投產業的37位冉冉升起的新星',
        source: '刊登於《商業內幕》',
        url: 'https://www.businessinsider.com/venture-capital-industry-rising-stars-list-2026-1'
    },
    {
        tag: '特殊情況',
        date: '2026年1月30日',
        title: '貝恩資本和弗雷澤銀行以創紀錄的價格將巴塞隆納辦事處出售給InmoCaixa銀行。',
        source: '發表於IPE Real Assets',
        url: 'https://realassets.ipe.com/news/bain-capital-and-freo-sell-barcelona-office-to-inmocaixa-in-record-deal/10134922.article'
    },
    {
        tag: '房地產，特殊情況',
        date: '2026年1月28日',
        title: 'APP Jet Center連鎖店易主，被貝恩資本收購',
        source: '刊登於《國際航空新聞在線》',
        url: 'https://www.ainonline.com/aviation-news/business-aviation/2026-01-28/app-jet-center-chain-changes-hands'
    },
    {
        tag: '特殊情況',
        date: '2026年1月28日',
        title: '金融50強',
        source: '刊登於公告牌',
        url: 'https://www.billboard.com/p/billboard-finance-50-list-2026/'
    },
    {
        tag: '房地產',
        date: '2026年1月21日',
        title: '對貝恩資本合夥人兼房地產主管瑞安·科頓的採訪',
        source: '刊登於《房地產資本》播客',
        url: 'https://podcasts.apple.com/us/podcast/ryan-cotton-bain-capitals-partner-and-head-of-real-estate/id1502127168?i=1000746022891&l=fr-FR'
    },
    {
        tag: '房地產',
        date: '2026年1月16日',
        title: '更具鑑賞力的市場：是什麼推動了房地產融資熱潮',
        source: '發表於PERE',
        url: 'https://www.perenews.com/a-more-discerning-market-whats-driving-real-estates-fundraising-upswing/'
    },
    {
        tag: '企業新聞',
        date: '2026年1月15日',
        title: '與貝恩資本的戴維·格羅斯的問答',
        source: '發表於Axios',
        url: 'https://www.axios.com/2026/01/15/bain-capital-david-gross-private-equity'
    },
    {
        tag: '企業新聞',
        date: '2026年1月13日',
        title: '貝恩資本任命大衛·格羅斯為唯一管理合夥人',
        source: '刊登於《金融時報》',
        url: 'https://www.ft.com/content/6e2c0ed7-497d-4511-9f93-8fdd63ba5c05'
    },
    {
        tag: '房地產',
        date: '2026年1月12日',
        title: '貝恩資本第三支旗艦基金完成募集，規模達34億美元。',
        source: '發表於PERE',
        url: 'https://www.perenews.com/bain-closes-third-flagship-fund-at-3-4bn/'
    }
]

const isTop = ref(false)
const isWhite = ref(true) // 確保 header 狀態正確
let lenis = null
let rafId = null

onMounted(() => {
    // 獲取滾動容器
    const scrollContainer = document.querySelector('.right-scrollable')

    lenis = new Lenis({
        wrapper: scrollContainer, // 限制 Lenis 在此容器內工作
        content: document.querySelector('.section-news'),
        duration: 1.2,
        easing: t => 1 - Math.pow(1 - t, 3),
        smooth: true,
        direction: "vertical",
        gestureDirection: "vertical",
        smoothTouch: false,
        touchMultiplier: 1.5
    })

    const raf = (time) => {
        lenis.raf(time)
        rafId = requestAnimationFrame(raf)
    }

    rafId = requestAnimationFrame(raf)

    lenis.on("scroll", ({ scroll, limit, direction }) => {
        // 根據局部滾動位置判斷 Header 狀態
        if (direction === 1) {
            isTop.value = true
        }
        if (direction === -1) {
            isTop.value = false
        }
    })
})

onUnmounted(() => {
    if (rafId) cancelAnimationFrame(rafId)
    if (lenis) lenis.destroy()
})

const goLink = (link) => {
    window.open(link, '_blank')
}
</script>

<template>
    <div class="cont">
        <headerTop :top="isTop" :white="true" :opacity="isTop"></headerTop>
        <div class="bodybox">
            <div class="container">
                <div class="main-layout">
                    <aside class="left-fixed">
                        <div class="contact-section">
                            <h3 class="label">{{ $lang('媒體聯絡人') }}</h3>
                            <div v-for="item in contacts" :key="item.region" class="contact-item">
                                <span class="region">{{ $lang(item.region) }}</span>
                                <a :href="`mailto:${item.email}`" class="email">
                                    {{ item.email }}
                                </a>
                            </div>
                        </div>
                    </aside>

                    <main class="right-scrollable">
                        <section class="section-news">
                            <div class="news-header">
                                <div class="newsleti">
                                    <h2 class="title">{{ $lang('最新消息') }}</h2>
                                    <div class="filters">
                                        <span>{{ $lang('商業：全部') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg"
                                                width="15" height="8.91" viewBox="0 0 15 8.91">
                                                <path class="cls-1"
                                                    d="M1.79.84c2.69,2.73,4.04,4.09,5.71,4.09s3.02-1.36,5.71-4.09l.48-.49.95.97-7.15,7.24L.35,1.32l.95-.97.48.49Z">
                                                </path>
                                            </svg></span>
                                        <span>{{ $lang('年：全部') }} <svg id="Layer_1" xmlns="//www.w3.org/2000/svg"
                                                width="15" height="8.91" viewBox="0 0 15 8.91">
                                                <path class="cls-1"
                                                    d="M1.79.84c2.69,2.73,4.04,4.09,5.71,4.09s3.02-1.36,5.71-4.09l.48-.49.95.97-7.15,7.24L.35,1.32l.95-.97.48.49Z">
                                                </path>
                                            </svg></span>
                                    </div>
                                </div>
                                <div class="headright">
                                    <div class="gao">{{ $lang('新聞稿') }}</div>
                                    <div class="baodao">{{ $lang('新聞報道') }}</div>
                                </div>
                            </div>

                            <div class="news-container">
                                <div class="featured-news" @click="navigateTo('/newsdetails')">
                                    <img src="@/assets/images/GettyImages-1942702729_0.jpg" alt="">
                                    <div class="meta">
                                        <span style="font-size: 15px;color: #011aff;"> {{ $lang('新聞稿') }} /</span>
                                        {{ $lang('私募股權') }} /
                                        {{ $lang('2025年10月6日') }}
                                    </div>
                                    <h3 class="news-title">{{ $lang('貝恩資本完成第十四期旗艦私募股權基金募集，規模達140億美元') }}</h3>
                                </div>

                                <div class="news-list">
                                    <div v-for="(news, index) in newsList" :key="index" class="list-items">
                                        <div class="meta">
                                            <span class="type">{{ $lang('新闻报道') }} / </span>
                                            <span class="date">{{ $lang(news.tag) }} / </span>
                                            <span class="date">{{ $lang(news.date) }}</span>
                                        </div>
                                        <h4 class="item-title" @click="goLink(news.url)">{{ $lang(news.title) }}</h4>
                                        <span class="date">{{ $lang(news.source) }}</span>
                                    </div>
                                </div>
                            </div>
                        </section>
                    </main>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped lang="sass">
\:global(body)
  margin: 0
  overflow: hidden // 禁止全局滾動
  background-color: #fcfaf2

.bodybox
  height: 100vh // 固定高度為視窗高度
  background-color: #fefcf5
  transition: background .3s
  overflow: hidden

  .container
    max-width: 90%
    margin: 0 auto
    height: 100% // 確保容器撐滿
    @media (max-width: 768px)
        padding-top: 70px

.main-layout
  display: flex
  height: calc(100vh - 120px) // 減去頂部 padding
  overflow: hidden

// 左側固定欄
.left-fixed
  width: 280px
  height: 100%
  flex-shrink: 0
  border-right: 1px solid rgba(0, 0, 0, 0.08)
  color: #1b215a
  padding-top: 120px
  @media (max-width: 768px)
    display: none

  
  .label
    font-size: 24px
    font-weight: 300
    margin-bottom: 30px

  .contact-item
    margin-bottom: 25px
    .region
      display: block
      font-size: 14px
      margin-bottom: 4px
    .email
      font-size: 14px
      text-decoration: none
      color: inherit
      &:hover
        text-decoration: underline

// 右側滾動區域
.right-scrollable
  flex: 1
  height: 100%
  overflow-y: auto // 允許垂直滾動
  padding: 0
  min-height: 0 // 修正 Flex 子元素溢出計算

.section-news
  padding: 0 20px 100px

.news-header
  display: flex
  justify-content: space-between
  align-items: center
  border-bottom: 1px solid #eee
  padding-bottom: 15px
  margin-bottom: 30px
  padding-top: 120px
  @media (max-width: 768px)
    display: block
    margin-bottom: 0
  .newsleti
    justify-content: space-between
    align-items: center
    display: flex
    @media (max-width: 768px)
      display: block
  .headright
    display: flex
    color: #fff
    border-radius: 5px
    font-size: 18px
    font-weight: 500
    overflow: hidden
    @media (max-width: 768px)
      font-size: 14px
    div
      background-color: rgba(156,150,154,.8)
      padding: 3px 8px
      cursor: pointer
      &:hover
        background-color: rgba(156,150,154,1)
    .gao
      margin-right: 2px

  .title
    font-size: 36px
    font-weight: 300
    @media (max-width: 768px)
      font-size: 30px
  .filters
    font-size: 18px
    color: #011aff
    display: flex
    align-items: center
    fill: #011aff
    @media (max-width: 768px)
      font-size: 16px
      margin: 15px 0
    span
      margin-left: 20px
      cursor: pointer
      display: flex
      align-items: center
      @media (max-width: 768px)
        margin-left: 0
        margin-right: 30px

.news-container
  display: flex
  gap: 20px
  @media (max-width: 768px)
    display: block

  .featured-news
    flex: 1.2
    cursor: pointer
    img
      width: 100%
      aspect-ratio: 16 / 9
      object-fit: cover
      margin-bottom: 20px
      border-radius: 5px
    .meta
      font-size: 17px
      color: #999
      margin-bottom: 10px
      @media (max-width: 768px)
        font-size: 12px
    .news-title
      font-size: 24px
      line-height: 1.4
      color: #1c2156
      font-weight: 300
      @media (max-width: 768px)
        font-size: 20px

  .news-list
    flex: 1
    border-left: 1px solid #eee
    padding-left: 30px
    @media (max-width: 768px)
        padding-left: 0
        border-left: 0
        margin-top: 80px

    .list-items
      padding-bottom: 20px
      margin-bottom: 20px
      border-bottom: 1px solid #f0f0f0
      .meta
        font-size: 12px
        margin-bottom: 8px
        color: #333
        .type
          font-weight: bold
          font-size: 15px
          color: #011aff
          @media (max-width: 768px)
            font-size: 12px
        
      .item-title
        font-size: 24px
        line-height: 1.5
        font-weight: 400
        cursor: pointer
        color: #1c2156
        &:hover
          color: #0056b3
        @media (max-width: 768px)  
          font-size: 20px
          font-weight: 300
      .date
        font-size: 17px
        font-weight: 500
        color: #999
        @media (max-width: 768px)
            font-size: 12px
</style>
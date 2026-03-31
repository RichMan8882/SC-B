<script lang="ts" setup>
import Lenis from "@studio-freight/lenis"
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import anime from '~/components/game/js/anime.es.js'
const { t } = useI18n()
const siteStore = useSiteStore()
const router = useRouter()
const scrollTop = ref(0)
const section1 = ref<HTMLElement | null>(null)
const section2 = ref<HTMLElement | null>(null)
const section3 = ref<HTMLElement | null>(null)
const section4 = ref<HTMLElement | null>(null)
const windowHeight = ref(0)
const timer = ref()
onMounted(() => {
  // timer.value = setInterval(() => {
  //   bannerIndex.value++
  //   if (bannerIndex.value > 2) bannerIndex.value = 0
  // }, 3000)
  // document.documentElement.scrollTop = 0
  // if (window) {
  //   console.log('window', window.innerWidth)
  //   window.addEventListener('scroll', handleScroll)
  // }
  // windowHeight.value = window.innerHeight
  // window.addEventListener('resize', () => {
  //   windowHeight.value = window.innerHeight
  // })
})
const handleScroll = () => {
  scrollTop.value = window.scrollY
  let scrollTrue = scrollTop.value + windowHeight.value
  console.log('offsetTop', section1.value?.offsetTop)
  console.log('scrollTop', window.scrollY)
  console.log('scrollTrue', scrollTrue)

  console.log(scrollTrue >= section1.value?.offsetTop - 100)

  if (scrollTrue >= section1.value?.offsetTop - 100) {
    section1.value?.classList.add('section-attain')
  } else {
    section1.value?.classList.remove('section-attain')
  }
  if (scrollTrue >= section2.value?.offsetTop - 100) {
    section2.value?.classList.add('section-scale')
  } else {
    section2.value?.classList.remove('section-scale')
  }
  if (scrollTrue >= section3.value?.offsetTop - 100) {
    section3.value?.classList.add('section-attain')
  } else {
    section3.value?.classList.remove('section-attain')
  }
  if (scrollTrue >= section4.value?.offsetTop - 100) {
    section4.value?.classList.add('section-scale')
  } else {
    section4.value?.classList.remove('section-scale')
  }
}
onUnmounted(() => {
  timer.value = null
  if (window) {
    window.removeEventListener('scroll', handleScroll)
  }
})
const toUrl = (url) => {
  window.open(url)
}
gsap.registerPlugin(ScrollTrigger);
let lenis = null
let rafId = null
const bgcolor = ref('#fefcf6')
const isStartnum = ref(false)
onMounted(() => {
  lenis = new Lenis({
    duration: 1.2,
    easing: t => 1 - Math.pow(1 - t, 3),
    smooth: true,
    direction: "vertical",
    gestureDirection: "vertical",
    smoothTouch: false,
    touchMultiplier: 2
  })

  const raf = (time) => {
    lenis.raf(time)
    rafId = requestAnimationFrame(raf)
  }

  rafId = requestAnimationFrame(raf)
  lenis.on("scroll", ({ scroll, limit, direction }) => {
    isWhite.value = scroll >= 100
    if (direction == 1) {
      isTop.value = true
    }
    if (direction == -1) {
      isTop.value = false
    }
    if (scroll < 350) {
      bgcolor.value = '#fefcf6 !important'
    }
    if (scroll <= 100) {
      isStartnum.value = true
      dataNumber.value = {
        1: 0,
        2: 0,
        3: 0,
        4: 0
      }
    }
    if (scroll > 100 && isStartnum.value) {
      isStartnum.value = false
      dwakjhhd()
    }
    const width = window.innerWidth
    if (width > 768) {
      if (scroll < 3500) {
        bgcolor.value = '#fefcf5'
      }
      if (scroll >= 3500) {
        bgcolor.value = '#b2deff'
      }
      if (scroll >= 5200) {
        bgcolor.value = '#1e5e94'
      }
      if (scroll >= 5200) {
        if (botAcitve.value == 1) {
          bgcolor.value = '#1e5e94'
        } else {
          bgcolor.value = '#164167'
        }
      }
    } else {
      if (scroll < 2500) {
        bgcolor.value = '#fefcf5'
      }
      if (scroll >= 2500) {
        bgcolor.value = '#b2deff'
      }
      if (scroll >= 3500) {
        bgcolor.value = '#1e5e94'
      }
    }
  })
  gsap.to('.chaimg', {
    y: 200, // 負值代表上浮，數值越大浮動越明顯
    ease: "none", // 必須為 none 才能完美同步滾動條
    scrollTrigger: {
      trigger: '.aboutmimg', // 監視這個大容器
      start: "top bottom",    // 當容器頂部進入視窗底部時開始計算
      end: "bottom top",      // 當容器底部離開視窗頂部時結束
      scrub: 1,             // [關鍵參數] 數字代表延遲感。1.5秒的緩動讓它有「懸浮沉降」的感覺
    }
  });
})

onUnmounted(() => {
  cancelAnimationFrame(rafId)
  lenis.destroy()
})
const hideplayerimgbg1 = ref(true)
const hideplayerimgbg2 = ref(true)
const hideplayerimgbg3 = ref(true)
const rotateValue = ref(0)
const useyixing = ref(false)
const goLink = (link) => {
  window.open(link)
}
const indexbannerAcitve = ref(0)
const indexbannerAcitveup = (a) => {
  if (a) {
    indexbannerAcitve.value--
    if (indexbannerAcitve.value == -1) {
      indexbannerAcitve.value = 5
    }
  } else {
    indexbannerAcitve.value++
    if (indexbannerAcitve.value == 6) {
      indexbannerAcitve.value = 0
    }
  }
}
const isTop = ref(false)
const isWhite = ref()
const botAcitve = ref(1)
const dataNumber = ref({
  1: 0,
  2: 0,
  3: 0,
  4: 0
})
const dwakjhhd = () => {
  anime({
    easing: 'easeInOutSine',
    targets: dataNumber.value,
    1: 1984,
    2: 23,
    3: 1985,
    4: 215,
    round: 1,
    duration: 1000
  })
}
</script>

<template>
  <div class="cont">
    <headerTop :top="isTop" :white="true" :opacity="isTop"></headerTop>
    <div :style="{ background: bgcolor }" class="bodybox">
      <div class="aboutmimg">
        <img class="abhimg" src="@/assets/images/bc-about-bg-parallax-v2.webp" alt="">
        <img class="chaimg" src="@/assets/images/parallax-cross-bg.webp" alt="">
        <div class="aobtbox">
          <div class="guanyutit" style="">{{ $lang('關於我們') }}</div>
          <div>{{ $lang('我們是世界領先的私人投資公司之一，與我們的投資者、公司和社區合作，創造持久的影響力。') }}</div>
        </div>
      </div>
      <div class="container">
        <div class="numlook">
          <div>{{ $lang('以數字來看') }}</div>
          <div class="numbox">
            <div class="numboxitem">
              <div @click="dwakjhhd" class="numte">{{ dataNumber[1] }}</div>
              <div class="bote">{{ $lang('貝恩資本創立') }}</div>
            </div>
            <div class="numboxitem">
              <div class="numte">{{ dataNumber[2] }}</div>
              <div class="bote">{{ $lang('全球辦事處') }}</div>
            </div>
            <div class="numboxitem">
              <div class="numte">{{ new Intl.NumberFormat('zh-TW').format(dataNumber[3]) }}+</div>
              <div class="bote">{{ $lang('團隊成員') }}</div>
            </div>
            <div class="numboxitem">
              <div class="numte">~<span>$</span>{{ dataNumber[4] }}<span style="vertical-align: 20px">B</span></div>
              <div class="bote">{{ $lang('資產項下管理') }}</div>
            </div>
          </div>
        </div>
        <h2 class="ftitle">{{ $lang('我們的宗旨和價值觀') }}</h2>
        <h1 class="stitle">{{ $lang('致力於產生持久影響') }}</h1>
        <div class="banner-box" style="justify-content: center;">
          <div class="ifbox abifsty">
            <iframe allow="autoplay;" class="player2" muted="" plays-inline=""
              src="https://player.vimeo.com/video/1026848889?api=1&amp;player_id=player2&amp;quality=1080p&amp;autoplay=0"
              frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="">
            </iframe>
            <img v-if="hideplayerimgbg1" class="playerbg1" style="width: 110% !important;max-width: none;"
              src="@/assets/images/homepage-bannerfang.jpg" alt="">
            <div v-if="hideplayerimgbg1" class="textbg"></div>
            <div v-if="hideplayerimgbg1" @click="hideplayerimgbg1 = false" class="textmore"><svg id="Layer_1"
                xmlns="//www.w3.org/2000/svg" width="25.88" height="25.88" viewBox="0 0 25.88 25.88">
                <path class="cls-1"
                  d="M11.29,19.96l-1.32-1.32.67-.67c2.41-2.41,3.62-3.62,3.62-5.03s-1.21-2.62-3.62-5.03l-.67-.67,1.32-1.32,7.02,7.02-7.02,7.02ZM12.94,0C5.8,0,0,5.8,0,12.94s5.8,12.94,12.94,12.94,12.94-5.8,12.94-12.94S20.07,0,12.94,0">
                </path>
              </svg>{{ $lang('用我們的話語來說，我們的宗旨') }}</div>
          </div>
        </div>
        <section class="content-wrapper">
          <h1 class="main-title">
            {{ $lang('我們投資並參與商業活動，以期為公司、員工、社區和環境') }}<span class="highlight-text">{{ $lang('帶來正面且持久的影響。') }}</span>
          </h1>
          <div class="grid-container">
            <div class="grid-item">
              <h3>{{ $lang('我們建立了卓越的合作關係') }}</h3>
              <p>{{ $lang('我們真心希望彼此都能成功。我們深知，多元化和包容性的團隊才能帶來卓越的成果。') }}</p>
            </div>

            <div class="grid-item">
              <h3>{{ $lang('我們挑戰傳統思維') }}</h3>
              <p>{{ $lang('我們思維獨特。我們秉持客觀嚴謹的探究精神，力求在每個機會中發揮最大潛能。我們尊重事實的力量。') }}</p>
            </div>

            <div class="grid-item">
              <h3>{{ $lang('我們堅持不懈地工作') }}</h3>
              <p>{{ $lang('我們擼起袖子，埋頭苦幹，每天努力工作，力求更好的成果。我們堅持不懈地攻克難題。我們把事情做到到底。') }}</p>
            </div>

            <div class="grid-item">
              <h3>{{ $lang('我們相信品格至關重要。') }}</h3>
              <p>{{ $lang('我們秉持個人誠信、謙遜和公民責任感。我們以同理心和信念行事。') }}</p>
            </div>
          </div>
          <div class="bottom-line"></div>
          <h1 class="main-title twotitle" style="margin-top: 50px;">
            {{ $lang('我們的宗旨、價值觀以及對持久影響的承諾') }}<span class="highlight-text">{{ $lang('都始於我們的員工') }}</span>。
          </h1>
        </section>
        <div class="banner-box nedju">
          <h1 class="titlesbox">
            <h2 @click="hideplayerimgbg2 = !hideplayerimgbg2">
              {{
                $lang('我們的人才是我們最大的優勢。我們求知欲強，善於提出精闢的問題，彼此尊重地提出挑戰，並努力攜手共進，取得成功。積極參與高風險議題的解決是我們成長的動力，也是我們持續發展的關鍵，因為我們深知，團結合作才能成就更大的事業。')
              }}
            </h2>
            <div class="linkbtn">
              {{ $lang('了解更多貝恩資本的職業機會') }}
              <div class="arrow-outline">
                <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17" viewBox="0 0 6.63 11.17">
                  <path class="arrow-icon"
                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                  </path>
                </svg>
              </div>
            </div>
          </h1>
          <div class="ifbox">
            <iframe allow="autoplay;" class="player2 playermr" muted="" plays-inline=""
              src="https://player.vimeo.com/video/1026854116?api=1&amp;player_id=player2&amp;quality=1080p&amp;autoplay=0"
              frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="">
            </iframe>
            <img v-if="hideplayerimgbg2" class="playerbg1" src="@/assets/images/career-video-bg_0.jpg" alt="">
            <div v-if="hideplayerimgbg2" class="textbg"></div>
            <div v-if="hideplayerimgbg2" @click="hideplayerimgbg2 = false" class="textmore"><svg id="Layer_1"
                xmlns="//www.w3.org/2000/svg" width="25.88" height="25.88" viewBox="0 0 25.88 25.88">
                <path class="cls-1"
                  d="M11.29,19.96l-1.32-1.32.67-.67c2.41-2.41,3.62-3.62,3.62-5.03s-1.21-2.62-3.62-5.03l-.67-.67,1.32-1.32,7.02,7.02-7.02,7.02ZM12.94,0C5.8,0,0,5.8,0,12.94s5.8,12.94,12.94,12.94,12.94-5.8,12.94-12.94S20.07,0,12.94,0">
                </path>
              </svg>{{ $lang('我們優勢的核心在於我們的人才。') }}</div>
          </div>
        </div>
        <h2 class="ftitle">{{ $lang('我們不同的合作方式') }}</h2>
        <h1 class="stitle">{{ $lang('夥伴關係是我們的核心價值觀') }}</h1>
        <div class="huobancont">
          <div class="huobanconttitle">{{ $lang('與同事們') }}</div>
          <div class="huobanconttexts">
            {{
              $lang('公司成立於1984年，最初是一家私人合夥企業，我們致力於培養創新、創業和敏捷的企業文化，並賦能員工自主規劃和掌控職涯發展道路。如今，我們的合夥模式使我們能夠追求策略性的平台成長，並共同致力於跨平台協作。')
            }}</div>
          <div class="huobanconttitle">{{ $lang('與合作夥伴') }}</div>
          <div class="huobanconttexts">
            {{
              $lang('我們與業界領先專家和高階主管建立了長期穩固的合作關係，這種關係不僅限於公司內部，還延伸至合作夥伴、交易對手和社群組織。透過整合全球網路中深厚多元的專業知識，我們得以挖掘突破性洞見，掌握前所未有的機會。')
            }}</div>
          <div class="huobanconttitle">{{ $lang('管理階層') }}</div>
          <div class="huobanconttexts" @click="hideplayerimgbg3 = !hideplayerimgbg3">
            {{
              $lang('投資組合公司的管理團隊親身體驗了我們合作共贏的模式。我們以嚴謹的分析方法深入了解每家公司，並迅速調配最合適的資源，以理解和提升其獨特的財務、營運和文化動態。秉持著「優秀企業如何成就卓越」的信念，我們與管理團隊緊密合作，協助其在成長階段和策略轉型中不斷突破傳統思維，持續追求規模化改進。')
            }}
          </div>
        </div>
        <div class="banner-box" style="justify-content: center;">
          <div class="ifbox abifsty">
            <iframe allow="autoplay;" class="player2" muted="" plays-inline=""
              src="https://player.vimeo.com/video/1026931144?api=1&amp;player_id=player2&amp;quality=1080p&amp;autoplay="
              frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="">
            </iframe>
            <img v-if="hideplayerimgbg3" class="playerbg1" style="width: 100% !important;max-width: none;"
              src="@/assets/images/partnership-bg.jpg" alt="">
            <div v-if="hideplayerimgbg3" class="textbg"></div>
            <div v-if="hideplayerimgbg3" @click="hideplayerimgbg3 = false" class="textmore"><svg id="Layer_1"
                xmlns="//www.w3.org/2000/svg" width="25.88" height="25.88" viewBox="0 0 25.88 25.88">
                <path class="cls-1"
                  d="M11.29,19.96l-1.32-1.32.67-.67c2.41-2.41,3.62-3.62,3.62-5.03s-1.21-2.62-3.62-5.03l-.67-.67,1.32-1.32,7.02,7.02-7.02,7.02ZM12.94,0C5.8,0,0,5.8,0,12.94s5.8,12.94,12.94,12.94,12.94-5.8,12.94-12.94S20.07,0,12.94,0">
                </path>
              </svg>{{ $lang('共同創造價值') }}</div>
          </div>
        </div>
        <div class="yixing">
          <div class="map">
            <img v-if="botAcitve == 1" src="@/assets/images/imagemap.png" alt="">
            <div class="mapcont" :class="botAcitve == 1 ? 'absolutecls' : ''">
              <div class="maptitlebox">
                <div class="maptitle">{{ $lang('我們的全球佈局') }}</div>
                <div class="zhou">
                  <div @click="botAcitve = 1, bgcolor = '#1e5e94'" :class="botAcitve == 1 ? 'botacitve' : ''">{{
                    $lang('全球位置') }}</div>
                  <div @click="botAcitve = 2, bgcolor = '#164167'" :class="botAcitve == 2 ? 'botacitve' : ''">{{
                    $lang('美洲') }}</div>
                  <div @click="botAcitve = 3, bgcolor = '#164167'" :class="botAcitve == 3 ? 'botacitve' : ''">{{
                    $lang('亞洲') }}</div>
                  <div @click="botAcitve = 4, bgcolor = '#164167'" :class="botAcitve == 4 ? 'botacitve' : ''">{{
                    $lang('歐洲') }}</div>
                </div>
              </div>
              <div class="syall"><span>{{ $lang('商業：') }}</span>{{ $lang('全部') }}</div>
              <div v-if="botAcitve == 2" class="maplist">
                <div class="nonelineb"></div>
                <div class="noneliner"></div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('波士頓') }}</p>
                  <p>{{ $lang('美國麻薩諸塞州') }}</p>
                  <p>{{ $lang('波士頓克拉倫登街200號，') }}</p>
                  <p>{{ $lang('郵編02116 。') }}</p>
                  <p class="phone">+1 (617) 516-2000</p>
                  <p>{{ $lang('傳真：') }}+1 (617) 516-2010</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('芝加哥') }}</p>
                  <p>{{ $lang('美國伊利諾州芝加哥市西亞當斯街222號') }}</p>
                  <p>{{ $lang('2200室，郵編：60606主要地址：') }}</p>
                  <p class="phone" style="margin-top: 50px;">+1 (312) 253-6940</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('紐約') }}</p>
                  <p>{{ $lang('美國紐約州') }}</p>
                  <p>{{ $lang('紐約市麥迪遜大道535號29樓，郵編10022主要地址：') }}</p>
                  <p class="phone">+1 (212) 326-9420</p>
                  <p>{{ $lang('傳真：') }}+1 (212) 421-2225</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('紐約百老匯') }}</p>
                  <p style="color: #abcae9;">{{ $lang('創投與加密貨幣') }}</p>
                  <p>{{ $lang('美國紐約州') }}</p>
                  <p>{{ $lang('紐約市百老匯大街799號10樓，郵編10003主要地址：') }}</p>
                  <p class="phone">+1 (212) 822-2900</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('帕洛阿爾托') }}</p>
                  <p>{{ $lang('美國加州') }}</p>
                  <p>{{ $lang('帕洛阿爾托市漢密爾頓大道524號，郵編94301。主地址：') }}</p>
                  <p class="phone">+1 (650) 798-2500</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('舊金山') }}</p>
                  <p>{{ $lang('美國加州') }}</p>
                  <p>{{ $lang('舊金山太平洋大道450號，') }}</p>
                  <p>{{ $lang('郵編94133主要地址：') }}</p>
                  <p class="phone">+1 (628) 201-3600</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
              </div>
              <div v-if="botAcitve == 3" class="maplist">
                <div class="nonelineb"></div>
                <div class="noneliner"></div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('香港') }}</p>
                  <p>{{ $lang('香港金鐘皇后大道中88號') }}</p>
                  <p>{{ $lang('太古廣場一號25樓2501室') }}</p>
                  <p class="phone" style="margin-top: 50px;">+852-36566800</p>
                  <p>{{ $lang('傳真：') }}+852-30140844</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('模里西斯') }}</p>
                  <p>{{ $lang('毛里求斯博普蘭') }}</p>
                  <p>{{ $lang('湖濱區斯特蘭德 街3號樓底層1號辦公室，') }}</p>
                  <p>{{ $lang('郵編21001 。') }}</p>
                  <p class="phone">+230 468 1320</p>
                  <p>{{ $lang('傳真：') }}+230 468 1321</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('墨爾本') }}</p>
                  <p>{{ $lang('澳洲維多利亞省墨爾本柯林斯街101號20層，') }}</p>
                  <p>{{ $lang('郵編3000主要地址：') }}</p>
                  <p class="phone">+61-3-8102-8600</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('孟買') }}</p>
                  <p>Express Towers</p>
                  <p>{{ $lang('私募股權：22樓2201單元；') }}</p>
                  <p>{{ $lang('特殊情況：11樓1104單元；') }}</p>
                  <p>Nariman Point；</p>
                  <p>{{ $lang('孟買；') }}</p>
                  <p>{{ $lang('馬哈拉施特拉邦；400 021；') }}</p>
                  <p>{{ $lang('印度；') }}</p>
                  <p>{{ $lang('總機：') }}+91-2267528000</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('大阪') }}</p>
                  <p>Grand Front Osaka Tower A 24F</p>
                  <p>4-20 Ofukacho</p>
                  <p>Kita-ku</p>
                  <p>Osaka 530-0011</p>
                  <p>{{ $lang('日本') }}</p>
                  <p>+81 6-7712-2777</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('首爾') }}</p>
                  <p>28F, Parnas Tower</p>
                  <p>521, Teheran-ro, Gangnam-gu</p>
                  <p>{{ $lang('首爾 06164') }}</p>
                  <p>{{ $lang('韓國，') }}</p>
                  <p>{{ $lang('美因共和國：') }}+82 2 6940 2300</p>
                  <p>{{ $lang('傳真：') }}+82 2 6322 9822</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('上海') }}</p>
                  <p>{{ $lang('中國上海市靜安區') }}</p>
                  <p>{{ $lang('南京西路1266號廣場66辦公大樓2號大樓47層4705室主要地址：') }}</p>
                  <p class="phone" style="margin-top: 60px;">+86-21-22508000</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('上海') }}</p>
                  <p>{{ $lang('中國上海市') }}</p>
                  <p>{{ $lang('世紀大道8號國際金融中心二期36樓3669室，郵編：') }}</p>
                  <p>{{ $lang('200120主要地址：') }}</p>
                  <p class="phone">+86-2160626120</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('新加坡') }}</p>
                  <p>{{ $lang('新加坡市場街88號，40-01室，凱德集團，新加坡') }}</p>
                  <p>{{ $lang('048948主樓：') }}</p>
                  <p class="phone">+65 6016 1030</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('雪梨') }}</p>
                  <p>{{ $lang('澳洲新南威爾斯州雪梨') }}</p>
                  <p>{{ $lang('菲利普街88號28層，郵編2000主要地址：') }}</p>
                  <p class="phone" style="margin-top: 60px;">+61-2-9093-5500</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('東京') }}</p>
                  <p>5F, Palace Building 1-1-1 Marunouchi</p>
                  <p>Chiyoda-ku</p>
                  <p>Tokyo 100-0005</p>
                  <p>{{ $lang('日本') }}</p>
                  <p>+81-362127070</p>
                  <p>{{ $lang('傳真：') }}+81-362127071</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
              </div>
              <div v-if="botAcitve == 4" class="maplist">
                <div class="nonelineb"></div>
                <div class="noneliner"></div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('都柏林') }}</p>
                  <p>{{ $lang('愛爾蘭') }}</p>
                  <p>{{ $lang('都柏林 4 區梅斯皮爾路 45 號主地址：') }}</p>
                  <p class="phone">+353-19019800</p>
                  <p>{{ $lang('傳真：') }}+353-16335380</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('里斯本') }}</p>
                  <p>AV。 da Liberdade 245 4C</p>
                  <p>Office 414</p>
                  <p>Lisbon 1250-143</p>
                  <p>{{ $lang('葡萄牙') }}</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('倫敦') }}</p>
                  <p>{{ $lang('英國') }}</p>
                  <p>{{ $lang('倫敦梅菲爾廣場德文郡大廈') }}</p>
                  <p>W1J 8AJ{{ $lang('主要地址：') }}</p>
                  <p class="phone">+44 20 7514 5252</p>
                  <p>{{ $lang('傳真：') }}+44 20 7514 5250</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('盧森堡') }}</p>
                  <p>13 rue Edward Steichen</p>
                  <p>L-2540</p>
                  <p>{{ $lang('盧森堡') }}</p>
                  <p>{{ $lang('主要地址：') }}+352 27 94 2930</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('馬德里') }}</p>
                  <p>Calle de Serrano n°38</p>
                  <p>{{ $lang('1 樓') }}</p>
                  <p>{{ $lang('馬德里 28001') }}</p>
                  <p>{{ $lang('西班牙') }}</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
                <div class="mapitem">
                  <p class="mapitemtitle">{{ $lang('慕尼黑') }}</p>
                  <p>Maximilianstraße 11</p>
                  <p>80539 München</p>
                  <p>{{ $lang('德國') }}</p>
                  <p>{{ $lang('主要：') }}+49-89244410700</p>
                  <p>{{ $lang('傳真：') }}+49-89244410731</p>
                  <p class="googletext">{{ $lang('Google地圖') }}</p>
                </div>
              </div>
            </div>
            <div class="bottomftr" :class="botAcitve == 1 ? 'absoluteftr' : ''">
              <div>
                <div>
                  © 2012-2026 {{ $lang('貝恩資本有限合夥公司。貝恩資本方形標誌是貝恩資本有限合夥公司的商標。版權所有。') }}</div>
                <div class="ftrtext">
                  <div @click="goLink('https://www.baincapital.com/privacy-policy')">隱私權政策</div>
                  <div @click="goLink('https://www.baincapital.com/terms-use')">使用條款</div>
                  <div @click="goLink('https://www.baincapital.com/regulatory-disclosures')">監理揭露</div>
                  <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning')">
                    詐欺和網路安全警告</div>
                  <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning-chinese')">
                    警告：網路詐騙及網路釣魚</div>
                  <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning-spanish')">
                    網路安全詐欺和廣告</div>
                </div>
              </div>
              <div class="ftricon">
                <div>
                  <i class="fa-brands fa-linkedin-in"></i>
                </div>
                <div><i class="fa-brands fa-twitter"></i>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- <FooterBottom></FooterBottom> -->
  </div>
</template>

<style scoped lang="sass">
// 定義顏色變量
$bg-color: #fefcf6
$text-dark: #1b215a // 接近圖片中的深藍色
$highlight-red: #f06a55 // 圖片中的珊瑚紅/橘紅色

.content-wrapper
  margin: 0 auto
  padding: 0 40px
  color: $text-dark
  @media (max-width: 768px)
    padding: 0
.twotitle
  @media (max-width: 768px)
    font-size: 30px !important
.main-title
  font-size: 3rem
  line-height: 1.4
  font-weight: 500
  margin-bottom: 80px
  text-align: left
  text-align: center
  font-weight: 300
  @media (max-width: 768px)
    font-size: 16px
    margin-bottom: 50px
  .highlight-text
    color: $highlight-red
    font-style: italic
    // display: inline-block
.grid-container
  display: grid
  grid-template-columns: repeat(4, 1fr)
  gap: 40px
  margin-bottom: 60px
  @media (max-width: 768px)
    display: block
  .grid-item
    @media (max-width: 768px)
      margin-bottom: 30px
    h3
      font-size: 26px
      font-weight: 700
      margin-bottom: 40px
      white-space: nowrap // 防止標題換行
      @media (max-width: 768px)
        font-size: 18px
        margin-bottom: 20px
    p
      font-size: 22px
      line-height: 1.8
      opacity: 0.9
      text-align: justify // 讓段落兩端對齊，更有質感
      @media (max-width: 768px)
        font-size: 16px
.bottom-line
  width: 1px
  height: 80px
  background-color: $text-dark
  margin: 40px auto 0
</style>

<style scoped lang="sass">
.bodybox
  min-height: 5000px
  background-color: #fefcf6
  transition: background .3s
  .aboutmimg
    height: 100dvh
    position: relative
    overflow: hidden
    @media (max-width: 768px)
      height: auto
      padding-top: 300px
    .abhimg
      height: 100%
      width: 100%
      object-fit: cover
      @media (max-width: 768px)
        height: 320px
        
    .chaimg
      width: 100%
      position: absolute
      z-index: 1
      top: 80px
      @media (max-width: 768px)
        transform: scale(2) !important
        left: 0
        top: 450px
    .aobtbox
      position: absolute
      left: 100px
      top: 240px
      color: #fff
      font-size: 22px
      width: 600px
      z-index: 2
      @media (max-width: 768px)
        color: #1b215a
        left: 25px
        top: 110px
        font-size: 16px
        width: 90%
      .guanyutit
        margin-bottom: 15px
        font-size: 84px
        @media (max-width: 768px)
          font-size: 50px
          font-weight: 300
  .container
    max-width: 90%
    margin: 0 auto
    margin-top: 100px
    @media (max-width: 768px)
      margin-top: 50px
    .numlook
      color: #1c2156
      font-size: 42px
      font-weight: 300
      @media (max-width: 768px)
        font-size: 25px
      .numbox
        display: flex
        padding: 40px 0
        border-top: 1px solid #cec8c1
        border-bottom: 1px solid #cec8c1
        margin-top: 20px
        @media (max-width: 768px)
          display: block
        .numboxitem
          text-align: center
          width: 25%
          @media (max-width: 768px)
            width: 100%
            margin-top: 30px
            &:first-child
              margin-top: 0
        .numte
          font-size: 100px
          color: #0082ff
          line-height: 100px
          font-family: 'Martinass'
          @media (max-width: 768px)
            font-size: 50px
            line-height: 50px
          span
            font-size: 70px
            font-weight: 400
            line-height: 50px
            @media (max-width: 768px)
              font-size: 35px
        .bote
          color: #1c2156
          font-size: 22px
          margin-top: 20px
          font-weight: 500
          @media (max-width: 768px)
            font-size: 18px
          
    .stitle
      font-size: 84px
      color: #1b215a
      font-weight: 300
      @media (max-width: 768px)
        font-size: 32px
    .ftitle
      font-size: 32px
      margin-top: 210px
      color: #1b215a
      font-weight: 400
      @media (max-width: 768px)
        margin-top: 130px
        font-size: 16px
    .huobancont
      width: 1120px
      margin: 100px auto
      color: #1b215a
      @media (max-width: 768px)
        margin-top: 30px
        width: 100%
        margin-bottom: 50px
      .huobanconttitle
        font-size: 38px
        margin-bottom: 20px
        @media (max-width: 768px)
          font-size: 20px
          font-weight: 300
      .huobanconttexts
        font-size: 22px
        margin-bottom: 30px
        @media (max-width: 768px)
          font-size: 16px
.bluebg
  background-color: #abcae9 !important
  
.tanagram-anim-col
  position: absolute
  top: 0
  right: -10px
  height: 100vh
  display: flex
  align-items: center
  justify-content: center
  padding-right: 0

</style>
<style scoped lang="sass">
html.lenis 
  height: auto


.lenis.lenis-smooth 
  scroll-behavior: auto


.page 
  min-height: 300vh


.block 
  height: 100vh
  display: flex
  align-items: center
  justify-content: center
  font-size: 40px

</style>

<style scoped lang="sass">
.nedju
  justify-content: space-between
.banner-box
  width: 100%
  display: flex
  margin: 100px 0
  margin-bottom: 130px
  @media (max-width: 768px)
    margin: 30px 0
    display: block
  
  .ifbox
    width: 52%
    position: relative
    border-radius: 5px
    overflow: hidden
    margin-left: 120px
    margin-right: 30px
    @media (max-width: 768px)
      width: 100%
      margin: 0
    .player2
      width: 100% !important
      height: 41dvw
      @media (max-width: 768px)
        height: 191px
    .playermr
      height: 410px
      width: 100% 
      @media (max-width: 768px)
        width: 100%
        height: 191px
    .playerbg1
      width: 110% !important
      height: 100%
      object-fit: cover
      position: absolute
      right: 0
      top: 0
      // bottom: 50%
      // transform: translateY(50%)
    .textbg
      position: absolute
      width: 100%
      height: 200px
      background: linear-gradient(to bottom, rgba(0,0,0,0) 0%,rgba(0,0,0,0) 30%, rgba(0,0,0,0.6) 100%)
      left: 0
      bottom: 0
    .textmore
      position: absolute
      bottom: 30px
      left: 40px
      fill: #fff
      color: #fff
      display: flex
      align-items: center
      font-size: 28px
      cursor: pointer
      @media (max-width: 768px)
        bottom: 10px
        left: 15px
        font-size: 16px
      svg
        margin-right: 10px
        @media (max-width: 768px)
          transform: scale(.8)
  .abifsty
    width: 80%
    margin: 0
    @media (max-width: 768px)
      width: 100%
      margin: 0
.yixing
  color: #fff
  margin-top: 200px
  font-weight: 300
  
  
  .map
    padding-bottom: 100px
    position: relative
    min-height: 100dvh
    @media (max-width: 768px)
      margin-top: 400px
      padding-bottom: 30px
    .maplist
      display: flex
      flex-wrap: wrap
      margin-top: 50px
      position: relative
      .nonelineb
        position: absolute
        bottom: 50px
        width: 100%
        height: 3px
        background-color: #164167
        z-index: 99
      .noneliner
        position: absolute
        right: -10px
        height: 100%
        width: 3px
        background-color: #164167
        z-index: 99
      .mapitem
        min-height: 240px
        width: 20%
        font-size: 18px
        font-weight: 400
        border-bottom: 1px solid #1e5e94
        padding-bottom: 50px
        padding-left: 25px
        margin-bottom: 50px
        &::after
          content: ''
          right: -10px
          height: 85%
          // height: calc(100% + 2px)
          width: 1px
          top: 0
          background: #1e5e94
          position: absolute
        &:last-child
          &::after
            height: 0
        .mapitemtitle
          margin-bottom: 10px
          font-weight: 600
        .phone
          margin-top: 25px
        .googletext
          cursor: pointer
          transition: all .3s
          text-decoration: underline
          color: #1ca6df
          &:hover
            color: #fff
    img
      width: 100dvw
    .absolutecls
      position: absolute
      width: 100%
      z-index: 11
      top: 0
    .mapcont
      padding-top: 100px
      @media (max-width: 768px)
        padding-top: 0
        margin-top: -300px
      .maptitlebox
        display: flex
        justify-content: space-between
        align-items: center
        @media (max-width: 768px)
          display: block
      .maptitle
        font-size: 77px
        color: #fff
        @media (max-width: 768px)
          font-size: 32px
      .zhou
        display: flex
        @media (max-width: 768px)
          flex-wrap: wrap
          margin-top: 50px
        div
          cursor: pointer
          margin-left: 40px
          font-size: 22px
          padding-bottom: 5px
          font-weight: 400
          @media (max-width: 768px)
            font-size: 18px
            margin-right: 20px
            margin-left: 0
            padding-top: 5px
            &:first-child
              width: 100%
              margin: 0
        .botacitve
          border-bottom: 3px solid #fff
          font-weight: 600
    .syall
      margin-top: 30px
      span
        color: #a3cbec
    .absoluteftr
      position: absolute
      z-index: 88
      bottom: 130px
    .bottomftr
      padding-top: 30px
      border-top: 1px solid #abcae9
      color: #abcae9
      font-weight: 500
      width: 100%
      display: flex
      justify-content: space-between
      margin-top: 150px
      @media (max-width: 768px)
        display: block
      .ftricon
        display: flex
        @media (max-width: 768px)
          margin-top: 20px
        div
          width: 32px
          height: 32px
          background-color: #1b215a
          border-radius: 50%
          display: flex
          align-items: center
          justify-content: center
          color: #fff
          margin-left: 15px
          transition: all .3s
          cursor: pointer
          font-size: 18px
          @media (max-width: 768px)
            margin-left: 0
            margin-right: 20px
          &:hover
            background-color: #001aff
      .ftrtext
        display: flex
        margin-top: 8px
        @media (max-width: 768px)
          flex-wrap: wrap
        div
          margin-right: 30px
          border-bottom: 1px solid #abcae9
          transition: all .3s
          cursor: pointer
          @media (max-width: 768px)
            margin-top: 5px
          &:hover
            border-bottom: 1px solid transparent !important
  
  
.titlesbox
  z-index: 2
  // font-family: 'Martina Plantijn', serif
  font-size: 45px
  width: 35%
  font-weight: 300
  color: #1b215a
  @media (max-width: 768px)
    width: 100%
  h2
    font-size: 22px
    font-weight: 500
    margin-top: 20px
    @media (max-width: 768px)
      font-size: 16px
      font-weight: 400
  .linkbtn
    color: #001aff
    border: 2px solid #001aff
    padding: 5px 17px
    font-size: 21px
    border-radius: 30px
    font-weight: 500
    display: inline-flex
    align-items: center
    cursor: pointer
    transition: all .3s
    @media (max-width: 768px)
      padding: 3px 17px
      font-size: 14px
      margin-bottom: 40px
    &:hover
      background-color: #001aff
      color: #fff
      .arrow-outline
        fill: #fff
        border: 2px solid #fff
    .arrow-outline
        margin-left: 12px
        width: 21px
        height: 21px
        border: 2px solid #001aff
        border-radius: 50%
        display: flex
        align-items: center
        justify-content: center
        fill: #001aff
        @media (max-width: 768px)
          width: 18px
          height: 18px
    .arrow-round-icon
        background-color: #001aff
        fill: #fff !important
        margin-left: 0
        margin-right: 12px
</style>
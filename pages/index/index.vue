<script lang="ts" setup>
import Lenis from "@studio-freight/lenis"
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
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
const mm = gsap.matchMedia()
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
  // window.addEventListener('resize', checkWidthAndInit)
  rafId = requestAnimationFrame(raf)
  lenis.on("scroll", ({ scroll, limit, direction }) => {

    isWhite.value = scroll >= 100
    if (scroll >= 350) {
      bgcolor.value = '#abcae9 !important'
    }
    if (direction == 1) {
      isTop.value = true
    }
    if (direction == -1) {
      isTop.value = false
    }
    if (scroll < 350) {
      bgcolor.value = '#fefcf6 !important'
    }
    if (scroll >= 350) {
      bgcolor.value = '#abcae9 !important'
    }
    const width = window.innerWidth
    if (width > 768) {
      if (scroll >= 2479) {
        bgcolor.value = '#152d48'
      }
      if (scroll >= 4000) {
        bgcolor.value = '#fefcf5'
      }
      if (scroll >= 5200) {
        bgcolor.value = 'url(@/assets/images/homebg.webp)'
      }
      if (scroll >= 6200) {
        bgcolor.value = '#fefcf5'
      }
      if (scroll >= 7000) {
        if (botAcitve.value == 1) {
          bgcolor.value = '#1e5e94'
        } else {
          bgcolor.value = '#164167'
        }
      }
    } else {
      if (scroll >= 1500) {
        bgcolor.value = '#152d48'
      }
      if (scroll >= 3000) {
        bgcolor.value = '#1e5e94'
      }
    }
  })
  mm.add("(min-width: 700px)", () => {
    const titlesbox = gsap.utils.toArray(".titlesbox");
    titlesbox.forEach((title) => {
      gsap.to(title, {
        y: -300, // 負值代表上浮，數值越大浮動越明顯
        ease: "none", // 必須為 none 才能完美同步滾動條
        scrollTrigger: {
          trigger: title, // 監視這個大容器
          start: "top bottom",    // 當容器頂部進入視窗底部時開始計算
          end: "bottom top",      // 當容器底部離開視窗頂部時結束
          scrub: 1,             // [關鍵參數] 數字代表延遲感。1.5秒的緩動讓它有「懸浮沉降」的感覺
        }
      });
    });
  });

})

onUnmounted(() => {
  cancelAnimationFrame(rafId)
  lenis.destroy()
})
const hideplayerimgbg1 = ref(true)
const hideplayerimgbg2 = ref(true)
const hideplayerimgbg3 = ref(true)
const clyixing = (tye) => {

}
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
</script>

<template>
  <div class="cont">
    <headerTop :top="isTop" :white="isWhite" :opacity="isTop"></headerTop>
    <div :style="{ background: bgcolor }" class="bodybox">
      <banner></banner>
      <div class="container">
        <h1 class="stitle">{{ $lang('將洞察力轉化為優勢') }}</h1>
        <h2 class="ftitle">{{ $lang('我們致力於價值創造之旅，從最初的想法到持久的影響。') }}</h2>
        <div class="banner-box">
          <div class="ifbox">
            <iframe allow="autoplay;" class="player2" muted="" plays-inline=""
              src="https://player.vimeo.com/video/1026850835?api=1&amp;player_id=player2&amp;quality=1080p&amp;autoplay=0"
              frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="">
            </iframe>
            <img v-if="hideplayerimgbg1" class="playerbg1" src="@/assets/images/playerbg1.jpg" alt="">
            <div v-if="hideplayerimgbg1" class="textbg"></div>
            <div v-if="hideplayerimgbg1" @click="hideplayerimgbg1 = false" class="textmore"><svg id="Layer_1"
                xmlns="//www.w3.org/2000/svg" width="25.88" height="25.88" viewBox="0 0 25.88 25.88">
                <path class="cls-1"
                  d="M11.29,19.96l-1.32-1.32.67-.67c2.41-2.41,3.62-3.62,3.62-5.03s-1.21-2.62-3.62-5.03l-.67-.67,1.32-1.32,7.02,7.02-7.02,7.02ZM12.94,0C5.8,0,0,5.8,0,12.94s5.8,12.94,12.94,12.94,12.94-5.8,12.94-12.94S20.07,0,12.94,0">
                </path>
              </svg>{{ $lang('我們不同的合作方式') }}</div>
          </div>
          <h1 class="titlesbox">
            <h1>{{ $lang('不同的合作方式') }}</h1>
            <h2>{{ $lang('我們以不同的方式合作，建立持久的關係，在我們的平台上進行協作，並專注於創造價值，以實現更好的結果。') }}</h2>
          </h1>
        </div>
        <div class="banner-box fan">
          <h1 class="titlesbox">
            <h1>{{ $lang('開啟機遇') }}</h1>
            <h2>{{ $lang('我們匯聚多元視角，追求變革性理念。透過協作文化，我們整合洞見，釋放潛能。') }}</h2>
          </h1>
          <div class="ifbox marle40">
            <iframe allow="autoplay;" class="player2" muted="" plays-inline=""
              src="https://player.vimeo.com/video/1026850705?api=1&amp;player_id=player2&amp;quality=1080p&amp;autoplay=0"
              frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="">
            </iframe>
            <img v-if="hideplayerimgbg2" class="playerbg1" src="@/assets/images/playerbg2.jpg" alt="">
            <div v-if="hideplayerimgbg2" class="textbg"></div>
            <div v-if="hideplayerimgbg2" @click="hideplayerimgbg2 = false" class="textmore"><svg id="Layer_1"
                xmlns="//www.w3.org/2000/svg" width="25.88" height="25.88" viewBox="0 0 25.88 25.88">
                <path class="cls-1"
                  d="M11.29,19.96l-1.32-1.32.67-.67c2.41-2.41,3.62-3.62,3.62-5.03s-1.21-2.62-3.62-5.03l-.67-.67,1.32-1.32,7.02,7.02-7.02,7.02ZM12.94,0C5.8,0,0,5.8,0,12.94s5.8,12.94,12.94,12.94,12.94-5.8,12.94-12.94S20.07,0,12.94,0">
                </path>
              </svg>{{ $lang('我們如何釋放機遇') }}</div>
          </div>
        </div>
        <div class="banner-box">
          <div class="ifbox">
            <iframe allow="autoplay;" class="player2" muted="" plays-inline=""
              src="https://player.vimeo.com/video/1026850567?api=1&amp;player_id=player2&amp;quality=1080p&amp;autoplay=0"
              frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="">
            </iframe>
            <img v-if="hideplayerimgbg3" class="playerbg1" src="@/assets/images/playerbg3.jpg" alt="">
            <div v-if="hideplayerimgbg3" class="textbg"></div>
            <div v-if="hideplayerimgbg3" @click="hideplayerimgbg3 = false" class="textmore"><svg id="Layer_1"
                xmlns="//www.w3.org/2000/svg" width="25.88" height="25.88" viewBox="0 0 25.88 25.88">
                <path class="cls-1"
                  d="M11.29,19.96l-1.32-1.32.67-.67c2.41-2.41,3.62-3.62,3.62-5.03s-1.21-2.62-3.62-5.03l-.67-.67,1.32-1.32,7.02,7.02-7.02,7.02ZM12.94,0C5.8,0,0,5.8,0,12.94s5.8,12.94,12.94,12.94,12.94-5.8,12.94-12.94S20.07,0,12.94,0">
                </path>
              </svg>{{ $lang('我們如何努力創造卓越成果') }}</div>
          </div>
          <h1 class="titlesbox">
            <h1>{{ $lang('創造卓越成果') }}</h1>
            <h2>{{ $lang('我們致力於透過支持員工和提升投資績效來實現卓越成果。我們不斷挑戰自我，力求找到最佳解決方案。') }}</h2>
          </h1>
        </div>
        <div class="yixing">
          <h1 class="ytitle" @click="useyixing = !useyixing">{{ $lang('我們的整合平台') }}</h1>
          <div class="ytext" :style="{ opacity: useyixing ? '0' : '1' }">{{
            $lang('四十多年來，我們透過策略性地發展業務，並擴大業務範圍，以應對日益複雜的投資環境。') }}</div>
          <div class="yixcont">
            <div
              :style="{ transform: 'rotate(' + rotateValue + 'deg)', marginLeft: useyixing ? '0px' : 'calc(50% - 300px)' }"
              class="yixingleft">
              <div class="ganzi"></div>
              <div class="ganzi"></div>
              <div class="ganzi"></div>
              <div class="ganzi"></div>
              <div class="ganzi"></div>
              <img class="pdx" src="@/assets/images/pdx.png" alt="">
              <div :style="{ transform: 'rotate(' + -rotateValue + 'deg)', color: rotateValue == 0 ? '#f0f2f4' : '' }"
                @click="rotateValue = 0, useyixing = true" class="yixingtext yixingtextchengzhang">{{ $lang('成長與創投') }}
              </div>
              <div :style="{ transform: 'rotate(' + -rotateValue + 'deg)', color: rotateValue == -72 ? '#f0f2f4' : '' }"
                @click="rotateValue = -72, useyixing = true" class="yixingtext yixingtextziben">{{ $lang('資本解決方案') }}
              </div>
              <div
                :style="{ transform: 'rotate(' + -rotateValue + 'deg)', color: rotateValue == -144 ? '#f0f2f4' : '' }"
                @click="rotateValue = -144, useyixing = true" class="yixingtext yixingtextxinyong">
                {{ $lang('信用') }}</div>
              <div :style="{ transform: 'rotate(' + -rotateValue + 'deg)', color: rotateValue == 144 ? '#f0f2f4' : '' }"
                @click="rotateValue = 144, useyixing = true" class="yixingtext yixingtextshiti">{{ $lang('實體資產') }}
              </div>
              <div :style="{ transform: 'rotate(' + -rotateValue + 'deg)', color: rotateValue == 72 ? '#f0f2f4' : '' }"
                @click="rotateValue = 72, useyixing = true" class="yixingtext yixingtextsimu">{{ $lang('私募股權') }}</div>
            </div>
            <div :style="{ opacity: useyixing ? '1' : '0', left: useyixing ? '50%' : '100%' }" class="yixingright">
              <div :style="{ opacity: rotateValue == 0 ? '1' : '0', pointerEvents: rotateValue == 0 ? 'auto' : 'none' }"
                class="yxcont">
                <div class="yxrtitle">{{ $lang('成長與創投') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何創造價值') }}</div>
                <div class="yxrtext">{{ $lang('與富有遠見的領導者合作，加速從種子輪到規模化成長。') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何創造價值') }}</div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapital.com/ventures')">{{ $lang('創投') }}<div
                    class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapitallifesciences.com/portfolio')">{{
                  $lang('生命科學') }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapitaltechopportunities.com/')">{{
                  $lang('技術機會') }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapital.com/crypto')">{{ $lang('加密貨幣') }}<div
                    class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
              <div
                :style="{ opacity: rotateValue == -72 ? '1' : '0', pointerEvents: rotateValue == -72 ? 'auto' : 'none' }"
                class="yxcont">
                <div class="yxrtitle">{{ $lang('資本解決方案') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何創造價值') }}</div>
                <div class="yxrtext">{{ $lang('針對不同類型的資產、產業、市場和業務生命週期，建構客製化解決方案。') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何投資') }}</div>
                <div class="yxrlinktext" @click="goLink('https://baincapitalspecialsituations.com/')">{{ $lang('特殊情況')
                }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
              <div
                :style="{ opacity: rotateValue == -144 ? '1' : '0', pointerEvents: rotateValue == -144 ? 'auto' : 'none' }"
                class="yxcont">
                <div class="yxrtitle">{{ $lang('信用') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何創造價值') }}</div>
                <div class="yxrtext">{{ $lang('透過嚴謹的分析和涵蓋整個信貸領域的解決方案，創造投資機會。') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何投資') }}</div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapitalcredit.com/')">{{ $lang('信用') }}<div
                    class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
              <div
                :style="{ opacity: rotateValue == 144 ? '1' : '0', pointerEvents: rotateValue == 144 ? 'auto' : 'none' }"
                class="yxcont">
                <div class="yxrtitle">{{ $lang('實體資產') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何創造價值') }}</div>
                <div class="yxrtext">{{ $lang('建構下一代房地產資產。') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何投資') }}</div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapitalrealestate.com/')">{{ $lang('房地產') }}
                  <div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
                <div class="yxrlinktext" @click="goLink('https://baincapitalspecialsituations.com/')">{{ $lang('特殊情況')
                }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
              <div
                :style="{ opacity: rotateValue == 72 ? '1' : '0', pointerEvents: rotateValue == 72 ? 'auto' : 'none' }"
                class="yxcont">
                <div class="yxrtitle">{{ $lang('私募股權') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何創造價值') }}</div>
                <div class="yxrtext">{{ $lang('憑藉著深厚的產業專業知識與能力，協助企業轉型升級。') }}</div>
                <div class="yxrxtext">{{ $lang('我們如何投資') }}</div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapitalprivateequity.com/')">{{ $lang('全球私募股權')
                }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapitaldoubleimpact.com/')">{{ $lang('雙重衝擊') }}
                  <div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
                <div class="yxrlinktext" @click="goLink('https://www.baincapitalinsurance.com/')">{{ $lang('保險') }}<div
                    class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="yixing">
          <h1 class="ytitle">{{ $lang('垂直聚光燈') }}</h1>
          <div class="jgdcont">
            <div @click="goLink('https://www.baincapital.com/technology/')" class="">
              <div class="lefimgbox" style="overflow: hidden;">
                <img src="@/assets/images/investment-spotlight-tech-v2.jpg" alt="">
              </div>
              <div class="jgdteboxl">
                <div class="keji">{{ $lang('科技') }}</div>
                <div class="kejit">{{ $lang('引領公司邁向未來') }}</div>
              </div>
            </div>
            <div @click="goLink('https://www.baincapital.com/healthcare/')" class="">
              <div class="rigimgbox" style="overflow: hidden;">
                <img src="@/assets/images/investment-spotlight-health-v2.png.jpg" alt="">
              </div>
              <div class="jgdteboxr">
                <div class="keji">{{ $lang('衛生保健') }}</div>
                <div class="kejir">{{ $lang('打造服務病患的偉大公司') }}</div>
              </div>
            </div>
            <div class=""></div>
          </div>
        </div>
        <div class="yixing">
          <div class="yoxucont">
            <div class="yoxule">
              <div class="yoxutitle">{{ $lang('永續性與影響') }}</div>
              <div class="yoxutext">{{ $lang('將永續發展理念融入我們的各項業務組合，將對我們的環境 and 社會產生正面的長期影響。') }}</div>
              <div class="youxuitem" style="font-size: 37px;font-weight: 300;">{{ $lang('我們的核心永續發展承諾') }}</div>
              <div class="youxuitem"
                @click="goLink('https://www.baincapital.com/sustainability-and-impact/active-governance-and-stewardship')"
                @mouseenter="indexbannerAcitve = 1" @mouseleave="indexbannerAcitve = 0">{{ $lang('積極的治理與管理') }}
                <div class="arrow-outline">
                  <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17" viewBox="0 0 6.63 11.17">
                    <path class="arrow-icon"
                      d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                    </path>
                  </svg>
                </div>
              </div>
              <div class="youxuitem"
                @click="goLink('https://www.baincapital.com/sustainability-and-impact/sustainable-growth-reducing-climate-impact')"
                @mouseenter="indexbannerAcitve = 2" @mouseleave="indexbannerAcitve = 0">{{ $lang('永續成長和減少氣候影響') }}
                <div class="arrow-outline">
                  <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17" viewBox="0 0 6.63 11.17">
                    <path class="arrow-icon"
                      d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                    </path>
                  </svg>
                </div>
              </div>
              <div class="youxuitem"
                @click="goLink('https://www.baincapital.com/sustainability-and-impact/fair-employment-engagement-well-being')"
                @mouseenter="indexbannerAcitve = 3" @mouseleave="indexbannerAcitve = 0">{{ $lang('公平就業、參與和福祉') }}
                <div class="arrow-outline">
                  <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17" viewBox="0 0 6.63 11.17">
                    <path class="arrow-icon"
                      d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                    </path>
                  </svg>
                </div>
              </div>
              <div class="youxuitem"
                @click="goLink('https://www.baincapital.com/sustainability-and-impact/diversity-equity-and-inclusion')"
                @mouseenter="indexbannerAcitve = 4" @mouseleave="indexbannerAcitve = 0">{{ $lang('多元化、公平性和包容性') }}
                <div class="arrow-outline">
                  <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17" viewBox="0 0 6.63 11.17">
                    <path class="arrow-icon"
                      d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                    </path>
                  </svg>
                </div>
              </div>
              <div class="youxuitem"
                @click="goLink('https://www.baincapital.com/sustainability-and-impact/community-engagement')"
                @mouseenter="indexbannerAcitve = 5" @mouseleave="indexbannerAcitve = 0">{{ $lang('社區參與') }}<div
                  class="arrow-outline">
                  <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17" viewBox="0 0 6.63 11.17">
                    <path class="arrow-icon"
                      d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                    </path>
                  </svg>
                </div>
              </div>
            </div>
            <div class="yoxuri">
              <img v-if="indexbannerAcitve == 0" src="@/assets/images/indexbanner0.jpg" alt="">
              <img v-if="indexbannerAcitve == 1" src="@/assets/images/indexbanner1.jpg" alt="">
              <img v-if="indexbannerAcitve == 2" src="@/assets/images/indexbanner2.jpg" alt="">
              <img v-if="indexbannerAcitve == 3" src="@/assets/images/indexbanner3.jpg" alt="">
              <img v-if="indexbannerAcitve == 4" src="@/assets/images/indexbanner4.jpg" alt="">
              <img v-if="indexbannerAcitve == 5" src="@/assets/images/indexbanner5.jpg" alt="">
              <div @click="indexbannerAcitveup(true)" class="lejian" style="left: -40px;">
                <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="15.04" height="26.54" viewBox="0 0 15.04 26.54">
                  <path class="cls-1"
                    d="M14.15,23.88c-5-5-7.5-7.5-7.5-10.61s2.5-5.61,7.5-10.61l.89-.89-1.77-1.77L0,13.27l13.27,13.27,1.77-1.77-.89-.89Z">
                  </path>
                </svg>
              </div>
              <div @click="indexbannerAcitveup(false)" class="lejian rijian"
                style="position: absolute;right: -35px !important;">
                <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="15.04" height="26.54" viewBox="0 0 15.04 26.54">
                  <path class="cls-1"
                    d="M.89,23.88c5-5,7.5-7.5,7.5-10.61S5.89,7.66.89,2.66l-.89-.89L1.77,0l13.27,13.27L1.77,26.54l-1.77-1.77.89-.89Z">
                  </path>
                </svg>
              </div>
              <div v-if="indexbannerAcitve == 0" class="botcont" style="padding-top: 70px;">
                <div class="bottitle">{{ $lang('創造永續價值') }}</div>
                <div class="botbtn"
                  @click="goLink('https://cdn-east2.baincapital.com/2025-06/Bain-Capital-Sustainability-Report-June2025_0.pdf?VersionId=g_eEXbw1xbuP1q8YuljPD5jzIevSVKpu')"
                  style="color: #1b215a;background-color: #dcf54e">{{ $lang('2025年永續發展報告') }}
                  <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="16" height="15.19" viewBox="0 0 16 15.19">
                    <path class="cls-1"
                      d="M15,10.19c-.55,0-1,.45-1,1v1.2c0,.44-.36.8-.81.8H2.8c-.44,0-.8-.36-.8-.8v-1.2c0-.55-.45-1-1-1s-1,.45-1,1v2c0,.55.2,1.02.59,1.41.39.39.86.59,1.41.59h12c.55,0,1.02-.2,1.41-.59.39-.39.59-.86.59-1.41v-2c0-.55-.45-1-1-1">
                    </path>
                    <path class="cls-1"
                      d="M8,11l5-5h0c.4-.39.41-1.02.02-1.42-.39-.4-1.02-.41-1.42-.03l-2.6,2.6V1c0-.55-.45-1-1-1s-1,.45-1,1v6.15l-2.6-2.6c-.4-.39-1.04-.37-1.42.03-.39.4-.37,1.03.03,1.42l5,5Z">
                    </path>
                  </svg>
                </div>
              </div>
              <div v-if="indexbannerAcitve == 1" class="botcont">
                <div class="bottitle">{{ $lang('積極的治理與管理') }}</div>
                <div class="bottext">{{ $lang('為了促進積極參與的治理，我們將與投資組合公司和管理團隊合作，秉持高度誠信，對創造價值負責。') }}</div>
                <div class="botbtn"
                  @click="goLink('https://www.baincapital.com/sustainability-and-impact/active-governance-and-stewardship')">
                  {{ $lang('探索承諾') }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
              <div v-if="indexbannerAcitve == 2" class="botcont">
                <div class="bottitle">{{ $lang('永續成長和減少氣候影響') }}</div>
                <div class="bottext">{{ $lang('為了減少排放並提高資源利用效率，我們將永續發展理念融入公司營運中，並嚴格衡量其隨時間推移所產生的影響。') }}</div>
                <div class="botbtn"
                  @click="goLink('https://www.baincapital.com/sustainability-and-impact/sustainable-growth-reducing-climate-impact')">
                  {{ $lang('探索承諾') }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
              <div v-if="indexbannerAcitve == 3" class="botcont">
                <div class="bottitle">{{ $lang('公平就業、參與和福祉') }}</div>
                <div class="bottext">{{ $lang('為了公平、尊重地對待員工，我們需要創造一個以員工安全、福祉和敬業度為核心的環境和文化。') }}</div>
                <div class="botbtn"
                  @click="goLink('https://www.baincapital.com/sustainability-and-impact/fair-employment-engagement-well-being')">
                  {{ $lang('探索承諾') }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
              <div v-if="indexbannerAcitve == 4" class="botcont">
                <div class="bottitle">{{ $lang('多元化、公平性和包容性') }}</div>
                <div class="bottext">{{ $lang('倡導多元化和包容性，並透過培養高績效文化推動有意義的進步。') }}</div>
                <div class="botbtn"
                  @click="goLink('https://www.baincapital.com/sustainability-and-impact/diversity-equity-and-inclusion')">
                  {{ $lang('探索承諾') }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
              <div v-if="indexbannerAcitve == 5" class="botcont">
                <div class="bottitle">{{ $lang('社區參與') }}</div>
                <div class="bottext">{{ $lang('為了鼓勵和支持我們旗下公司積極參與並貢獻於其所在社區，無論是在本地還是在全球範圍內。') }}</div>
                <div class="botbtn"
                  @click="goLink('https://www.baincapital.com/sustainability-and-impact/community-engagement')">{{
                    $lang('探索承諾') }}<div class="arrow-outline">
                    <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                      viewBox="0 0 6.63 11.17">
                      <path class="arrow-icon"
                        d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                      </path>
                    </svg>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="yixing" style="margin-top: 100px;">
          <div class="zhuoyue">
            <div class="zhuoyuecont">
              <div class="zytitle"><span>{{ $lang('卓越的團隊') }}</span>{{ $lang('才能取得卓越的成果。') }}</div>
              <div class="zytext">{{ $lang('我們互相激勵，以不同的方式思考和工作，從而創造有意義且持久的影響。') }}</div>
              <div class="zybtn">{{ $lang('認識我們的團隊成員') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="12.63"
                  height="18.17" viewBox="0 0 6.63 11.17">
                  <path
                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                  </path>
                </svg></div>
            </div>
            <div class="namebox"><span style="color: #26698a;">{{ $lang('阿姆里塔·桑卡爾') }}</span> / {{ $lang('永續發展與影響力總監')
            }} / {{ $lang('波士頓') }}</div>
          </div>
        </div>
        <div class="yixing">
          <div class="newsbox">
            <div class="nele">
              <h1 class="neletitle">{{ $lang('最新消息') }}</h1>
              <img src="@/assets/images/HSO 2.jpg" alt="">
              <div class="timetext"><span style="color: #001aff;">{{ $lang('新聞稿') }} /</span> {{ $lang('私募股權') }} / {{
                $lang('2025年8月13日') }}</div>
              <div class="newtext">{{ $lang('貝恩資本將投資HSO，該公司是微軟雲端和人工智慧商業應用領域的全球領導者') }}</div>
            </div>
            <div class="neri">
              <div class="timetext"><span style="color: #001aff;">{{ $lang('新聞稿') }} /</span> {{ $lang('特殊情況') }} / {{
                $lang('2026年3月18日') }}</div>
              <div class="neritext">{{ $lang('通風和空氣品質解決方案領導者 Duravent 集團獲得貝恩資本的策略性成長投資') }}</div>
              <div class="timetext"><span style="color: #001aff;">{{ $lang('新聞稿') }} /</span> {{ $lang('私募股權') }} / {{
                $lang('2026年3月16日') }}</div>
              <div class="neritext">{{ $lang('貝恩資本將收購永續財富管理公司') }}</div>
              <div class="timetext"><span style="color: #001aff;">{{ $lang('新聞稿') }} /</span> {{ $lang('私募股權') }} / {{
                $lang('2026年3月2日') }}</div>
              <div class="neritext">{{ $lang('貝恩資本宣布投資瑞典領先的非食品消費品分銷商Tingstad') }}</div>
              <div class="timetext"><span style="color: #001aff;">{{ $lang('新聞稿') }} /</span> {{ $lang('信用') }} / {{
                $lang('2026年2月26日') }}</div>
              <div class="neritext">{{ $lang('貝恩資本專業金融公司公佈截至2025年12月31日的財務業績，並宣布2026年第一季每股派息042美元。') }}</div>
              <div class="timetext"><span style="color: #001aff;">{{ $lang('新聞稿') }} /</span> {{ $lang('信用') }} / {{
                $lang('2026年2月20日') }}</div>
              <div class="neritext">{{ $lang('Fluent Commerce 從貝恩資本獲得 4,600 萬澳元投資，加速下一階段成長') }}</div>
              <div class="zybtn">{{ $lang('查看所有新聞') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="12.63"
                  height="18.17" viewBox="0 0 6.63 11.17">
                  <path
                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                  </path>
                </svg></div>
            </div>
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
                  {{ $lang('© 2012-2026 貝恩資本有限合夥公司。貝恩資本方形標誌是貝恩資本有限合夥公司的商標。版權所有。') }}</div>
                <div class="ftrtext">
                  <div @click="goLink('https://www.baincapital.com/privacy-policy')">{{ $lang('隱私權政策') }}</div>
                  <div @click="goLink('https://www.baincapital.com/terms-use')">{{ $lang('使用條款') }}</div>
                  <div @click="goLink('https://www.baincapital.com/regulatory-disclosures')">{{ $lang('監理揭露') }}
                  </div>
                  <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning')">
                    {{ $lang('詐欺和網路安全警告') }}</div>
                  <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning-chinese')">
                    {{ $lang('警告：網路詐騙及網路釣魚') }}</div>
                  <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning-spanish')">
                    {{ $lang('網路安全詐欺和廣告') }}</div>
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
.bodybox
  min-height: 5000px
  background-color: #fefcf6
  transition: background .3s
  overflow: hidden
  // background: url(@/assets/images/homebg.webp) !important
  .container
    width: 90%
    margin: 0 auto
    margin-top: 750px
    overflow: hidden
    // @media (max-width: 768px)
    //   width: 100%
    //   padding: 0 25px
    .stitle
      font-size: 84px
      color: #1b215a
      font-weight: 300
      @media (max-width: 768px)
        font-size: 36px
    .ftitle
      font-size: 32px
      margin-top: 30px
      color: #1b215a
      font-weight: 300
      @media (max-width: 768px)
        font-size: 20px
        margin-top: 12px
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
<style>
html.lenis {
  height: auto;
}

.lenis.lenis-smooth {
  scroll-behavior: auto;
}

.block {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40px;
}
</style>

<style scoped lang="sass">
.fan
  @media (max-width: 768px)
    flex-direction: column-reverse !important
.banner-box
  width: 100%
  display: flex
  align-items: center
  margin: 100px 0
  margin-bottom: 130px
  @media (max-width: 768px)
    flex-wrap: wrap
    margin: 20px 0
  .marle40
    margin-left: 40px
    @media (max-width: 768px)
      margin-left: 0
  .ifbox
    width: 42%
    position: relative
    border-radius: 5px
    overflow: hidden
    margin-left: 100px
    margin-right: 30px
    @media (max-width: 768px)
      width: 100%
      margin: 0
    .player2
      width: 100% !important
      height: 415px
      @media (max-width: 768px)
        height: 191px
    .playerbg1
      width: 110% !important
      height: 100%
      object-fit: cover
      position: absolute
      right: 0
      bottom: 50%
      transform: translateY(50%)
    .textbg
      position: absolute
      width: 100%
      height: 200px
      background: linear-gradient(to bottom, rgba(0,0,0,0) 0%,rgba(0,0,0,0) 30%, rgba(0,0,0,0.6) 100%)
      left: 0
      bottom: 0
      @media (max-width: 768px)
        height: 191px
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
        left: 15px
        bottom: 10px
        font-size: 16px
      svg
        margin-right: 10px
        @media (max-width: 768px)
          transform: scale(.8)
          margin-right: 7px
.yixing
  color: #fff
  margin-top: 200px
  font-weight: 300
  @media (max-width: 768px)
    margin-top: 100px
  .ytitle
    font-size: 76px
    @media (max-width: 768px)
      font-size: 32px
  .jgdcont
    display: flex
    gap: 20px
    margin-top: 20px
    font-size: 33px
    cursor: pointer
    @media (max-width: 768px)
      display: block
      font-size: 24px
    .lefimgbox
      @media (max-width: 768px)
        width: 263px
        height: 312px
        margin-left: -30px
        border-radius: 5px
        img
          height: 312px
          object-fit: cover
    .rigimgbox
      @media (max-width: 768px)
        margin-top: 40px
        width: 263px
        height: 312px
        margin-left: auto
        margin-right: -30px
        border-radius: 5px
        img
          height: 312px
          object-fit: cover
    .jgdteboxl
      @media (max-width: 768px)
        position: absolute
        left: 50%
        top: 20px
    .jgdteboxr
      @media (max-width: 768px)
        position: absolute
        left: 0px
        top: 20px

    .lefimgbox
    .keji
      font-size: 16.5px
      font-weight: 600
      color: #77b2f9
      margin-top: 20px
      margin-bottom: 5px
      @media (max-width: 768px)
        font-size: 12px
    img
      width: 100%
      transition: all .5s
      &:hover
        transform: scale(1.1)
  .zhuoyue
    position: relative
    display: flex
    align-items: center
    height: 100dvh
    @media (max-width: 768px)
      display: none
    .zhuoyuecont
      width: 45%
      color: #fff
      

      .zytitle
        font-size: 74px
        span
          font-style: italic
      .zytext
        font-size: 28px
        margin: 20px 0
      .zybtn
        color: #3fb6ff
        border: 2px solid #3fb6ff
        border-radius: 30px
        padding: 5px 17px
        display: inline-flex
        align-items: center
        font-size: 21px
        font-weight: 500
        fill: #3fb6ff
        cursor: pointer
        transition: all .3s
        @media (max-width: 768px)
          font-size: 14px
        &:hover
          background-color: #3fb6ff
          color: #fff
          fill: #fff
    .namebox
      background-color: #d5cfce
      position: absolute
      right: 0
      bottom: 100px
      padding: 6px 16px
      color: #1b215a
      font-weight: 400
      border-radius: 5px
  .newsbox
    display: flex
    @media (max-width: 768px)
      display: block
    .timetext
      color: #716e6a
      margin-top: 30px
      font-weight: 600
      font-size: 17px
      @media (max-width: 768px)
        font-size: 12px
    .nele
      width: 70%
      border-right: 1px solid #dedcd5
      padding-right: 70px
      @media (max-width: 768px)
        width: 100%
        border-right: none
        border-bottom: 1px solid #dedcd5
        padding: 0
        padding-bottom: 30px
      .neletitle
        font-size: 77px
        margin-bottom: 30px
        color: #1b215a
        @media (max-width: 768px)
          font-size: 32px
          margin-bottom: 20px
      img
        width: 90%
        border-radius: 5px
        @media (max-width: 768px)
          width: 100%
      
      .newtext
        font-size: 32px
        font-weight: 200
        transition: all .3s
        color: #1c2156
        @media (max-width: 768px)
          font-size: 24px
        &:hover
          color: #0047bb
    .neri
      padding-left: 80px
      @media (max-width: 768px)
        padding: 40px 8px
      .neritext
        font-size: 25px
        color: #1c2156
        width: 80%
        transition: all .3s
        @media (max-width: 768px)
          width: 100%
          font-size: 18px
        &:hover
          color: #0047bb
      .zybtn
        margin-top: 50px
        color: #001aff
        border: 2px solid #001aff
        border-radius: 30px
        padding: 5px 17px
        display: inline-flex
        align-items: center
        font-size: 21px
        font-weight: 500
        fill: #001aff
        cursor: pointer
        transition: all .3s
        @media (max-width: 768px)
          font-size: 14px
        svg
          margin-left: 5px
          @media (max-width: 768px)
            transform: scale(0.6)
            margin-left: 0
        &:hover
          background-color: #001aff
          color: #fff
          fill: #fff
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
      font-size: 16px !important
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
  .yoxucont
    display: flex
    gap: 70px
    color: #1b215a
    @media (max-width: 768px)
      display: block
    .yoxule
      width: 50%
      @media (max-width: 768px)
        width: 100%
    .yoxuri
      width: 50%
      aspect-ratio: 1 / 1
      border-radius: 5px
      position: relative
      @media (max-width: 768px)
        width: 100dvw
        margin-left: -20px
        height: 512px
      img
        height: 100%
        object-fit: cover
      .lejian
        position: absolute
        top: 50%
        transform: translateY(-50%)
        opacity: .5
        margin-left: 7px
        transition: all .3s
        width: 48px
        height: 48px
        border: 3px solid #1b215a
        border-radius: 50%
        display: flex
        align-items: center
        justify-content: center
        fill: #1b215a
        cursor: pointer
        @media (max-width: 768px)
          display: none
        &:hover
          background-color: #1b215a
          fill: #fff
          opacity: 1
      .botcont
        height: 250px
        width: 100%
        background: linear-gradient(to bottom, rgba(0,0,0,0) 0%,rgba(0,0,0,0.6) 30%, rgba(0,0,0,0.82) 100%)
        position: absolute
        bottom: 0
        z-index: 11
        padding-left: 50px
        padding-bottom: 40px
        color: #fff
        @media (max-width: 768px)
          padding-left: 20px
          padding-top: 30px
          height: 200px
        .bottitle
          font-size: 48px
          margin-bottom: 20px
          @media (max-width: 768px)
            font-size: 30px
        .bottext
          font-weight: 500
          width: 80%
          font-size: 18px
          margin-bottom: 20px
        .botbtn
          font-size: 20px
          color: #001aff
          background-color: #fff
          padding: 5px 16px
          border-radius: 20px
          display: inline-flex
          align-items: center
          font-weight: 500
          cursor: pointer
          @media (max-width: 768px)
            font-size: 14px
            svg
              transform: scale(0.8)
          .arrow-outline
            margin-left: 7px
            transition: all .3s
            width: 20px
            height: 20px
            border: 2px solid #001aff
            border-radius: 50%
            display: flex
            align-items: center
            justify-content: center
            fill: #001aff
    .yoxutitle
      font-size: 74px
      @media (max-width: 768px)
        font-size: 32px
    .yoxutext
      font-size: 26.6px
      margin-top: 30px
      margin-bottom: 100px
      @media (max-width: 768px)
        font-size: 16px
    .youxuitem
      font-size: 24.6px
      border-bottom: 1px solid #cec8c1
      padding: 16.4px
      font-weight: 500
      display: flex
      align-items: center
      cursor: pointer
      @media (max-width: 768px)
        display: none
      &:hover
        .arrow-outline
          background-color: #1b215a
          fill: #fff
      .arrow-outline
        margin-left: 7px
        transition: all .3s
        width: 24px
        height: 24px
        border: 2px solid #1b215a
        border-radius: 50%
        display: flex
        align-items: center
        justify-content: center
        fill: #1b215a
  .ytext
    margin-top: 30px
    width: 310px
    font-size: 22px
    transition: all .5s
    @media (max-width: 768px)
      font-size: 16px
      margin-top: 20px
      opacity: 1 !important
  .yixcont
    width: 100%
    display: flex
    margin: 0 auto
    width: 100%
    position: relative
    // transition: all 2s
  .yixingleft
    width: 600px
    height: 600px
    position: relative
    fill: #0082ff
    transition: all .5s
    margin: 0 auto
    margin-top: -100px
    @media (max-width: 768px)
      width: 360px
      height: 360px
      margin: 0 auto !important
      margin-top: 10px
    .pdx
      position: absolute
      width: 54px
      height: 54px
      top: 50%
      left: 50%
      transform: translate(-44%,-53%)
      @media (max-width: 768px)
        width: 30px
        height: 30px
      // opacity: 0
    .ganzi
      position: absolute
      width: 6px
      height: 300px
      border-radius: 2px
      background-color: #0082ff
      top: 0
      left: 50%
      transform: translateX(-50%)
      z-index: 11
      transform-origin: center bottom
      &:nth-child(1)
        transform: rotate(0deg)
      &:nth-child(2)
        transform: rotate(72deg)
      &:nth-child(3)
        transform: rotate(144deg)
      &:nth-child(4)
        transform: rotate(216deg)
      &:nth-child(5)
        transform: rotate(288deg)
      @media (max-width: 768px)
        width: 3px
        height: 180px
    .yixingtext
      color: #296d9d
      font-size: 34px
      position: absolute
      text-align: center
      transition: all .5s
      cursor: pointer
      @media (max-width: 768px)
        font-size: 18px
      &:hover
        color: #55708d
      &:focus
        color: #fff
    .yixingtextchengzhang
      top: 80px
      left: 350px
      @media (max-width: 768px)
        top: 50px
        left: 210px
    .yixingtextziben
      top: 300px
      left: 430px
      @media (max-width: 768px)
        top: 190px
        width: 80px
        left: 240px
    .yixingtextxinyong
      top: 500px
      left: calc( 50% - 30px)
      @media (max-width: 768px)
        top: 300px
        left: calc( 50% - 14px)
    .yixingtextshiti
      top: 330px
      left: 30px
      @media (max-width: 768px)
        top: 200px
        left: 20px
    .yixingtextsimu
      top: 80px
      left: 100px
      @media (max-width: 768px)
        top: 50px
        left: 50px
  .yixingright
    width: 50%
    padding-right: 50px
    margin-left: 50px
    margin-top: -100px
    opacity: 0
    transition: all .5s
    pointer-events: none
    position: absolute
    right: -50%
    @media (max-width: 768px)
      margin-left: 100%
      width: 100%
    .yxrtitle
      font-size: 41px
      font-weight: 300
    .yxrxtext
      font-size: 18px
      color: #4e8dc4
      margin-top: 60px
      padding-top: 8px
      border-top: 1px solid #4e8dc4
    .yxrtext
      font-size: 21px
      margin-top: 15px
    .yxrlinktext
      margin-top: 25px
      font-size: 24px
      display: flex
      align-items: center
      cursor: pointer
      transition: all .5s
      &:hover
        color: #3fb6ff !important
        .arrow-outline
          fill: #3fb6ff
          border: 2px solid #3fb6ff
      .arrow-outline
        margin-left: 12px
        transition: all .5s
        width: 21px
        height: 21px
        border: 2px solid #fff
        border-radius: 50%
        display: flex
        align-items: center
        justify-content: center
        fill: #fff
    .yxcont
      position: absolute
      transition: all .3s
      width: 90%
.titlesbox
  z-index: 2
  // font-family: 'Martina Plantijn', serif
  font-size: 45px
  width: 40%
  font-weight: 300
  color: #1b215a
  @media (max-width: 768px)
    width: 100%
    font-size: 30px
    margin-top: 20px
  h2
    font-size: 22px
    font-weight: 500
    margin-top: 20px
    @media (max-width: 768px)
      font-size: 16px
      margin-top: 10px
</style>
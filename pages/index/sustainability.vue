<script lang="ts" setup>
import Lenis from "@studio-freight/lenis"
import { gsap } from 'gsap'
import anime from '~/components/game/js/anime.es.js'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import avatar1 from '@/assets/images/Jonathan-Lavine.jpg'
import avatar2 from '@/assets/images/John-Connaughton.jpg'
import avatar3 from '@/assets/images/David Gross.jpg'
import avatar4 from '@/assets/images/Tricia-Winton.jpg'
import avatar5 from '@/assets/images/AjayAgarwa.jpeg'
import avatar6 from '@/assets/images/Nancy-Lotane-impact.jpg'
import avatar7 from '@/assets/images/square.jpg'
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
const isStartnum = ref(false)
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

    rafId = requestAnimationFrame(raf)
    lenis.on("scroll", ({ scroll, limit, direction }) => {
        isWhite.value = scroll >= 100
        if (direction == 1) {
            isTop.value = true
        }
        if (direction == -1) {
            isTop.value = false
        }
        const width = window.innerWidth
        if (width > 768) {
            if (scroll <= 6200) {
                isStartnum.value = true
                dataNumber.value = {
                    1: 0,
                    2: 0,
                }
            }

            if (scroll > 6200 && isStartnum.value) {
                isStartnum.value = false
                dwakjhhd()
            }
        } else {
            if (scroll <= 5200) {
                isStartnum.value = true
                dataNumber.value = {
                    1: 0,
                    2: 0,
                }
            }

            if (scroll > 5200 && isStartnum.value) {
                isStartnum.value = false
                dwakjhhd()
            }
        }
    })
    mm.add("(min-width: 700px)", () => {
        const titlesbox = gsap.utils.toArray(".titlesbox");
        titlesbox.forEach((title) => {
            gsap.to(title, {
                y: -200, // 負值代表上浮，數值越大浮動越明顯
                ease: "none", // 必須為 none 才能完美同步滾動條
                scrollTrigger: {
                    trigger: title, // 監視這個大容器
                    start: "top bottom",    // 當容器頂部進入視窗底部時開始計算
                    end: "bottom top",      // 當容器底部離開視窗頂部時結束
                    scrub: 1,             // [關鍵參數] 數字代表延遲感。1.5秒的緩動讓它有「懸浮沉降」的感覺
                }
            });
        });
        gsap.to('.jccha', {
            y: 200, // 負值代表上浮，數值越大浮動越明顯
            ease: "none", // 必須為 none 才能完美同步滾動條
            scrollTrigger: {
                trigger: '.jingcaibox', // 監視這個大容器
                start: "top bottom",    // 當容器頂部進入視窗底部時開始計算
                end: "bottom top",      // 當容器底部離開視窗頂部時結束
                scrub: 1,             // [關鍵參數] 數字代表延遲感。1.5秒的緩動讓它有「懸浮沉降」的感覺
            }
        });
    });
})

onUnmounted(() => {
    cancelAnimationFrame(rafId)
    lenis.destroy()
})
const goLink = (link) => {
    window.open(link)
}
const isTop = ref(false)
const isWhite = ref()


const testimonials = [
    {
        name: '約翰·康諾頓',
        title: '椅子 / 波士頓',
        quote: '我們致力於創造持久的影響力。我們的成就既體現在我們的行動上，也體現在我們執行行動的方式上——我們堅定地秉持核心價值和目標，重視員工及其專業技能的培養，並始終不渝地重視我們的企業文化。',
        img: avatar2
    },
    {
        name: '大衛‧格羅斯',
        title: '管理合夥人 / 波士頓',
        quote: '將永續發展理念融入我們的投資，有助於我們發掘價值創造機遇，並產生持久影響。我們秉持宗旨和價值觀，致力於打造更強大、更有韌性、更負責任的企業，以實現長期發展。',
        img: avatar3
    },
    {
        name: '喬納森·拉文',
        title: '資深顧問合夥人 / 波士頓',
        quote: '我們積極主動的投資策略和對永續性的重視，有助於我們提升投資品質和投資回報。我們致力於加強公司治理和監管，投資於人才培養，並建立長期可持續的商業模式。',
        img: avatar1
    }
]
const testimonials2 = [
    {
        name: '崔西亞·溫頓',
        title: '合夥人 / 永續發展與影響力負責人 / 波士頓',
        quote: '我們致力於將永續發展最佳實踐融入我們的平台和投資項目中，從而幫助我們降低風險並提升績效。我們相信，增強永續性和韌性對於我們投資的長期成功至關重要。',
        img: avatar4
    },
    {
        name: '阿傑·阿加瓦爾',
        title: '合夥人 / 創投 / 舊金山',
        quote: '我們相信，人才是我們投資的早期新創公司長期成功的關鍵。因此，創造發展機會並保持員工的積極性至關重要。我們看到了一個絕佳的機會，可以支持創辦人及領導者建立促進員工成長和福祉的卓越企業文化。',
        img: avatar5
    },
    {
        name: '南希·洛坦',
        title: '合夥人 / 人力資源官 / 波士頓',
        quote: '我們的團隊以及我們投資組合公司的員工是我們最大的財富。我們鼓勵團隊跳出思維定式，挑戰傳統觀念，以便在所有工作中創造有意義且持久的影響力。',
        img: avatar6
    },
    {
        name: '麥可·沃德',
        title: '合夥人 / 營運長兼財務官 / 波士頓',
        quote: '我們將永續性融入我們的平台和投資中，以創造可擴展的影響，專注於我們可以在獲得有意義、可衡量的結果的同時，實現強勁回報的領域。',
        img: avatar7
    }
]
const dataNumber = ref({
    1: 0,
    2: 0,
})
const dwakjhhd = () => {
    anime({
        easing: 'easeInOutSine',
        targets: dataNumber.value,
        1: 250,
        2: 84,
        round: 1,
        duration: 1000
    })
}
</script>

<template>
    <div class="cont">
        <headerTop :top="isTop" :white="true" :opacity="isTop"></headerTop>
        <div class="bodybox">
            <div class="aboutmimg">
                <img src="@/assets/images/esg-banner-triangle.png" alt="">
                <div class="aobtbox">
                    <div class="abtottile">{{ $lang('我們從整體角度考慮回報。') }}
                    </div>
                    <div class="adbtotext">
                        {{
                            $lang('我們相信，透過我們自身的特質、價值觀和參與方式，我們可以創造持久且可擴展的影響力。我們天生就是批判性思考者、問題解決者和實踐者。我們相信，應對時代挑戰有助於我們創造價值並獲得可觀的回報。鑑於當前全球挑戰的緊迫性和嚴重性，我們深受鼓舞，決心做得更多。我們承諾，在履行受託責任、為投資者尋求可觀回報的前提下，積極應對風險並掌握潛在收益。')
                        }}
                    </div>
                    <div @click="goLink('https://cdn-east2.baincapital.com/2025-06/Bain-Capital-Sustainability-Report-June2025_0.pdf?VersionId=g_eEXbw1xbuP1q8YuljPD5jzIevSVKpu')"
                        class="linkbtn">
                        {{ $lang('2025年永續發展報告') }}
                        <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="16" height="15.19"
                            viewBox="0 0 16 15.19">
                            <path class="cls-1"
                                d="M15,10.19c-.55,0-1,.45-1,1v1.2c0,.44-.36.8-.81.8H2.8c-.44,0-.8-.36-.8-.8v-1.2c0-.55-.45-1-1-1s-1,.45-1,1v2c0,.55.2,1.02.59,1.41.39.39.86.59,1.41.59h12c.55,0,1.02-.2,1.41-.59.39-.39.59-.86.59-1.41v-2c0-.55-.45-1-1-1">
                            </path>
                            <path class="cls-1"
                                d="M8,11l5-5h0c.4-.39.41-1.02.02-1.42-.39-.4-1.02-.41-1.42-.03l-2.6,2.6V1c0-.55-.45-1-1-1s-1,.45-1,1v6.15l-2.6-2.6c-.4-.39-1.04-.37-1.42.03-.39.4-.37,1.03.03,1.42l5,5Z">
                            </path>
                        </svg>
                    </div>
                </div>
            </div>
            <peopleSwiper :data="testimonials"></peopleSwiper>
            <div class="container">
                <h1 class="stitle">{{ $lang('我們的核心永續發展承諾') }}</h1>
                <h2 class="ftitle">{{ $lang('我們積極考慮與永續發展相關的因素，並將工作重點放在我們認為能夠產生有意義、可衡量的長期影響的五個關鍵領域。') }}
                </h2>
                <div class="banner-box">
                    <img class="playerbg1 marle100" src="@/assets/images/indexbanner1.jpg" alt="">
                    <div class="titlesbox marle50">
                        <h1>{{ $lang('積極的治理與管理') }}</h1>
                        <h2>{{ $lang('為了促進積極參與的治理，我們將與投資組合公司和管理團隊合作，秉持高度誠信，對創造價值負責。') }}</h2>
                        <div class="zybtn">{{ $lang('探索') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63"
                                height="14.17" viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                    </div>
                </div>
                <div class="banner-box diandao">
                    <div class="titlesbox marri50">
                        <h1>{{ $lang('永續成長和減少氣候影響') }}</h1>
                        <h2>{{ $lang('我們將透過將永續發展理念融入公司運營，並嚴格衡量其長期影響，來減少排放並提高資源利用效率。') }}</h2>
                        <div class="zybtn">{{ $lang('探索') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63"
                                height="14.17" viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                    </div>
                    <img class="playerbg1" src="@/assets/images/indexbanner2.jpg" alt="">
                </div>
                <div class="banner-box">
                    <img class="playerbg1" src="@/assets/images/indexbanner3.jpg" alt="">
                    <div class="titlesbox marle50">
                        <h1>{{ $lang('公平就業、參與和福祉') }}</h1>
                        <h2>{{ $lang('公平、尊重地對待員工，營造一種以促進員工安全、福祉和敬業度為核心的環境和文化。') }}</h2>
                        <div class="zybtn">{{ $lang('探索') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63"
                                height="14.17" viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                    </div>
                </div>
                <div class="banner-box diandao">
                    <div class="titlesbox marri50">
                        <h1>{{ $lang('多元化、公平性和包容性') }}</h1>
                        <h2>{{ $lang('倡導多元化和包容性，並透過培養高績效文化推動有意義的進步。') }}</h2>
                        <div class="zybtn">{{ $lang('探索') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63"
                                height="14.17" viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                    </div>
                    <img class="playerbg1" src="@/assets/images/indexbanner4.jpg" alt="">
                </div>
                <div class="banner-box">
                    <img class="playerbg1" src="@/assets/images/indexbanner5.jpg" alt="">
                    <div class="titlesbox marle50">
                        <h1>{{ $lang('社區參與') }}</h1>
                        <h2>{{ $lang('為了鼓勵和支持我們旗下公司積極參與並貢獻於其所在社區，無論是在本地還是在全球範圍內。') }}</h2>
                        <div class="zybtn">{{ $lang('探索') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63"
                                height="14.17" viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                    </div>
                </div>
            </div>
            <peopleSwiper :data="testimonials2"></peopleSwiper>
            <section class="sustainability-intro">
                <h1 class="title">{{ $lang('融入永續性') }}</h1>

                <p class="lead-text">
                    {{ $lang('我們在投資和持有過程中始終以整體視角看待回報，積極管理環境、社會和治理因素，以降低風險、提升價值創造並實現可觀的回報。') }}
                </p>

                <div class="content-grid">
                    <div class="content-col">
                        <h2>{{ $lang('在我們的投資方法中') }}</h2>
                        <p>
                            {{
                                $lang(`我們以策略性、基於事實的盡職調查為基礎進行投資決策，該調查會考慮廣泛的風險和價值槓桿，包括與永續性相關的因素。我們力求全面了解投資機會，並將策略、產品、服務和商業實踐納入考量。我們的投資團隊致力於評估關鍵的可持續性盡職調查結果，將重大風險和機會提請投資委員會討論，並明確潛在的可持續性重點領域，以便進行投資後的規劃和監測。`)
                            }}
                        </p>
                    </div>

                    <div class="content-col">
                        <h2>{{ $lang('在投資組合管理中') }}</h2>
                        <p>
                            {{
                                $lang('我們相信，將永續發展融入商業策略和負責任的運營，是我們創造價值和發展卓越企業不可或缺的一部分。投資完成後，我們致力於在核心永續發展承諾方面取得實質進展，並提升各公司在具體永續發展要素方面的表現。作為投資者和全球公民，我們努力透過發揮公司、投資和員工的影響力，為環境和社會做出貢獻。')
                            }}
                        </p>
                    </div>
                </div>
            </section>
            <div class="jingcaibox">
                <img class="shulu" src="@/assets/images/esg-breaker-bg.jpg" alt="">
                <div class="mask"></div>
                <img class="jccha" src="@/assets/images/bcv-parallax-cross-bg.webp" alt="">
                <div class="jingcont">
                    <div class="jtitle">{{ $lang('精彩片段') }}</div>
                    <div class="jtext">
                        <div class="item">{{ $lang('榮獲2024年度大型企業獎，並獲得Real Deals ESG認可') }}</div>
                        <div class="item fs100">{{ dataNumber[1] }}<span class="fs70 va40">0+</span>
                            <div class="itemtext">{{ $lang('我們的員工在非營利組織的董事會和其他機構任職。') }}</div>
                        </div>
                        <div class="item fs70"><span style="font-weight: 300;">{{ $lang('約') }}</span><span
                                class="fs100">{{
                                    dataNumber[2] }}</span><span class="va70">%</span>
                            <div class="itemtext">{{ $lang('公司在綠色認證的辦公空間建築物') }}</div>
                        </div>
                        <div class="item" style="margin-top: 50px;">{{ $lang('榮獲福布斯2024年全球最佳雇主稱號') }}</div>
                    </div>
                </div>
            </div>
            <div class="bottomftr">
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
                </div>
            </div>
        </div>
        <!-- <FooterBottom></FooterBottom> -->
    </div>
</template>

<style scoped lang="sass">
.sustainability-intro
  background-color:#1e5e94 // 圖片中的深藍色背景
  color: #ffffff
  padding: 100px
  font-family: "PingFang SC", "Microsoft JhengHei", sans-serif

    

.title
  font-size: 76px // 大標題
  font-weight: 400
  margin-bottom: 50px
  letter-spacing: 2px
.lead-text
  font-size: 22px
  line-height: 1.6
  max-width: 900px
  margin-bottom: 40px
  font-weight: 500
  @media (max-width: 768px)
    font-size: 16px
.content-grid
  display: flex
  gap: 80px // 左右兩欄的間距
  
  .content-col
    flex: 1
    
    h2
      font-size: 50px
      font-weight: 500
      margin-bottom: 30px
      position: relative
      @media (max-width: 768px)
        font-size: 30px
    
    p
      font-size: 22px
      line-height: 1.8
      color: rgba(255, 255, 255, 1) // 稍微透明一點增加層次感
      text-align: justify
      font-weight: 500
      @media (max-width: 768px)
        font-size: 16px

// 響應式：手機端改為垂直排列
@media (max-width: 992px)
  .sustainability-intro
    padding: 60px 5%
    .title
      font-size: 32px
    .content-grid
      flex-direction: column
      gap: 40px
.bodybox
  min-height: 5000px
  background-color: #eaf1fa
  transition: background .3s
  // background: url(@/assets/images/homebg.webp) !important
  .aboutmimg
    height: 100dvh
    position: relative
    overflow: hidden
    background-color: #fefcf5
    @media (max-width: 768px)
        height: 80dvh
    img
        width: 100%
        @media (max-width: 768px)
            position: absolute
            bottom: 90px
            transform: scale(1.8)
    .aobtbox
      position: absolute
      left: 100px
      top: 300px
      color: #1b215a
      font-size: 22px
      width: 1200px
      z-index: 2
      @media (max-width: 768px)
        font-size: 16px
        left: 25px
        width: 90%
        top: 270px
      .abtottile
        margin-bottom: 60px
        font-size: 120px
        line-height: 130px
        font-weight: 300
        @media (max-width: 768px)
            font-size: 40px
            line-height: 50px
            margin-bottom: 30px
      .adbtotext
        width: 968px
        margin-bottom: 20px
        @media (max-width: 768px)
            width: 100%
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
            font-size: 14px
        &:hover
            background-color: #001aff
            color: #fff
            svg
                fill: #fff
            .arrow-outline
                fill: #fff
                border: 2px solid #fff
        svg
            fill: #001aff
            margin-left: 5px
            transition: all .3s
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
        .arrow-round-icon
            background-color: #001aff
            fill: #fff !important
            margin-left: 0
            margin-right: 12px
  .container
    max-width: 90%
    margin: 0 auto
    margin-top: 100px
    background-color: #eaf1fa
    @media (max-width: 768px)
        padding-bottom: 50px
    .stitle
      font-size: 76px
      color: #1b215a
      font-weight: 300
      @media (max-width: 768px)
        font-size: 32px
    .ftitle
      font-size: 30px
      margin-top: 30px
      color: #1b215a
      width: 960px
      font-weight: 400
      @media (max-width: 768px)
        width: 100%
        font-size: 18px
        margin-top: 20px
  .jingcaibox
    height: 900px
    position: relative
    overflow: hidden
    width: 100%
    @media (max-width: 768px)
        height: 100dvh
    .shulu
        width: 100%
        height: 900px
        // margin-top: -90px
        object-fit: cover
    .mask
        position: absolute
        left: 0
        top: 0
        width: 100%
        height: 100%
        background: linear-gradient(-150deg,rgba(0,0,0,0.5) 50%,rgba(0,0,0,1) 100%)
        opacity: 0.5
    .jccha
        position: absolute
        z-index: 2
        width: 100%
        top: -100px
        right: 0
        @media (max-width: 768px)
            transform: scale(4)
            top: 45%
    .jingcont
        position: absolute
        left: 100px
        top: 100px
        z-index: 3
        @media (max-width: 768px)
            top: 20px
            left: 25px
        .jtitle
            font-size: 76px
            margin-bottom: 150px
            color: #fff
            font-weight: 300
            @media (max-width: 768px)
                font-size: 32px
                margin-bottom: 400px
        .jtext
            display: flex
            color: #3fb6ff
            font-size: 38px
            width: 50%
            flex-wrap: wrap
            @media (max-width: 768px)
                width: 100%
                font-size: 20px
            .item
                width: 50%
                text-align: center
                font-weight: 600
                padding: 0 30px
                font-family: 'Martinass'
                @media (max-width: 768px)
                    padding: 0 5px
                .itemtext
                    font-size: 22px
                    font-weight: 500
                    color: #fff
                    @media (max-width: 768px)
                        font-size: 14px

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
.diandao
  @media (max-width: 768px)
    flex-direction: column-reverse !important
.fs100
    font-size: 100px
    @media (max-width: 768px)
        font-size: 40px
.fs70
    font-size: 70px
    @media (max-width: 768px)
        font-size: 28px
.va40
    vertical-align: 40px
    @media (max-width: 768px)
        vertical-align: 20px
.va70
    vertical-align: 70px
    @media (max-width: 768px)
        vertical-align: 20px
.banner-box
  width: 100%
  display: flex
  align-items: center
  margin-top: 165px
  margin-bottom: 130px
  @media (max-width: 768px)
    flex-wrap: wrap
    margin: 0
    margin-top: 50px
  .player2
    width: 100% !important
  .marle100
    margin-left: 100px
    @media (max-width: 768px)
        margin-left: 0
  .marle50
    margin-left: 50px
    @media (max-width: 768px)
        margin-left: 0
  .marri50
    margin-right: 50px
    @media (max-width: 768px)
        margin-right: 0
  .playerbg1
    width: 50%
    height: auto
    border-radius: 5px
    @media (max-width: 768px)
        width: 100%

.titlesbox
  font-size: 50px
  width: 40%
  font-weight: 500
  color: #1b215a
  @media (max-width: 768px)
    width: 100%
    margin-top: 20px
    font-size: 30px
  h1
    transition: all .3s
    cursor: pointer
    &:hover
        color: #001aff
  h2
    font-size: 22px
    font-weight: 400
    margin-top: 20px
    @media (max-width: 768px)
        font-size: 16px
.zybtn
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
    &:hover
      background-color: #001aff
      color: #fff
      fill: #fff
    svg
        margin-left: 5px
.bottomftr
    padding: 50px 100px
    color: #abcae9
    font-weight: 500
    width: 100%
    display: flex
    justify-content: space-between
    background-color: #152d48
    @media (max-width: 768px)
        display: block
        padding: 50px 25px
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
</style>
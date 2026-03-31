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
const bgcolor = ref('#164167')
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
            if (scroll < 2300) {
                bgcolor.value = '#164167'
            }
            if (scroll > 2300) {
                bgcolor.value = '#fefcf5'
            }
            if (scroll > 6200) {
                bgcolor.value = '#1e5e94'
            }
        } else {
            if (scroll < 1200) {
                bgcolor.value = '#164167'
            }
            if (scroll > 1200) {
                bgcolor.value = '#fefcf5'
            }
            if (scroll > 3900) {
                bgcolor.value = '#1e5e94'
            }
        }
    })
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


const hideplayerimgbg1 = ref(true)
const trainingData = [
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-learning-development-bain-capital-academy.jpg?VersionId=DMkl7nqbfV2OZiJtPo8mt7Xfu7Hra7qT&amp;itok=0m9YMTMp", // 這裡填入你上傳的訓練工作坊圖片
        text: "貝恩資本學院是公司員工的學習平台，員工可以探索豐富的內部和外部課程，了解即將到來的培訓機會，並參考以往課程的教學大綱。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-learning-development-2.jpg?VersionId=6lxin0PPBkeZrfKBffmU0xZOFPVXNEVp&amp;itok=vOv7xA8G", // 範例多筆數據
        text: "全球培訓計畫貫穿貝恩資本員工職涯的關鍵節點。這些項目著重培養員工在當前職位及未來發展中所需的技能。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-learning-development-3.jpg?VersionId=VP5doQKGmhfg3DzCAilfr8OuWhqPVRtA&amp;itok=gHhSuHwH", // 範例多筆數據
        text: "LEAD計畫旨在提昇平台服務專業人員的專業技能。該計畫專注於領導力、創業精神、敏捷性和發展等技能培養主題，幫助參與者在貝恩資本及其他領域取得成功。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-learning-development-4.jpg?VersionId=8yg75dK7Dk26w7NZZh6mMpO1lXF85U41&amp;itok=EUceYTL9", // 範例多筆數據
        text: "投資專業人士入職培訓 (IPO)匯集了來自貝恩資本平台各部門的新晉投資專業人士。該計畫旨在幫助新晉投資專業人士快速融入貝恩資本，建立人脈網絡，提供行業背景知識，並建立知識庫，幫助他們取得成功。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-learning-development-5.jpg?VersionId=4WkdJhPGnqKWP4e4rezcFHoO.nOcmOVQ&amp;itok=vCOfs3lx", // 範例多筆數據
        text: "我們的學徒製文化驅動著員工的學習與發展。透過正式和非正式的指導，員工互相學習，不斷提陞技能。"
    }
]
const trainingData2 = [
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-opportunity-network-1-v2.jpg?VersionId=KHopSv5g7CNExt0SipY0UaGFwSjas7lF&amp;itok=frLg2787", // 範例多筆數據
        text: "我們每季都會舉辦「專家演講系列」活動，所有員工均可參加。在這些精彩的討論中，外部專家將就各種主題分享他們的真知灼見和獨到見解。近期，這些討論的重點包括種族平等、心理健康、以目標為導向的企業、永續發展以及氣候危機等議題。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-opportunity-network-2.jpg?VersionId=W538uiufh2JFxTRnglaM9zK_dwN2etrd&amp;itok=D_kcMMTQ", // 範例多筆數據
        text: "我們經常透過各種論壇召集投資組合公司的領導人，分享最佳實踐，創造交流機會，並促進公司、地理和產業之間的合作。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-opportunity-network-3.jpg?VersionId=QA9OCSK8EyA3f5AJI3mdNkk1XNuaJk1R&amp;itok=YMAMeBR-", // 範例多筆數據
        text: "秉承我們積極進取的企業文化，我們致力於為員工和人脈網絡創造機遇，無論是在公司內部還是在投資組合公司中。查看貝恩資本私募股權科技投資創投投資組合公司的職缺。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-opportunity-network-1-v2.jpg?VersionId=KHopSv5g7CNExt0SipY0UaGFwSjas7lF&amp;itok=frLg2787", // 範例多筆數據
        text: "我們每季都會舉辦「專家演講系列」活動，所有員工均可參加。在這些精彩的討論中，外部專家將就各種主題分享他們的真知灼見和獨到見解。近期，這些討論的重點包括種族平等、心理健康、以目標為導向的企業、永續發展以及氣候危機等議題。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-opportunity-network-2.jpg?VersionId=W538uiufh2JFxTRnglaM9zK_dwN2etrd&amp;itok=D_kcMMTQ", // 範例多筆數據
        text: "我們經常透過各種論壇召集投資組合公司的領導人，分享最佳實踐，創造交流機會，並促進公司、地理和產業之間的合作。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-opportunity-network-3.jpg?VersionId=QA9OCSK8EyA3f5AJI3mdNkk1XNuaJk1R&amp;itok=YMAMeBR-", // 範例多筆數據
        text: "秉承我們積極進取的企業文化，我們致力於為員工和人脈網絡創造機遇，無論是在公司內部還是在投資組合公司中。查看貝恩資本以及我們旗下私募股權科技投資創投投資組合公司的職缺。"
    }
]
const trainingData3 = [
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-well-being-gym_0.jpg?VersionId=rBy0Q89bTIf0rGksK1Ddh.qknCBWf3y_&amp;itok=M12v8w2T",
        text: "我們相信身體健康對整體健康至關重要，並提供虛擬健身課程、健身報銷和現場健身設施。"
    },
    {
        image: "https://cdn-east2.baincapital.com/2024-11/bc-careers-well-being-well-being.jpg?VersionId=a4ul5BGsJNYi8.MoN1dxtIT3BEKOzFyL",
        text: "我們提供一系列全面且具競爭力的員工福利。除了完善的醫療和退休計劃外，我們還提供提升生活品質的福利，包括靈活的休假選擇以及健康和生育計劃方面的資源。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-well-being-mental-health.jpg?VersionId=EQcgLI9iFE40VK_ZKxjrxKUaK3RlkrEB&amp;itok=Y0VJcKF7",
        text: "我們非常重視員工的心理健康，並提供諸如 Modern Health 和 Happier 等資源。員工協助方案 (EAP) 也提供全天候保密的諮詢和支持，幫助員工解決個人、家庭和工作相關的問題。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-well-being-new-child.jpg?VersionId=K2bmiF3JGdmRITqVP.6IZ5b4yVofyBKU&amp;itok=3PeVGF3j",
        text: "我們提供包容性的組成家庭福利，為員工提供資源，幫助他們應對建立或擴大家庭過程中遇到的各種複雜問題。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-well-being-gym_0.jpg?VersionId=rBy0Q89bTIf0rGksK1Ddh.qknCBWf3y_&amp;itok=M12v8w2T",
        text: "我們相信身體健康對整體健康至關重要，並提供虛擬健身課程、健身報銷和現場健身設施。"
    }
]
const trainingData4 = [
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-diversity-equity-inclusion-6.jpg?VersionId=iWEZ_9W0BV5UpUSObE4dkS2tCOleJCFL&amp;itok=D6mSEuUm",
        text: "貝恩資本亞太裔龍舟隊在"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-diversity-equity-inclusion-1.jpg?VersionId=zp0c7G8JJG0ntZNBMnGILA_DMQ1yH_MC&amp;itok=pqK4apul",
        text: "員工網絡旨在促進人際聯繫和支持，舉辦學習活動，並提供交流機會。我們的網路對所有人開放——認同我們理念的人、盟友以及希望了解更多資訊的人。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-diversity-equity-inclusion-2.jpg?VersionId=.Tg21iUM5UJX.gZwkRKjpEBGzEAp0Jt6&amp;itok=vxcIuBW1",
        text: "在驕傲月慶祝活動期間，驕傲網絡成員和公司領導與同事們交流和互動。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-diversity-equity-inclusion-3.jpg?VersionId=vWeOPeWWsqvz.DydX1ERVhR06wINuYn4&amp;itok=f75i4ZUj",
        text: "貝恩資本平台上的女性員工齊聚一堂，與一位開拓進取的女性CEO進行爐邊談話和招待會。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-diversity-equity-inclusion-4.jpg?VersionId=WZBSlfQXxfqw1XI105PLdwY490tEo6_1&amp;itok=h0Obdx3t",
        text: "貝恩資本的黑人成員們齊聚黑人歷史月社交活動，建立聯繫，加深關係。"
    }
]
const trainingData5 = [
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-positive-Impact-4.jpg?VersionId=rfHNDTWS4ZHSLRkS5YeJwoW2fSFrL4C4&amp;itok=Crme2t8G",
        text: "我們的配捐計畫為所有員工向符合資格的非營利組織的捐款提供 1:1 的配捐，以及志工獎勵配捐。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-positive-Impact-1_0.jpg?VersionId=P8.QDypVAtvl92WqMMqZnpcBkN400Mxd&amp;itok=e_ne5qIe",
        text: "透過貝恩資本兒童慈善機構和貝恩資本兒童基金會歐洲分會，員工可以提名他們關心的組織，由公司捐贈。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-positive-Impact-2.jpg?VersionId=YtjBWJDltUX8HzlrpcBTfSDRNH8tm85h&amp;itok=Ir9z8eFr",
        text: "本公司全年都會邀請員工參加公司協調組織的各類非營利合作計畫和志工活動。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-positive-Impact-3.jpg?VersionId=FpBZpGliyBl4GdhdkGB9xjAKJziYNHdH&amp;itok=m5qeSfKc",
        text: "我們經常聚在一起，參與各種活動，互相支持，也支持我們的社區。公司範圍內的慈善團隊活動包括波士頓兒童醫院步行活動、為生存而騎行活動、為利亞姆的幸運符騎行MS團隊活動、Peak24接力賽、泛馬薩諸塞州挑戰賽和東京馬拉松。"
    },
    {
        image: "https://cdn-east2.baincapital.com/styles/optimize_image/s3/2024-11/bc-careers-positive-Impact-4.jpg?VersionId=rfHNDTWS4ZHSLRkS5YeJwoW2fSFrL4C4&amp;itok=Crme2t8G",
        text: "我們的配捐計畫為所有員工向符合資格的非營利組織的捐款提供 1:1 的配捐，以及志工獎勵配捐。"
    }
]
</script>

<template>
    <div class="cont">
        <headerTop :top="isTop" :white="true" :opacity="isTop"></headerTop>
        <div :style="{ background: bgcolor }" class="bodybox">
            <div class="container">
                <h1 class="stitle">{{ $lang('發揮你的潛力') }}</h1>
                <h2 class="ftitle">{{
                    $lang('在支持你、重視你的領導團隊中發展你的職涯。在貝恩資本，各層級的同事都擁有發言權，共同以主要投資者的思維方式應對業務挑戰。在這裡，人才是我們最大的優勢。') }}
                </h2>
                <div class="banner-box" style="justify-content: center;">
                    <div class="ifbox">
                        <iframe allow="autoplay;" class="player2" muted="" plays-inline=""
                            src="https://player.vimeo.com/video/1026854116?api=1&amp;player_id=player2&amp;quality=1080p&amp;autoplay=0"
                            frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="">
                        </iframe>
                        <img v-if="hideplayerimgbg1" class="playerbg1" style="width: 110% !important;max-width: none;"
                            src="@/assets/images/career-video-bg_0.jpg" alt="">
                        <div v-if="hideplayerimgbg1" class="textbg"></div>
                        <div v-if="hideplayerimgbg1" @click="hideplayerimgbg1 = false" class="textmore"><svg
                                id="Layer_1" xmlns="//www.w3.org/2000/svg" width="25.88" height="25.88"
                                viewBox="0 0 25.88 25.88">
                                <path class="cls-1"
                                    d="M11.29,19.96l-1.32-1.32.67-.67c2.41-2.41,3.62-3.62,3.62-5.03s-1.21-2.62-3.62-5.03l-.67-.67,1.32-1.32,7.02,7.02-7.02,7.02ZM12.94,0C5.8,0,0,5.8,0,12.94s5.8,12.94,12.94,12.94,12.94-5.8,12.94-12.94S20.07,0,12.94,0">
                                </path>
                            </svg>{{ $lang('用我們的話語來說，我們的宗旨') }}</div>
                    </div>
                </div>
                <div class="linlist">
                    <div>{{ $lang('機會') }}</div>
                    <div>{{ $lang('生長') }}</div>
                    <div>{{ $lang('加入我們') }}</div>
                </div>
            </div>
            <bainCarousel></bainCarousel>
            <div class="container">
                <div class="sztext">{{ $lang('生長') }}</div>
                <h1 class="stitle" style="color: #1b215a;">{{ $lang('我們以有意義的方式支持員工及其發展。') }}</h1>
                <div class="swipertextbox pale120">
                    <div class="imgcon">
                        <ImageTextCarousel :carouselData="trainingData"></ImageTextCarousel>
                    </div>
                    <div class="contxt">
                        <div class="contxtit">{{ $lang('學習與發展') }}</div>
                        <div>{{
                            $lang('我們學習速度很快，在小團隊中工作，獲得實務經驗和學徒機會，並解決廣泛的策略、財務和營運問題。我們也透過持續的正式培訓來補充這些學習，從而為下一個職位或挑戰奠定必要的技能基礎。')
                            }}
                        </div>
                    </div>
                </div>
                <div class="swipertextbox pari120 diandao">
                    <div class="contxt">
                        <div class="contxtit">{{ $lang('職業機會和人脈') }}</div>
                        <div>{{
                            $lang('我們期望並認可員工的最佳努力，並創造一個支持性的環境，鼓勵員工挑戰自我，促進個人成長。團隊成員建立並利用強大的內部和外部網絡，作為我們高度重視的長期合作關係的基礎。')
                            }}
                        </div>
                    </div>
                    <div class="imgcon">
                        <ImageTextCarousel :carouselData="trainingData2"></ImageTextCarousel>
                    </div>
                </div>
                <div class="swipertextbox pale120">
                    <div class="imgcon">
                        <ImageTextCarousel :carouselData="trainingData3"></ImageTextCarousel>
                    </div>
                    <div class="contxt">
                        <div class="contxtit">{{ $lang('職業永續性和幸福感') }}</div>
                        <div>{{ $lang('作為一家公司，我們深知身心健康對員工日常生活（無論是在工作或生活中）的重要性。我們致力於提供各種資源和支持，確保每位團隊成員都能專注於工作、自身和家庭。') }}
                        </div>
                    </div>
                </div>
                <div class="swipertextbox pari120 diandao">
                    <div class="contxt">
                        <div class="contxtit">{{ $lang('多元化、公平性和包容性') }}</div>
                        <div>
                            {{
                                $lang('我們員工多元化的背景、觀點和觀點營造了充滿活力的工作環境，有助於做出更明智的投資決策。我們透過包容的企業文化來培養這種環境，並建立了正式和非正式的交流網絡，幫助團隊成員相互協作、學習。')
                            }}
                        </div>
                    </div>
                    <div class="imgcon">
                        <ImageTextCarousel :carouselData="trainingData4"></ImageTextCarousel>
                    </div>
                </div>
                <div class="swipertextbox pale120">
                    <div class="imgcon">
                        <ImageTextCarousel :carouselData="trainingData5"></ImageTextCarousel>
                    </div>
                    <div class="contxt">
                        <div class="contxtit">{{ $lang('正面影響') }}</div>
                        <div>
                            {{
                                $lang('我們將一系列永續發展考量融入投資流程，為我們管理的資產創造價值，並兼顧眾多利害關係人的利益。透過貝恩資本社區合作項目，我們致力於在我們工作和生活的社區中產生切實的影響。我們也投入個人資源、時間和專業知識，支持當地社區和慈善事業，共同創造更美好的世界。')
                            }}
                        </div>
                    </div>
                </div>
                <div class="sztext" style="font-weight: 500;margin-top: 150px;color: #fff;">{{ $lang('加入我們') }}</div>
                <h1 class="stitle" style="color: #fff;">{{ $lang('讓我們聯繫') }}</h1>
                <div class="job">
                    <div class="left">
                        <div style="margin-bottom: 15px;">{{ $lang('了解貝恩資本的空缺：') }}</div>
                        <div @click="goLink('https://baincapital.wd1.myworkdayjobs.com/External_Public')" class="zybtn">
                            {{ $lang('目前空缺職位') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63"
                                height="14.17" viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                    </div>
                    <div class="right">
                        <div style="margin-bottom: 15px;">{{ $lang('了解我們投資組合公司提供的職缺：') }}</div>
                        <div @click="goLink('https://www.baincapital.com/crypto')" class="zybtn">{{ $lang('加密貨幣') }}<svg
                                id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63" height="14.17"
                                viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                        <br>
                        <div @click="goLink('https://www.baincapitalinsurance.com/')" class="zybtn">{{ $lang('保險')
                            }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63" height="14.17"
                                viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                        <br>
                        <div @click="goLink('https://www.baincapitalprivateequity.com/')" class="zybtn">{{ $lang('私募股權')
                            }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63" height="14.17"
                                viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                        <br>
                        <div @click="goLink('https://baincapitalspecialsituations.com/')" class="zybtn">{{ $lang('特殊情況')
                            }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63" height="14.17"
                                viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                        <br>
                        <div @click="goLink('https://www.baincapitaltechopportunities.com/')" class="zybtn">{{
                            $lang('技術機會') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63" height="14.17"
                                viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                        <br>
                        <div @click="goLink('https://www.baincapital.com/ventures')" class="zybtn">{{ $lang('創投') }}<svg
                                id="Layer_1" xmlns="//www.w3.org/2000/svg" width="8.63" height="14.17"
                                viewBox="0 0 6.63 11.17">
                                <path
                                    d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                                </path>
                            </svg></div>
                    </div>

                </div>
                <div class="jobtext">
                    {{ $lang('對於美國的求職者，貝恩資本參與了E-Verify計劃，如果您被錄用，我們將使用E-Verify系統來確認您的工作許可。有關E-Verify的更多信息，請參閱') }}
                    <u>{{ $lang('《E-Verify參與和工作權利通知》') }}</u>。
                </div>
            </div>
            <div class="foterboxbg">
                <div class="bottomftr">
                    <div>
                        <div>
                            {{ $lang('© 2012-2026 貝恩資本有限合夥公司。貝恩資本方形標誌是貝恩資本有限合夥公司的商標。版權所有。') }}</div>
                        <div class="ftrtext">
                            <div @click="goLink('https://www.baincapital.com/privacy-policy')">{{ $lang('隱私權政策') }}
                            </div>
                            <div @click="goLink('https://www.baincapital.com/terms-use')">{{ $lang('使用條款') }}</div>
                            <div @click="goLink('https://www.baincapital.com/regulatory-disclosures')">{{ $lang('監理揭露')
                                }}</div>
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
        <!-- <FooterBottom></FooterBottom> -->
    </div>
</template>

<style scoped lang="sass">
.diandao
  @media (max-width: 768px)
    flex-direction: column-reverse !important
.bodybox
  min-height: 5000px
  background-color: #164167
  transition: background .3s
  // background: url(@/assets/images/homebg.webp) !important
  .aboutmimg
    height: 100dvh
    position: relative
    overflow: hidden
    background-color: #fefcf5
    img
        width: 100%
    .aobtbox
      position: absolute
      left: 100px
      top: 300px
      color: #1b215a
      font-size: 22px
      width: 1200px
      z-index: 2
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
    padding-top: 150px
    .stitle
      font-size: 84px
      color: #fff
      font-weight: 300
      @media (max-width: 768px)
        font-size: 36px
    .pale120
        padding-left: 120px
        @media (max-width: 768px)
            padding-left: 0
    .pari120
        padding-right: 120px
        @media (max-width: 768px)
            padding-right: 0
    .swipertextbox
        display: flex
        gap: 60px
        margin-top: 100px
        @media (max-width: 768px)
            flex-wrap: wrap
            margin-top: 40px
            gap: 40px
        .contxt
            width: 30%
            color: #1b215a
            font-size: 22px
            @media (max-width: 768px)
                font-size: 16px
                width: 100%
            .contxtit
                font-size: 50px
                margin-bottom: 20px
                @media (max-width: 768px)
                    font-size: 32px
                    font-weight: 300
        .imgcon
            width: 60%
            @media (max-width: 768px)
                width: 90%
                margin: 0 auto
    .sztext
        font-size: 24px
        color: #1b215a
    .ftitle
      font-size: 22px
      margin: 0 auto
      margin-top: 50px
      color: #fff
      width: 960px
      font-weight: 400
      max-width: 100%
      @media (max-width: 768px)
        font-size: 16px
    .job
        margin-top: 120px
        display: flex
        font-size: 22px
        color: #fff
        @media (max-width: 768px)
            margin-top: 50px
            display: block
            font-size: 16px
        .left
            width: 40%
            border-right: 1px solid rgba(255,255,255,0.35)
            @media (max-width: 768px)
                width: 100%
                border-right: 0
                border-bottom: 1px solid rgba(255,255,255,0.35)
                margin-bottom: 30px
        .right
            padding-left: 30px
            @media (max-width: 768px)
                padding: 0
    .jobtext
        margin: 100px 0
        color: #fff
        font-size: 22px
        width: 80%
        @media (max-width: 768px)
            width: 100%
            font-size: 16px
            margin: 50px 0
.zybtn
    color: #001aff
    border: 2px solid #000
    border-radius: 30px
    padding: 5px 17px
    display: inline-flex
    align-items: center
    font-size: 21px
    font-weight: 500
    fill: #001aff
    cursor: pointer
    transition: all .3s
    background-color: #fff
    margin-bottom: 20px
    @media (max-width: 768px)
        font-size: 14px
        border: none
    &:hover
      background-color: #001aff
      color: #fff
      border: 2px solid #001aff
      fill: #fff
    svg
        margin-left: 5px
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

.banner-box
  width: 100%
  display: flex
  margin: 100px 0
  margin-bottom: 130px
  @media (max-width: 768px)
    margin: 40px 0
  .ifbox
    width: 80%
    position: relative
    border-radius: 5px
    overflow: hidden
    margin: 0
    @media (max-width: 768px)
        width: 100%
    .player2
      width: 100% !important
      height: 41dvw
      @media (max-width: 768px)
        height: 191px
    .playerbg1
      width: 110% !important
      height: auto
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
.linlist
    display: flex
    padding: 10px
    border-top: 1px solid rgba(255,255,255,0.35)
    border-bottom: 1px solid rgba(255,255,255,0.35)
    margin-bottom: 150px
    @media (max-width: 768px)
        margin-bottom: 0
    div
        width: 33.3%
        border-right: 1px solid rgba(255,255,255,0.35)
        font-size: 22px
        color: #fff
        padding: 25px 20px
        text-align: center
        cursor: pointer
        transition: all .3s
        &:hover
            color: #3fb6ff
        &:last-child
            border: none
        @media (max-width: 768px)
            font-size: 14px
.titlesbox
  font-size: 50px
  width: 40%
  font-weight: 500
  color: #1b215a
  h1
    transition: all .3s
    cursor: pointer
    &:hover
        color: #001aff
  h2
    font-size: 22px
    font-weight: 400
    margin-top: 20px
.foterboxbg
    padding: 100px
    background-color: #f7f5f4
    @media (max-width: 768px)
        padding: 30px 25px
.bottomftr
    color: #716e6a
    font-weight: 500
    width: 100%
    display: flex
    justify-content: space-between
    background-color: #f7f5f4
    align-items: center
    padding-top: 28px
    border-top: 1px solid #716e6a
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
        border-bottom: 1px solid #716e6a
        transition: all .3s
        cursor: pointer
        @media (max-width: 768px)
            margin-top: 5px
        &:hover
          border-bottom: 1px solid transparent !important
</style>
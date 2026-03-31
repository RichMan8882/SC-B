<script lang="ts" setup>
import Lenis from "@studio-freight/lenis"
import avatar1 from '@/assets/images/Darren.jpg'
import avatar2 from '@/assets/images/AjayAgarwa.jpeg'
import avatar3 from '@/assets/images/bc-no-image.png'
import avatar4 from '@/assets/images/bc-no-image.png'
import avatar5 from '@/assets/images/peopleav5.jpg'
import avatar6 from '@/assets/images/peopleav6.jpg'
import avatar7 from '@/assets/images/peopleav7.jpg'
import avatar8 from '@/assets/images/peopleav8.jpg'
import avatar9 from '@/assets/images/peopleav9.jpg'
import avatar10 from '@/assets/images/peopleav10.jpg'


const { t } = useI18n()
const siteStore = useSiteStore()
const router = useRouter()
const timer = ref()
onMounted(() => {
})

const toUrl = (url) => {
    window.open(url)
}
const goLink = (link) => {
    window.open(link)
}
const isTop = ref(false)

const isShowTishi = ref(true)
const peopleList = [
    {
        name: "達倫·亞伯拉罕森",
        role: "夥伴",
        department: "技術機會",
        location: "波士頓",
        img: avatar1
    },
    {
        name: "阿傑·阿加瓦爾",
        role: "夥伴",
        department: "創投",
        location: "舊金山，波士頓",
        img: avatar2
    },
    {
        name: "阿基爾·阿加瓦爾",
        role: "聯繫",
        department: "創投",
        location: "舊金山",
        img: avatar3
    },
    {
        name: "安基特·阿加瓦爾",
        role: "主要的",
        department: "私募股權",
        location: "孟買",
        img: avatar4
    },
    {
        name: "沙基布·艾哈邁德",
        role: "合規副總裁",
        department: "公司的",
        location: "倫敦",
        img: avatar5
    },
    {
        name: "安娜·亞歷山德里亞",
        role: "薪資福利主管",
        department: "公司的",
        location: "波士頓",
        img: avatar6
    },
    {
        name: "塔拉·艾琳",
        role: "夥伴",
        department: "信用",
        location: "波士頓",
        img: avatar7
    },
    {
        name: "格雷森·艾利森",
        role: "常務董事",
        department: "信用",
        location: "波士頓",
        img: avatar8
    },
    {
        name: "埃里克·安德森",
        role: "夥伴",
        department: "私募股權",
        location: "波士頓",
        img: avatar9
    },
    {
        name: "派崔克安德魯斯",
        role: "聯繫",
        department: "技術機會",
        location: "舊金山",
        img: avatar10
    }
];
const himg = ref(true)
let lenis = null
let rafId = null
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

})
onUnmounted(() => {
    cancelAnimationFrame(rafId)
    lenis.destroy()
})
</script>

<template>
    <div class="cont">
        <headerTop :top="isTop" :white="true" :opacity="isTop"></headerTop>
        <div class="bodybox">
            <div class="container">
                <div class="tishi" v-if="isShowTishi">
                    <div>
                        {{
                            $lang('防範詐騙與網路安全警告：貝恩資本及其員工絕不會透過網站或WhatsApp、Telegram等即時通訊平台進行任何投資活動，也不會索取任何資金或銀行帳戶資訊。請勿回覆任何來歷不明的簡訊、社群媒體訊息、電子郵件或電話。')
                        }}
                    </div>
                    <div class="closebtn" @click="isShowTishi = false">
                        <svg id="Layer_1" xmlns="http://www.w3.org/2000/svg" width="10.34" height="10.34"
                            viewBox="0 0 10.34 10.34">
                            <path class="cls-1"
                                d="M1.19,8.35c1.5-1.5,2.25-2.25,2.25-3.18s-.75-1.68-2.25-3.18L0,.8l.8-.8,1.19,1.19c1.5,1.5,2.25,2.25,3.18,2.25.93,0,1.68-.75,3.18-2.25l1.19-1.19.8.8-1.19,1.19c-1.5,1.5-2.25,2.25-2.25,3.18s.75,1.68,2.25,3.18l1.19,1.19-.8.8-1.19-1.19c-1.5-1.5-2.25-2.25-3.18-2.25s-1.68.75-3.18,2.25l-1.19,1.19-.8-.8,1.19-1.19Z">
                            </path>
                        </svg>
                    </div>
                </div>
                <h1 class="stitle">{{ $lang('我們的人民') }}</h1>
                <h2 class="ftitle">{{ $lang('我們互相激勵，以不同的方式思考和工作，從而創造有意義且持久的影響。') }}</h2>
                <div class="topmenu">
                    <div class="topmenusele">{{ $lang('佈局：') }}<svg @click="himg = true" id="Layer_1"
                            xmlns="//www.w3.org/2000/svg" width="19.83" height="19.82" viewBox="0 0 19.83 19.82">

                            <rect class="cls-1" x="0" width="9" height="9" rx="2" ry="2"></rect>
                            <rect class="cls-1" x="10.83" width="9" height="9" rx="2" ry="2"></rect>
                            <rect class="cls-1" x="0" y="10.82" width="9" height="9" rx="2" ry="2"></rect>
                            <rect class="cls-1" x="10.83" y="10.82" width="9" height="9" rx="2" ry="2"></rect>
                        </svg>
                        <svg @click="himg = false" id="Layer_1" xmlns="//www.w3.org/2000/svg" width="20.5"
                            height="19.85" viewBox="0 0 20.5 19.85">
                            <g class="cls-2" stroke="#001aff">
                                <g>
                                    <line class="cls-1" x1="1.2" y1="1.2" x2="19.3" y2="1.2"></line>
                                    <line class="cls-1" x1="1.2" y1="7.02" x2="19.3" y2="7.02"></line>
                                    <line class="cls-1" x1="1.2" y1="12.83" x2="19.3" y2="12.83"></line>
                                    <line class="cls-1" x1="1.2" y1="18.65" x2="19.3" y2="18.65"></line>
                                </g>
                            </g>
                        </svg>
                    </div>
                    <div class="topmenusele">{{ $lang('地點：全部') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg"
                            width="15" height="8.91" viewBox="0 0 15 8.91">
                            <path class="cls-1"
                                d="M1.79.84c2.69,2.73,4.04,4.09,5.71,4.09s3.02-1.36,5.71-4.09l.48-.49.95.97-7.15,7.24L.35,1.32l.95-.97.48.49Z">
                            </path>
                        </svg>
                    </div>
                    <div class="topmenusele">{{ $lang('標題：全部') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg"
                            width="15" height="8.91" viewBox="0 0 15 8.91">
                            <path class="cls-1"
                                d="M1.79.84c2.69,2.73,4.04,4.09,5.71,4.09s3.02-1.36,5.71-4.09l.48-.49.95.97-7.15,7.24L.35,1.32l.95-.97.48.49Z">
                            </path>
                        </svg>
                    </div>
                    <div class="topmenusele">{{ $lang('商業：全部') }}<svg id="Layer_1" xmlns="//www.w3.org/2000/svg"
                            width="15" height="8.91" viewBox="0 0 15 8.91">
                            <path class="cls-1"
                                d="M1.79.84c2.69,2.73,4.04,4.09,5.71,4.09s3.02-1.36,5.71-4.09l.48-.49.95.97-7.15,7.24L.35,1.32l.95-.97.48.49Z">
                            </path>
                        </svg>
                    </div>
                </div>
                <div v-if="himg" class="people">
                    <div class="item" v-for="(item, index) in peopleList"
                        @click="navigateTo('/peopledetails?id=' + index)">
                        <img :src="item.img" alt="">
                        <div class="name">{{ t(item.name) }}</div>
                        <div>{{ t(item.role) }}</div>
                        <div style="margin-top: 30px;">{{ t(item.department) }}</div>
                        <div>{{ t(item.location) }}</div>
                    </div>
                </div>
                <div v-else class="peolist">
                    <div class="item" v-for="(item, index) in peopleList"
                        @click="navigateTo('/peopledetails?id=' + index)">
                        <div class="name">{{ item.name }}</div>
                        <div>{{ item.role }}</div>
                        <div>{{ item.department }}</div>
                        <div>{{ item.location }}</div>
                    </div>
                </div>
            </div>
        </div>
        <!-- <FooterBottom></FooterBottom> -->
    </div>
</template>

<style scoped lang="sass">
.bodybox
  background-color: #fefcf5
  transition: background .3s
  // background: url(@/assets/images/homebg.webp) !important
  .container
    max-width: 90%
    margin: 0 auto
    padding-top: 100px
    padding-bottom: 200px
    // background-color: #eaf1fa
    .tishi
        background-color: #ffc86b
        color: #1c2156
        padding: 20px
        border-radius: 5px
        margin: 50px 0
        font-weight: 500
        display: flex
        align-items: center
        @media (max-width: 768px)
            display: none
        .closebtn
            width: 25px
            height: 25px
            display: flex
            justify-content: center
            align-items: center
            border-radius: 50%
            background-color: #1c2156
            margin-left: 150px
            cursor: pointer
            transition: all .3s
            &:hover
                transform: rotate(90deg) !important
            svg
                fill: #fdbf61
    .stitle
      font-size: 84px
      color: #1b215a
      font-weight: 300
      margin-top: 70px
      @media (max-width: 768px)
        font-size: 36px
        margin-top: 10px
    .ftitle
      font-size: 22px
      margin-top: 30px
      color: #1b215a
      width: 600px
      font-weight: 400
      max-width: 100%
      @media (max-width: 768px)
        font-size: 16px
    .topmenu
        color: #001aff
        font-size: 18px
        font-weight: 500
        display: flex
        margin-top: 80px
        margin-bottom: 30px
        @media (max-width: 768px)
            display: none
        .topmenusele
            display: flex
            align-items: center
            fill: #001aff
            margin-right: 30px
            svg
                margin-left: 8px
                cursor: pointer
    .people
        display: flex
        flex-wrap: wrap
        @media (max-width: 768px)
            margin-top: 100px
        .item
            margin-bottom: 30px
            overflow: hidden
            width: 330px
            color: #1b215a
            font-size: 15px
            margin-right: 10px
            cursor: pointer
            &::before
                position: absolute
                top: 0
                left: -100%
                z-index: 2
                content: ""
                width: 50%
                height: 100%
                background: linear-gradient(to right, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.3) 100%)
                transform: skewX(-25deg)
            &:hover
                &::before
                    animation: shine 0.75s
            @media (max-width: 768px)
                width: 47%
            .name
                font-size: 18px
                font-weight: 600
                margin-top: 10px
            img
                width: 100%
                aspect-ratio: 1 / 1
                border-radius: 5px
    .peolist
        .item
            border-bottom: 1px solid #a9a7a8
            padding: 20px
            display: flex
            color: #1b215a
            cursor: pointer
            div
                width: 25%
            .name
                font-size: 18px
                font-weight: 600

@keyframes shine
    100%
        left: 125%
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
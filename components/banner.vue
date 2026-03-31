<template>
    <div class="bannerbox">
        <div class="titlebox">
            <h1>{{ $lang('擁抱可能性,') }}</h1>
            <h1 class="reditalic">{{ $lang('實現潛力') }}</h1>
            <div :class="bannerIndex == 1 ? 'banneractive' : ''" class="text">
                {{ $lang('貝恩資本是一家全球性私募投資公司，透過不同的合作方式釋放機遇，幫助個人和企業') }}<span class="reditalic">{{ $lang('創造卓越成果。')
                    }}</span>

            </div>
            <div :class="bannerIndex == 2 ? 'banneractive' : ''" class="text">{{ $lang('我們投資未來。透過') }}<span
                    class="reditalic">{{ $lang('跨平台協作') }}</span>{{ $lang('，我們整合深厚多元的垂直和區域專業知識，提供獨特的見解。') }}
                <br>
                <div class="linkbtn">
                    <div class="arrow-round-icon arrow-outline">
                        <svg id="Layer_1" xmlns="//www.w3.org/2000/svg" width="6.63" height="11.17"
                            viewBox="0 0 6.63 11.17">
                            <path class="arrow-icon"
                                d="M.71,9.77c1.97-1.97,2.96-2.96,2.96-4.18S2.68,3.37.71,1.4l-.35-.35.7-.7,5.23,5.23L1.05,10.82l-.7-.7.35-.35Z">
                            </path>
                        </svg>
                    </div>
                    {{ $lang('看看我們的方法是如何實施的') }}
                </div>
            </div>
            <div :class="bannerIndex == 3 ? 'banneractive' : ''" class="text">
                {{ $lang('作為我們團隊的一員，您將獲得支持型領導的幫助，加速您的職涯發展。加入貝恩資本，') }}<span class="reditalic">{{ $lang('開啟您的職業新篇章。')
                    }}</span>
                <div class="linkbtn">
                    {{ $lang('發揮你的潛力') }}
                    <div class="arrow-outline">
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

        <div class="tanagram-wrapper">
            <div class="banner-nav-slider-wrap">
                <div class="items" :class="bannerIndex == 1 ? 'fcolor' : ''" @click="onestart">
                    <div class="line">
                        <div class="bar" :class="bannerIndex == 1 ? 'baractive' : ''"></div>
                    </div>{{ $lang('我們是誰') }}
                </div>
                <div class="items" :class="bannerIndex == 2 ? 'fcolor' : ''" @click="oneend">
                    <div class="line">
                        <div class="bar" :class="bannerIndex == 2 ? 'baractive' : ''"></div>
                    </div>{{ $lang('我們有何不同') }}
                </div>
                <div class="items" :class="bannerIndex == 3 ? 'fcolor' : ''" @click="twoend">
                    <div class="line">
                        <div class="bar" :class="bannerIndex == 3 ? 'baractive' : ''"></div>
                    </div>{{ $lang('充滿成就感的職責') }}
                </div>
            </div>
            <div class="tanagram-anim-wrap">
                <svg ref="svgRef" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1273.76 1106.23" class="tanagram-svg">
                    <defs>
                        <clipPath id="clip1">
                            <path
                                d="M614.25,803.37c-4.11,2.87-10.39,6.02-19.28,10.46L27.12,1097.76c-7.41,3.7-12.58,6.28-16.57,7.58-3.93,1.29-5.74,1-7,.23-1.26-.78-2.32-2.27-2.93-6.36-.61-4.15-.62-9.93-.62-18.21v-270.03c0-3.46,0-5.77.19-7.56.18-1.71.49-2.62.93-3.33.44-.71,1.11-1.4,2.56-2.32,1.52-.97,3.59-2.01,6.68-3.55l297.83-148.91c5.27-2.64,6.82-3.31,8.38-3.31s3.11.67,8.38,3.31l270.03,135.02c8.89,4.45,15.17,7.6,19.28,10.46,4.13,2.88,4.98,4.74,4.98,6.3s-.85,3.41-4.98,6.3">
                            </path>
                        </clipPath>
                        <clipPath id="clip2">
                            <path
                                d="M934.55,643.34c-4.11,2.87-10.39,6.02-19.28,10.46l-270.02,134.9c-5.27,2.63-6.81,3.3-8.37,3.3s-3.11-.67-8.38-3.3l-297.83-148.79c-3.09-1.55-5.16-2.58-6.68-3.55-1.45-.92-2.12-1.61-2.56-2.32s-.75-1.62-.93-3.33c-.19-1.79-.19-4.11-.19-7.56v-270.15c0-8.28.01-14.06.63-18.21.61-4.09,1.67-5.58,2.93-6.36,1.26-.78,3.07-1.06,7,.23,3.99,1.3,9.16,3.88,16.57,7.59l567.85,284.04c8.89,4.45,15.17,7.6,19.28,10.47,4.13,2.88,4.98,4.74,4.98,6.3s-.85,3.42-4.98,6.3">
                            </path>
                        </clipPath>
                        <clipPath id="clip3">
                            <path
                                d="M1273.75,760.69c0,8.28-.01,14.06-.63,18.21-.61,4.09-1.67,5.58-2.93,6.36-1.26.78-3.07,1.06-7-.23-3.99-1.3-9.16-3.88-16.56-7.58l-567.84-283.92c-8.89-4.45-15.17-7.6-19.28-10.47-4.13-2.88-4.98-4.74-4.98-6.3s.85-3.42,4.98-6.3c4.11-2.87,10.39-6.02,19.29-10.46l567.83-283.92c7.41-3.71,12.58-6.28,16.57-7.59,3.93-1.29,5.74-1.01,7-.23s2.32,2.27,2.93,6.36c.62,4.15.63,9.93.63,18.21v567.86Z">
                            </path>
                        </clipPath>
                        <clipPath id="clipImage-4">
                            <path
                                d="M1252.39,161.38c-4.11,2.87-10.39,6.02-19.28,10.46l-567.85,283.93c-7.41,3.7-12.58,6.28-16.57,7.58-3.93,1.29-5.74,1-7,.23-1.26-.78-2.32-2.27-2.93-6.36-.61-4.15-.62-9.93-.62-18.21V168.98c0-3.46,0-5.77.19-7.56.18-1.71.49-2.62.93-3.33.44-.71,1.11-1.4,2.56-2.32,1.52-.97,3.59-2.01,6.68-3.55L946.33,3.31c5.27-2.64,6.82-3.31,8.38-3.31s3.11.67,8.38,3.31l270.03,135.02c8.89,4.45,15.17,7.6,19.28,10.46,4.13,2.88,4.98,4.74,4.98,6.3s-.85,3.42-4.98,6.3">
                            </path>
                        </clipPath>
                        <clipPath id="clipImage-5">
                            <path
                                d="M659.04,793.13c4.1-2.88,10.37-6.05,19.25-10.52l269.58-135.78c5.26-2.65,6.8-3.32,8.36-3.33s3.11.66,8.39,3.27l298.31,147.82c3.1,1.54,5.17,2.56,6.69,3.53,1.45.92,2.13,1.6,2.57,2.31s.76,1.62.94,3.33c.2,1.79.2,4.11.21,7.56l.88,270.15c.03,8.28.04,14.06-.57,18.21-.6,4.09-1.65,5.59-2.91,6.37-1.26.78-3.07,1.07-7-.21-3.99-1.29-9.17-3.85-16.59-7.54l-568.77-282.19c-8.9-4.42-15.19-7.55-19.31-10.41-4.14-2.87-5-4.72-5-6.28s.84-3.42,4.96-6.32">
                            </path>
                        </clipPath>
                    </defs>

                    <g class="fragments-group">
                        <!-- 下方 -->
                        <g class="fragment-item1 opcisty" clip-path="url(#clip1)">
                            <image :class="bannerIndex == 1 ? 'banneractive' : ''"
                                href="@/assets/images/banner/ban1g.jpg" x="0" y="641" width="620" height="464"
                                preserveAspectRatio="xMidYMid slice" />
                            <image :class="bannerIndex == 2 ? 'banneractive' : ''"
                                href="@/assets/images/banner/ban2j.jpg" x="0" y="641" width="620" height="464"
                                preserveAspectRatio="xMidYMid slice" />
                            <image :class="bannerIndex == 3 ? 'banneractive' : ''"
                                href="@/assets/images/banner/ban3bs.jpg" x="-320" y="160" width="1273" height="1106"
                                preserveAspectRatio="xMidYMid slice" />
                        </g>
                        <!-- 中間 -->
                        <g class="fragment-item2" clip-path="url(#clip2)">
                            <image href="@/assets/images/banner/banc.jpg" x="320" y="327" width="620" height="464"
                                preserveAspectRatio="xMidYMid slice" />
                        </g>
                        <!-- 三角形 -->
                        <g class="opcisty" clip-path="url(#clip3)">
                            <image :class="bannerIndex == 1 ? 'banneractive' : ''"
                                href="@/assets/images/banner/ban1bs.jpg" x="654" y="167" width="620" height="618"
                                preserveAspectRatio="xMidYMid slice" />
                            <image :class="bannerIndex == 2 ? 'banneractive' : ''"
                                href="@/assets/images/banner/ban2bs.jpg" x="654" y="167" width="620" height="618"
                                preserveAspectRatio="xMidYMid slice" />
                            <image :class="bannerIndex == 3 ? 'banneractive' : ''"
                                href="@/assets/images/banner/ban3bs.jpg" x="0" y="0" width="1273" height="1106"
                                preserveAspectRatio="xMidYMid slice" />
                        </g>
                        <!-- 上方 -->
                        <rect class="fragment-item3" x="638.1400146484375" y="0" width="619.239990234375"
                            height="464.2376708984375" fill="#B2DEFF" clip-path="url(#clipImage-4)"
                            data-svg-origin="638.1400146484375 0"></rect>
                        <!-- 下方 -->
                        <rect class="fragment-item4" x="654.0697631835938" y="643.4998168945312"
                            width="620.1608276367188" height="463.21795654296875" fill="#B2DEFF"
                            clip-path="url(#clipImage-5)" data-svg-origin="654.0697631835938 643.4998168945312">
                        </rect>
                    </g>
                </svg>
            </div>

        </div>
    </div>
</template>

<script setup>
import { gsap } from 'gsap';

const svgRef = ref(null);
const items1 = ref()
const items2 = ref()
const items3 = ref()
const items4 = ref()
const bannerIndex = ref(0)
const timer = ref()
onMounted(() => {
    if (!svgRef.value) return;
    items1.value = svgRef.value.querySelectorAll('.fragment-item1');
    items2.value = svgRef.value.querySelectorAll('.fragment-item2');
    items3.value = svgRef.value.querySelectorAll('.fragment-item3');
    items4.value = svgRef.value.querySelectorAll('.fragment-item4');
    gsap.set(items1.value, {
        y: -160,
        x: 320,
    });
    gsap.set(items2.value, {
        y: 500,
        x: 1000,
    });
    gsap.set(items3.value, {
        y: -500,
        x: 1000,
    });
    gsap.set(items4.value, {
        y: 400,
        x: 800,
    });
    bannerIndex.value = 1
    timer.value = setInterval(() => {
        if (bannerIndex.value < 3) {
            bannerIndex.value++;
        } else {
            bannerIndex.value = 1
        }
        if (bannerIndex.value == 1) {
            onestart()
        } else if (bannerIndex.value == 2) {
            oneend()
        } else {
            twoend()
        }
    }, 6000);
});
const onestart = () => {
    gsap.to(items3.value, {
        duration: 0.7,
        y: -500,
        x: 1000,
    });
    gsap.to(items4.value, {
        duration: 0.7,
        y: 400,
        x: 800,
    });
    gsap.to(items1.value, {
        duration: 0.7,
        delay: 0.7,
        x: 0,
        y: 0,
    });
    gsap.to(items2.value, {
        duration: 0.7,
        delay: 1.4,
        x: 0,
        y: 0,
    });
}
const oneend = () => {
    gsap.to(items1.value, {
        duration: 0.7,
        delay: 0.7,
        y: -160,
        x: 320,
    });
    gsap.to(items2.value, {
        duration: 0.7,
        y: 500,
        x: 1000,
    });
    gsap.to(items3.value, {
        duration: 0.7,
        delay: 1.4,
        y: 80,
        x: -160,
    });
}
const twoend = () => {
    gsap.to(items3.value, {
        duration: 0.7,
        y: -500,
        x: 1000,
    });
    gsap.to(items4.value, {
        duration: 0.7,
        delay: 0.7,
        y: 0,
        x: 0,
    });
}
</script>
<style scoped lang="sass">
.bannerbox
    position: relative
    width: 100%
    .titlebox
        padding-top: 200px
        width: 90%
        margin: 0 auto
        position: relative
        @media (max-width: 768px)
            padding-top: 80px
        h1
            font-size: 84px
            font-weight: 300
            color: #1b215a
            line-height: 100px
            @media (max-width: 768px)
                font-size: 36px
                line-height: 42px
        .text
            position: absolute
            margin-top: 50px
            font-size: 38px
            width: 422px
            color: #1b215a
            font-weight: 300
            opacity: 0
            transition: all 0.5s
            pointer-events: none
            @media (max-width: 768px)
                font-size: 18px
                margin-top: 410px
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
                &:hover
                    background-color: #001aff
                    color: #fff
                    .arrow-outline
                        fill: #fff
                        border: 2px solid #fff
                @media (max-width: 768px)
                    margin-top: 15px
                    font-size: 14px
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
        .reditalic
            color: #ff4b3f
            font-style: italic
            font-family: 'LightItalic'
</style>
<style scoped>
.tanagram-wrapper {
    position: absolute;
    width: 75%;
    top: -160px;
    right: -10px;
    height: 100vh;
}

@media (max-width: 768px) {
    .tanagram-wrapper {
        width: 100%;
        top: 160px;
        right: -10px;
        height: 100vh;
    }
}

.banner-nav-slider-wrap {
    position: absolute;
    right: 40px;
    top: calc(100vh + 90px);
    z-index: 44;
    width: 650px;
    display: flex;
    justify-content: space-between;
}

.banner-nav-slider-wrap .items {
    width: 200px;
    font-size: 18px;
    color: rgba(28, 33, 86, 0.7);
    overflow: hidden;
}

@media (max-width: 768px) {
    .banner-nav-slider-wrap {
        display: none;
    }
}

.banner-nav-slider-wrap .line {
    width: 200px;
    background-color: rgba(28, 33, 86, 0.3);
    height: 3px;
    margin-bottom: 12px;
}

.banner-nav-slider-wrap .line .bar {
    /* width: 100%; */
    background-color: #ff4b3f;
    height: 3px;
    width: 0px;
    margin-left: -57px;
}

.tanagram-anim-wrap {
    height: 100vh;
    width: 100%;
    /* max-width: 900px; */
    /* 調整最大寬度 */
    /* 增加陰影，讓圖形更有立體感 */
}

.tanagram-svg {
    width: 100%;
    height: auto;
    display: block;
    overflow: visible;
    /* 允許碎片在進場時超出範圍 */
}

.fragment-item {
    /* 性能優化 */
    will-change: transform, opacity;
}

.banneractive {
    opacity: 1 !important;
    pointer-events: auto !important;
}

.baractive {
    width: 257px !important;
    background-color: #ff4b3f !important;
    transition: all 6s linear;
}

.fcolor {
    color: rgba(28, 33, 86) !important;
}

.opcisty image {
    opacity: 0;
    transition: all 1s;
}
</style>

<template>
    <div class="swiperbox">
        <swiper :modules="[SwiperNavigation, SwiperPagination]" :slides-per-view="1" :loop="true" :speed="600"
            @swiper="onSwiper" @slideChange="onSlideChange" class="my-swiper">
            <swiper-slide v-for="(item, index) in data" :key="index">
                <div class="carousel-content">
                    <div class="avatar-box">
                        <img :src="item.img" alt="avatar" />
                    </div>
                    <div class="text-box">
                        <p class="quote">{{ t(item.quote) }}</p>
                        <p class="author">
                            <span class="name">{{ t(item.name) }}</span> / {{ t(item.title) }}
                        </p>
                    </div>
                </div>
            </swiper-slide>
        </swiper>

        <div class="carousel-controls">
            <div class="custom-indicators">
                <span v-for="(_, index) in data" :key="index" class="dot"
                    :class="{ 'is-active': activeIndex === index }" @click="goToSlide(index)"></span>
            </div>

            <div class="custom-arrows">
                <button class="arrow-btn prev" @click="swiperInstance?.slidePrev()">
                    <svg viewBox="0 0 15.04 26.54">
                        <path
                            d="M14.15,23.88c-5-5-7.5-7.5-7.5-10.61s2.5-5.61,7.5-10.61l.89-.89-1.77-1.77L0,13.27l13.27,13.27,1.77-1.77-.89-.89Z">
                        </path>
                    </svg>
                </button>
                <button class="arrow-btn next" @click="swiperInstance?.slideNext()">
                    <svg viewBox="0 0 15.04 26.54">
                        <path
                            d="M.89,23.88c5-5,7.5-7.5,7.5-10.61S5.89,7.66.89,2.66l-.89-.89L1.77,0l13.27,13.27L1.77,26.54l-1.77-1.77.89-.89Z">
                        </path>
                    </svg>
                </button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation as SwiperNavigation, Pagination as SwiperPagination } from 'swiper/modules'
import 'swiper/css'
const { t } = useI18n()
// 接收外部傳入的數據
const props = defineProps({
    data: { type: Array, required: true }
})

const swiperInstance = ref(null)
const activeIndex = ref(0)

const onSwiper = (swiper) => {
    swiperInstance.value = swiper
}

const onSlideChange = (swiper) => {
    activeIndex.value = swiper.realIndex
}

const goToSlide = (index) => {
    swiperInstance.value?.slideToLoop(index)
}
</script>

<style scoped lang="sass">
$bg-navy: #162a44 // 圖片中的深藍色
$highlight-red: #f06a55 // 圖片中的點亮色


.swiperbox
    background-color: #152d48
    padding: 100px
    @media (max-width: 768px)
        padding: 50px 25px
    .carousel-content
        display: flex
        align-items: flex-start
        gap: 40px
        color: #fff
        @media (max-width: 768px)
            display: block
        .avatar-box
            width: 180px
            flex-shrink: 0
            img
                width: 100%
                border-radius: 4px
        .text-box
            .quote
                font-size: 40px
                line-height: 45px
                margin-bottom: 20px
                font-weight: 300
                // width: 1400px
                @media (max-width: 768px)
                    font-size: 22px
                    line-height: 25px
                    width: 100%
                    margin-top: 20px
            .author
                font-size: 22px
                color: rgba(255, 255, 255, 0.8)
                @media (max-width: 768px)
                    font-size: 16px
            .name
                color: #a8c5da // 圖片中名字的淺藍色
                font-style: italic
    .carousel-controls
        display: flex
        justify-content: space-between
        align-items: center
        margin-top: 40px
        padding-left: 220px // 與文字對齊 (avatar 寬度 180 + gap 40)
        @media (max-width: 768px)
            padding: 0
            margin: 0
    .custom-indicators
        display: flex
        gap: 12px
        .dot
            width: 10px
            height: 10px
            border-radius: 50%
            background-color: rgba(255, 255, 255, 1)
            cursor: pointer
            transition: all 0.3s
            &.is-active
                background-color: $highlight-red // 被選中的紅點
                // transform: scale(1.2)
    .custom-arrows
        display: flex
        gap: 15px
        @media (max-width: 768px)
            gap: 5px
        .arrow-btn
            width: 50px
            height: 50px
            border-radius: 50%
            border: 3px solid #fff
            background: transparent
            color: #fff
            display: flex
            align-items: center
            justify-content: center
            cursor: pointer
            transition: all 0.3s
            @media (max-width: 768px)
                transform: scale(0.8)
            &:hover
                background-color: #fff
                color: $bg-navy
                svg
                    fill: #152d48
        svg
            width: 15px
            height: 26px
            fill: #fff
            transition: all 0.3s
</style>
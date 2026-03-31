<template>
    <div class="it-carousel-wrapper">
        <swiper :modules="[Navigation]" :slides-per-view="1" :loop="true" :speed="600"
            :navigation="{ prevEl: prevBtnEl, nextEl: nextBtnEl }" @swiper="onSwiperInit" class="my-swiper">
            <swiper-slide v-for="(item, index) in carouselData" :key="index">
                <div class="slide-image-wrapper">
                    <img :src="item.image" alt="Carousel Slide" />
                </div>

                <div class="slide-content-box">
                    <p class="desc">{{ $lang(item.text) }}</p>
                </div>
            </swiper-slide>
        </swiper>

        <button ref="prevBtnEl" class="nav-btn prev">
            <svg id="Layer_1" xmlns="http://www.w3.org/2000/svg" width="15.04" height="30.54" viewBox="0 0 15.04 26.54">
                <path class="cls-1"
                    d="M14.15,23.88c-5-5-7.5-7.5-7.5-10.61s2.5-5.61,7.5-10.61l.89-.89-1.77-1.77L0,13.27l13.27,13.27,1.77-1.77-.89-.89Z">
                </path>
            </svg>
        </button>
        <button ref="nextBtnEl" class="nav-btn next"><svg id="Layer_1" xmlns="http://www.w3.org/2000/svg" width="15.04"
                height="30.54" viewBox="0 0 15.04 26.54">
                <path class="cls-1"
                    d="M.89,23.88c5-5,7.5-7.5,7.5-10.61S5.89,7.66.89,2.66l-.89-.89L1.77,0l13.27,13.27L1.77,26.54l-1.77-1.77.89-.89Z">
                </path>
            </svg></button>
    </div>
</template>

<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'

// 定義 Prop 數據類型
interface CarouselItem {
    image: string
    text: string
}

// 定義 Props
defineProps<{
    carouselData: CarouselItem[]
}>()

// 導航按鈕的 DOM 引用
const prevBtnEl = ref<HTMLElement | null>(null)
const nextBtnEl = ref<HTMLElement | null>(null)

// Swiper 初始化完成後的範例回調（可選用）
const onSwiperInit = (swiper: any) => {
    // console.log('Swiper 實例已就緒', swiper)
}
</script>

<style scoped lang="sass">
// 全局基礎樣式
.it-carousel-wrapper
  width: 100%
  position: relative
  border-radius: 5px

.my-swiper
  width: 100%
  height: auto

.swiper-slide
  display: flex
  flex-direction: column
  align-items: center

// 圖片區域
.slide-image-wrapper
  width: 100%
  aspect-ratio: 16 / 9 // 嚴格參考原圖比例
  overflow: hidden
  img
    width: 100%
    height: 100%
    object-fit: cover
    border-radius: 5px

// 文字區域
.slide-content-box
  width: 100%
  padding: 6px 0
  p.desc
    font-size: 16px
    color: #1b215a
    line-height: 1.2
    margin: 0
    text-align: justify // 讓兩端對齊，更整齊
    @media (max-width: 768px)
        font-size: 12px

// 自定義導航按鈕樣式
.nav-btn
  position: absolute
  top: calc(50% - 48px) // 居中
  width: 48px
  height: 48px
  border: 3px solid #1b215a
  border-radius: 50%
  color: #333
  font-size: 28px
  display: flex
  justify-content: center
  align-items: center
  cursor: pointer
  transition: all 0.3s ease
  z-index: 10
  fill: #1b215a
  opacity: .5
  @media (max-width: 768px)
    transform: scale(.75)
    border: 4px solid #1b215a
  
  &:hover
    background: #1b215a
    color: #000
    opacity: 1
    fill: #fff

  &.swiper-button-disabled
    opacity: 0.3
    cursor: default
    pointer-events: none // 徹底禁用鼠標交互

  &.prev
    left: -35px
    @media (max-width: 768px)
        left: -25px
  
  &.next
    right: -35px
    @media (max-width: 768px)
        right: -25px
</style>
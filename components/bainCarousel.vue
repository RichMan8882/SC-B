<template>
    <div class="bain-carousel-wrapper">
        <div class="custom-navigation">

            <h2 class="section-title">
                <div class="jihui">{{ $lang('機會') }}</div>{{ $lang('在貝恩資本，您可以') }}
            </h2>
            <div class="arrow-group">
                <button class="prev-el"><svg id="Layer_1" xmlns="http://www.w3.org/2000/svg" width="20.04"
                        height="40.54" viewBox="0 0 15.04 26.54">
                        <path class="cls-1"
                            d="M14.15,23.88c-5-5-7.5-7.5-7.5-10.61s2.5-5.61,7.5-10.61l.89-.89-1.77-1.77L0,13.27l13.27,13.27,1.77-1.77-.89-.89Z">
                        </path>
                    </svg></button>
                <button class="next-el"><svg id="Layer_1" xmlns="http://www.w3.org/2000/svg" width="20.04"
                        height="40.54" viewBox="0 0 15.04 26.54">
                        <path class="cls-1"
                            d="M.89,23.88c5-5,7.5-7.5,7.5-10.61S5.89,7.66.89,2.66l-.89-.89L1.77,0l13.27,13.27L1.77,26.54l-1.77-1.77.89-.89Z">
                        </path>
                    </svg></button>
            </div>
        </div>

        <swiper :modules="[Navigation, Pagination, Autoplay]" :slides-per-view="'auto'" :centered-slides="true"
            :speed="800" :space-between="130" :loop="false"
            :navigation="{ prevEl: '.prev-el', nextEl: '.next-el', disabledClass: 'swiper-button-disabled' }"
            :pagination="{ el: '.custom-pagination', clickable: true }" class="my-swiper">
            <swiper-slide>
                <div class="content-box">
                    <div class="text-side">
                        <span class="index-num">1</span>
                        <p class="desc">{{ $lang('在支持你、願意投資你的領導者的帶領下，加速你的職涯發展。') }}</p>
                    </div>
                    <div class="text-side">
                        <span class="index-num">2</span>
                        <p class="desc">{{ $lang('在協作、多元和包容的團隊中，個人應被賦予權力並承擔責任。') }}</p>
                    </div>
                    <div class="text-side">
                        <span class="index-num">3</span>
                        <p class="desc">{{ $lang('行事要自信，但也要謙遜。') }}</p>
                    </div>
                    <div class="text-side">
                        <span class="index-num">4</span>
                        <p class="desc">{{ $lang('對自己的工作及其結果負責，同時在我們所做的一切中產生正面影響。') }}</p>
                    </div>
                    <div class="text-side">
                        <span class="index-num">5</span>
                        <p class="desc">{{ $lang('秉持持續改善的理念，共同營造卓越文化。') }}</p>
                    </div>
                </div>
            </swiper-slide>
            <swiper-slide v-for="(item, index) in carouselData" :key="index">
                <div class="content-box">
                    <div class="text-side" style="margin-bottom: 50px;width: 1124px;">
                        <span class="index-num fs98">{{ index + 1 }}</span>
                        <p class="desc fs38">{{ $lang(item.text) }}</p>
                    </div>
                    <div class="image-grid">
                        <div v-for="(img, i) in item.images" :key="i" class="img-wrapper">
                            <img :src="img.img" alt="Bain People" />
                            <div class="maskbox">
                                <div class="maskboxtext">
                                    <div style="font-size: 32px;font-weight: 300;">{{ $lang(img.text) }}</div>
                                    <div style="font-size: 24px;width: 60%;margin: 0 auto;font-weight: 300;"><i
                                            style="color: #3fb6ff;">{{ $lang(img.name) }}</i> {{ $lang(img.span) }}
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </swiper-slide>
        </swiper>

    </div>
</template>

<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation, Pagination, Autoplay } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'
import avatar1 from '@/assets/images/eli-winkler.jpg'
import avatar2 from '@/assets/images/Martina-Yu-v1.jpg'
import avatar3 from '@/assets/images/philippe-kamel-v4.jpg'

const carouselData = [
    {
        text: "在支持你、願意投資你的領導者的帶領下，加速你的職涯發展。",
        images: [{
            img: avatar1,
            text: "我從來沒聽過「我太忙了」這種說法。通常情況下，人們都會說：“好的，我能幫上什麼忙嗎？”",
            name: "伊萊·溫克勒 /",
            span: "常務董事 / 私募股權 / 波士頓"
        }, {
            img: avatar2,
            text: "每個人都很重視你的看法。你有機會暢所欲言，表達自己的觀點，為團隊做出貢獻。",
            name: "餘瑪蒂娜 /",
            span: "常務董事 / 私募股權 / 香港"
        }, {
            img: avatar3,
            text: "從最基層的助理到最資深的合夥人，每個人的聲音都能被聽見。",
            name: "菲利普·卡梅爾 /",
            span: "主要的 / 私募股權 / 倫敦"
        }]
    },
    {
        text: "在協作、多元和包容的團隊中，個人應被賦予權力並承擔責任。",
        images: [{
            img: "https://cdn-east2.baincapital.com/2024-11/darren-abrahamson.jpg",
            text: "我為什麼要去別的地方？我知道從第一天起，我就能擁有充分的自主權來做好我的工作，同時我也會得到強而有力的支持。",
            name: "安德烈亞·盧西多 /",
            span: "導演 / 信用 / 紐約"
        }, {
            img: "https://cdn-east2.baincapital.com/2024-11/andrea-lucido.jpg",
            text: "每個人都很重視你的看法。你有機會暢所欲言，表達自己的觀點，為團隊做出貢獻。",
            name: "餘瑪蒂娜 /",
            span: "常務董事 / 私募股權 / 香港"
        }, {
            img: "https://cdn-east2.baincapital.com/2024-11/ashish-kotecha.jpg",
            text: "在這裡，如果你對自己的成長歷程負責，你就能接觸到一些最優秀的人才、最前衛的理念和最強大的工具。",
            name: "阿什什·科特查 /",
            span: "夥伴 / 私募股權 / 孟買"
        }]
    },
    {
        text: "行事要自信，但也要謙遜。",
        images: [{
            img: "https://cdn-east2.baincapital.com/2024-11/ryan-cotton.jpg",
            text: "我很快就明白，最優秀的人每天都非常清楚自己的限制。當你意識到並非所有責任都在自己身上時，肩上的壓力就會減輕很多。",
            name: "瑞安·科頓 /",
            span: "夥伴 / 房地產 / 波士頓"
        }, {
            img: "https://cdn-east2.baincapital.com/2024-11/alicia-hu.jpg",
            text: "投資不僅在於深入了解某個領域，更在於認知到自身知識的限制。自信固然重要，但也要認清自身的局限性，善於合作，並保持開放的心態。",
            name: "胡艾麗西亞 /",
            span: "主要的 / 特殊情況 / 香港"
        }, {
            img: "https://cdn-east2.baincapital.com/2024-11/ivano-sessa.jpg",
            text: "我們善於傾聽不同的觀點。我們沒有「這就是我們的觀點，僅此而已」的思考模式。我們通常會先提出假設，然後用事實來檢驗它。",
            name: "伊凡諾·塞薩 /",
            span: "夥伴 / 私募股權 / 倫敦"
        }]
    },
    {
        text: "對自己的工作及其結果負責，同時在我們所做的一切中產生正面影響。",
        images: [{
            img: "https://cdn-east2.baincapital.com/2024-11/grace-mollard.jpg",
            text: "在你職業生涯的早期就能產生影響，而且在整個職業生涯中，你都將成為一個相當小的團隊的一員，做出相當重大的決策。",
            name: "格蕾絲·莫拉德 /",
            span: "夥伴 / 私募股權 / 墨爾本"
        }, {
            img: "https://cdn-east2.baincapital.com/2024-11/amir-zamani.jpg",
            text: "我認為我們文化中一個很棒的元素是，每個人都感到有能力去推動和領導，從而取得我們共同擁有的成果。",
            name: "阿米爾·紮馬尼 /",
            span: "夥伴 / 生命科學 / 波士頓"
        }, {
            img: "https://cdn-east2.baincapital.com/2024-11/mudit-kedia.jpg",
            text: "我們不會限制自己能夠產生的影響。",
            name: "穆迪特·凱迪亞 /",
            span: "副總裁 / 特殊情況 / 孟買"
        }]
    },
    {
        text: "秉持持續改善的理念，共同營造卓越文化。",
        images: [{
            img: "https://cdn-east2.baincapital.com/2024-11/nimisha-kanani.jpg",
            text: "僅僅因為你一直以來都是以某種方式做事，並不代表這種方式就是正確的。我們一直在尋求進步和提升。",
            name: "尼米莎·卡納尼 /",
            span: "導演 / 投資人關係 / 倫敦"
        }, {
            img: "https://cdn-east2.baincapital.com/2024-11/nancy-lotane.jpg",
            text: "這是一種深入探究的思考方式，它提出了一系列越來越深刻的問題。它逐漸形成一種思考模式。我們追求這種思考模式，真正深入地從各個角度審視事物。",
            name: "南希·洛坦 /",
            span: "夥伴 / 平台服務 / 波士頓"
        }, {
            img: "https://cdn-east2.baincapital.com/2024-11/william-eleazer.jpg",
            text: "我不斷被激勵去做更多、做得更好，這讓我很興奮。很少有人會鼓勵我說：“嘿，你做得很棒，但我們再接再厲吧。”",
            name: "威廉·伊萊澤 /",
            span: "招募人員 / 創投 / 舊金山"
        }]
    }
]
</script>

<style scoped lang="sass">
.bain-carousel-wrapper
  padding: 80px 0
  position: relative
  color: #fff
  overflow: hidden

.custom-navigation
  display: flex
  justify-content: space-between
  align-items: flex-end
  margin-bottom: 40px
  padding: 0 260px
  @media (max-width: 768px)
    padding:  0 30px
    display: block
    margin-bottom: 0
  
  .section-title
    font-size: 84px
    font-weight: 300
    margin: 0
    @media (max-width: 768px)
        font-size: 36px
    .jihui
        font-size: 24px
        font-weight: 600
        @media (max-width: 768px)
            font-size: 16px

//   .arrow-group
//     display: flex
//     gap: 15px
//     button
//       width: 70px
//       height: 70px
//       border-radius: 50%
//       border: 3px solid #3d89c0
//       background: transparent
//       color: #3d89c0
//       cursor: pointer
//       transition: all 0.3s
//       display: flex
//       align-items: center
//       justify-content: center
//       svg
//         fill: #3d89c0
//       &:hover
//         background: #3fb6ff
//         color: #0e3053
//         border: 3px solid #3fb6ff
//         svg
//             fill: #fff
.arrow-group
  display: flex
  gap: 15px
  @media (max-width: 768px)
    justify-content: flex-end
    gap: 0px
  button
    width: 70px
    height: 70px
    border-radius: 50%
    border: 3px solid #3d89c0
    background: transparent
    color: #3d89c0
    cursor: pointer
    transition: all 0.3s
    display: flex
    align-items: center
    justify-content: center
    // 預設開啟鼠標事件
    pointer-events: auto 
    fill: #3d89c0
    // 正常狀態的 Hover
    @media (max-width: 768px)
        transform: scale(.5) translateX(50px)
        &:first-child
            transform: scale(.5) translateX(100px)
    &:hover
      background: #3fb6ff
      color: #0e3053
      border: 3px solid #3fb6ff
      svg
        fill: #fff

    // 關鍵：當 Swiper 判定到頭時會自動加上這個 class
    &.swiper-button-disabled
      opacity: 0.5
      border-color: rgba(61, 137, 192, 0.4)
      color: rgba(61, 137, 192, 0.4)
      cursor: default
      
      // 徹底禁用鼠標交互，這會讓上面的 &:hover 直接失效
      pointer-events: none

.my-swiper
  padding: 0 10% // 關鍵修正 2：縮小 padding 以露出更多側邊
  overflow: visible // 關鍵修正 3：必須 visible，側邊的 slide 才會顯示出來
  @media (max-width: 768px)
    padding: 0 10px
  
  .swiper-slide
    width: 92% // 關鍵修正 4：手動指定 slide 寬度，配合 auto 模式
    opacity: 0.6 // 非活動狀態變淡
    transition: opacity 0.6s ease, transform 0.6s ease
    .text-side
      transition: transform 0.5s 
      transform: translateX(-280px) // 當 Index 為 2 時，它的文字先往右移 200px
      @media (max-width: 768px)
        transform: none
    &.swiper-slide-active
      opacity: 1
      transform: scale(1)
      .text-side
        transform: translateX(0) // 文字回到原位

.content-box
  .text-side
    display: flex
    align-items: center
    width: 936px
    height: 122px
    border-top: 1px solid #1e5e94
    max-width: 100%
    @media (max-width: 768px)
        height: 90px
    &:first-child
        border: none
    .index-num
      font-size: 80px
      font-weight: 700
      color: rgba(255, 255, 255, 1)
      line-height: 0.8
      margin-right: 30px
      font-family: 'Martinass'
      @media (max-width: 768px)
        font-size: 40px
    .fs98
        font-size: 98px
        @media (max-width: 768px)
            font-size: 60px
    .desc
      font-size: 36px
      line-height: 43px
      color: #3fb6ff
      @media (max-width: 768px)
        font-size: 18px
        line-height: 22px
    .fs38
        font-size: 38px
        @media (max-width: 768px)
            font-size: 18px
  .image-grid
    display: flex
    // gap: 20px
    .img-wrapper
      flex: 1
      aspect-ratio: 3 / 4
      overflow: hidden
      border-radius: 4px
      position: relative
      @media (max-width: 768px)
        flex: none
        width: 280px !important
      &:hover
        .maskbox
            background-color: rgba(0, 0, 0, 0.7)
            .maskboxtext
                transform: translateY(0) !important
      .maskbox
        position: absolute
        width: 100%
        height: 100%
        left: 0
        background-color: rgba(0, 0, 0, 0)
        top: 0
        transition: all .3s
        .maskboxtext
            width: 100%
            height: 100%
            transform: translateY(100%)
            transition: all .3s
            padding: 80px 30px
            display: flex
            flex-direction: column
            justify-content: space-between
            div
                text-align: center
      img
        width: 100%
        height: 100%
        object-fit: cover

.custom-pagination
  margin-top: 40px
  display: flex
  justify-content: center
  gap: 10px
  :deep(.swiper-pagination-bullet)
    background: rgba(255, 255, 255, 0.3)
    opacity: 1
    width: 10px
    height: 10px
  :deep(.swiper-pagination-bullet-active)
    background: #3d89c0
</style>
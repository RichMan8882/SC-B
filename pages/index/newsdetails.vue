<script lang="ts" setup>
import Lenis from "@studio-freight/lenis"

const { t } = useI18n()
const siteStore = useSiteStore()
const router = useRouter()
onMounted(() => {
})

const toUrl = (url) => {
    window.open(url)
}
const goLink = (link) => {
    window.open(link)
}
const isTop = ref(false)

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
                <h2 class="ftitle">
                    <span>{{ $lang('訊息') }}</span> / {{ $lang('新聞稿') }} / {{ $lang('私募股權') }} / {{ $lang('2025年10月6日')
                    }}
                </h2>
                <h1 class="stitle">{{ $lang('貝恩資本完成第十四期旗艦私募股權基金募集，規模達140億美元') }}</h1>
                <div class="content">
                    <div class="left">
                        <div>{{ $lang('分享此頁面') }}</div>
                        <ul class="iconlist">
                            <li><i class="fa-regular fa-envelope"></i></li>
                            <li><i class="fa-brands fa-linkedin-in"></i></li>
                            <li><i class="fa-brands fa-twitter"></i></li>
                            <li><i class="fa-brands fa-facebook-f"></i></li>
                        </ul>
                        <div class="titles">{{ $lang('媒體聯絡人') }}</div>
                    </div>
                    <div class="right">
                        <img src="@/assets/images/newdeimg.jpg" alt="">
                        <article class="article-container">
                            <div class="article-body">
                                <p class="summary">
                                    {{ $lang('此次成功募集體現了貝恩資本全球私募股權平台的實力，該平台兼具規模優勢和差異化投資策略，目前管理的北美、歐洲和亞洲基金規模已超過270億美元。')
                                    }}
                                </p>

                                <section class="content-text">
                                    <p>
                                        <span style="font-weight: 700;">{{ $lang('波士頓 – 2025年10月3日–') }}</span>
                                        {{
                                            $lang('貝恩資本今日宣布，其最新旗艦私募股權基金－貝恩資本第十四期基金（「第十四期基金」）已完成募資，總募資額達140億美元，其中包括約118億美元的外部認購承諾，超過了其最初設定的100億美元目標。秉承公司一貫的模式，貝恩資本旗下關聯實體認購了剩餘資金，並成為該基金的最大單一投資者。')
                                        }}
                                    </p>
                                </section>

                                <section class="content-text">
                                    <p>
                                        {{
                                            $lang('第十四期基金與近期完成募集的歐洲第六期（2023年）和亞洲第五期（2023年）私募股權基金合計募集超過270億美元的承諾資本。貝恩資本的私募股權平台管理約680億美元的總資產，兼俱全球領先機構的規模優勢、區域性基金的靈活性以及全球一體化團隊的緊密協作。此次募資也反映了投資者對紀律嚴明、穩健發展、目標一致且業績歷經週期始終如一的私募股權平台的持續信任。')
                                        }}
                                    </p>
                                </section>

                                <section class="content-text">
                                    <p>
                                        {{
                                            $lang('第十四期基金是貝恩資本全球私募股權業務的最新一期，該業務自1984年以來一直秉持著貝恩資本一貫的投資策略。四十多年來，貝恩資本與許多管理團隊攜手合作，透過推動營運改善、釋放變革潛力以及實現永續規模化，協助企業發展與轉型。該私募股權團隊的投資涵蓋五個核心垂直領域——消費品、醫療保健、工業、服務和科技——並經常利用貝恩資本平台更廣泛的洞察力和資源。')
                                        }}
                                    </p>
                                </section>

                                <section class="content-text">
                                    <p>
                                        {{
                                            $lang('「四十多年來，貝恩資本始終致力於幫助企業充分發揮潛力，即使在複雜的市場環境中也能做到這一點，這已成為我們私募股權策略的基石，」合夥人兼全球私募股權聯席主管克里斯戈登表示。')
                                        }}
                                        {{
                                            $lang('「我們以成長為導向的投資策略，將全球視野與深厚的行業專長相結合，賦能公司及投資組合公司的每一位員工，助力他們實現變革性增長，並達到可持續的規模化發展。我們平台擁有一個務實、協作、一體化的團隊，這尤其契合當今的市場環境。憑藉投資者的持續支持和我們強大的全球平台，第十四期基金將繼續發展的重要全球。')
                                        }}
                                    </p>
                                </section>

                                <section class="content-text">
                                    <p>
                                        {{
                                            $lang('「在當今競爭激烈的環境中，規模龐大而缺乏自律是遠遠不夠的，」貝恩資本北美私募股權聯席主管兼合夥人戴維·漢弗萊補充道，「我們的策略始終是專注於貝恩資本能夠真正發揮優勢的投資機會——將行業專家與跨平台洞察以及我們全球團隊的資源相結合。')
                                        }}
                                    </p>
                                </section>

                                <section class="content-text">
                                    <p>
                                        {{ $lang(
                                            `貝恩資本的全球私募股權平台匯集了全球超過330位投資和投資組合專業人士，其中包括一支由近90位專家組成的專屬投資組合團隊。該團隊將深厚的產業專長與數位轉型、供應鏈和人才等領域的專業能力結合，並與投資團隊和管理團隊緊密合作，從盡職調查到最終收購，全程參與。這種差異化、實踐型的投資模式——過去十年中約80%的價值創造源於營運改善而非財務運作——使貝恩資本能夠打造可持續發展的企業，並在各種市場環境下取得持續穩定的業績。`
                                        ) }}
                                    </p>
                                </section>

                                <footer class="about-section">
                                    <h3>{{ $lang('關於貝恩資本：') }}</h3>
                                    <p class="content-text" style="margin-bottom: 0;">
                                        {{
                                            $lang('貝恩資本成立於1984年，是全球領先的私募股權投資公司之一。我們致力於為投資者、團隊、企業以及我們所在的社區創造持久的影響力。作為一家私募合夥制公司，我們秉持信念和協作文化，這些優勢使我們能夠創新投資方式、把握機會並創造卓越成果。我們的全球平台專注於五大投資領域：私募股權、成長型及創投、資本解決方案、信貸及資本市場以及實體資產。在這些重點領域，我們擁有深厚的產業專長和廣泛的能力。我們在四大洲設有24個辦事處，擁有超過1,850名員工，管理資產規模約1,850億美元。欲了解更多信息，請訪問')
                                        }}
                                    </p>
                                    <div class="social-links">
                                        <a href="http://www.baincapital.com">www.baincapital.com</a>。{{
                                            $lang('您也可以在LinkedIn和Twitter上關注@BainCapital。') }}
                                    </div>
                                </footer>
                            </div>
                        </article>
                    </div>
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
                            }}
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
                        <!-- <div>
                            <i class="fa-brands fa-linkedin-in"></i>
                        </div>
                        <div><i class="fa-brands fa-twitter"></i>
                        </div> -->
                    </div>
                </div>
            </div>
        </div>

        <!-- <FooterBottom></FooterBottom> -->
    </div>
</template>
<style scoped lang="sass">
.article-container
  width: 90%
  margin-top: 40px
  background-color: #fefcf5 // 匹配圖片中的米黃色背景
  color: #1b215a
  line-height: 1.2 // 匹配圖片中較寬的行間距
  font-size: 22px
  font-weight: 400 !important
  @media (max-width: 768px)
    font-size: 16px
    line-height: 22px
    width: 100%

.article-body

  .summary
    color: #1b215a // 頂部摘要使用深藍色
    margin-bottom: 10px
    font-style: italic

  .content-text
    margin-bottom: 25px
    color: #1b215a
    p
      margin-bottom: 20px
      text-align: justify // 兩端對齊

  .quote-section
    margin: 40px 0
    padding: 0 30px
    border-left: none // 圖片中沒有左邊框，是純文字縮進
    font-size: 1.1em
    color: #1b215a
    position: relative
    font-weight: 500
    
    // 如果想模擬引號
    &::before
      content: "「"
      position: absolute
      left: 0
    &::after
      content: "」"

  .about-section
    margin-top: 60px
    
    h3
      font-size: 24px
      font-weight: 600
      color: #1b215a
      margin-bottom: 15px
      @media (max-width: 768px)
        font-size: 16px
        line-height: 22px
    
    p
      font-size: 22px
      color: #1b215a
      @media (max-width: 768px)
        font-size: 16px
        line-height: 22px
    
    .social-links
      font-size: 22px
      @media (max-width: 768px)
        font-size: 16px
        line-height: 22px
      a
        color: #1b215a
        text-decoration: none
        &:hover
          text-decoration: underline
</style>
<style scoped lang="sass">
.bodybox
  background-color: #fefcf5
  transition: background .3s
  .container
    max-width: 90%
    margin: 0 auto
    padding-top: 180px
    padding-bottom: 200px
    @media (max-width: 768px)
        padding-top: 80px
    .tishi
        background-color: #ffc86b
        color: #1c2156
        padding: 20px
        border-radius: 5px
        margin: 50px 0
        font-weight: 500
        display: flex
        align-items: center
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
      @media (max-width: 768px)
        font-size: 36px
        line-height: 45px
        margin-top: 15px
    .ftitle
      font-size: 26px
      margin-top: 30px
      color: rgba(33, 37, 41, 0.75)
      width: 600px
      font-weight: 400
      @media (max-width: 768px)
        font-size: 16px
      span
        color: #001aff
    .content
        margin-left: calc(20dvw - 50px)
        display: flex
        gap: 30px
        width: 1200px
        margin-top: 70px
        max-width: 100%
        @media (max-width: 768px)
            margin-left: 0
            display: block
            margin-top: 40px
        .left
            padding-top: 5px
            border-top: 1px solid #726e6a
            color: #8285a5
            width: 20%
            @media (max-width: 768px)
                width: 100%
                font-size: 12px
            .iconlist
                display: flex
                margin-top: 8px
                li
                    width: 20px
                    height: 20px
                    display: flex
                    align-items: center
                    justify-content: center
                    color: #fff
                    background-color: #4e8dc4
                    border-radius: 50%
                    font-size: 12px
                    margin-right: 5px
                    transition: all .3s
                    &:hover
                        background-color: #eb1c36
            .titles
                font-size: 24px
                font-weight: 300
                margin-top: 70px
                @media (max-width: 768px)
                    font-size: 18px
                    margin-top: 40px
                    margin-bottom: 30px
        .right
            width: 80%
            @media (max-width: 768px)
                width: 100%
.foterboxbg
    padding: 100px
    @media (max-width: 768px)
        padding: 30px 25px
.bottomftr
    color: #1c2156
    font-weight: 400
    width: 100%
    display: flex
    justify-content: space-between
    align-items: center
    padding-top: 28px
    border-top: 1px solid #1c2156
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
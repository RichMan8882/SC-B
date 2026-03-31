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
const route = useRoute()
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
const peopledet = ref()
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
    peopledet.value = peopleList[route.query.id]
})
onUnmounted(() => {
    cancelAnimationFrame(rafId)
    lenis.destroy()
})
const peopleList = [
    {
        name: "達倫·亞伯拉罕森",
        role: "夥伴",
        department: "技術機會",
        location: "波士頓",
        img: avatar1,
        experience: '達倫·亞伯拉罕森於2005年加入貝恩資本。他是科技機會團隊的合夥人，負責領導應用軟體、基礎設施、網路安全、金融科技和醫療保健IT領域的投資。在此之前，達倫曾是北美私募股權團隊科技垂直領域的負責人。他曾主導公司的招募和培訓工作，並在波士頓和倫敦辦公室工作。',
        education: '達倫在哈佛商學院獲得工商管理碩士學位，並曾是貝克學者。他以最優等成績畢業於賓州大學華頓商學院，獲得經濟學學士學位。'
    },
    {
        name: "阿傑·阿加瓦爾",
        role: "夥伴",
        department: "創投",
        location: "舊金山，波士頓",
        img: avatar2,
        experience: '阿傑·阿加瓦爾 (Ajay Agarwal) 於 2003 年加入貝恩資本。他是合夥人，負責領導創投團隊在舊金山灣區的辦公室。阿傑專注於早期應用軟體和 SaaS 領域的投資。他熱衷於與早期創業家合作，幫助他們進行團隊建立、企業文化建設、產品市場契合度迭代以及早期市場推廣營運的規模化。阿傑的主要投資主題包括商業賦能、銷售和行銷職能的變革，以及利用大數據和機器學習技術改造商業應用。 2012 年和 2013 年，阿傑榮登福布斯全球百大創投家榜單 (Midas List)。<br><br>在加入貝恩資本之前，Ajay曾擔任Trilogy的銷售和行銷主管，在他的領導下，公司年收入成長至3億美元。此前，他曾是麥肯錫公司洛杉磯辦事處的顧問。',
        education: '阿傑擁有哈佛商學院的工商管理碩士學位和史丹佛大學的電機工程學士學位。他還擁有“配置解決方案的方法和裝置”的專利。'
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
        img: avatar4,
        experience: "Ankit Aggarwal 於 2025 年加入貝恩資本。他是合夥人，也是亞太私募股權團隊的成員，專注於醫療保健和消費領域的投資。<br><br>在加入貝恩資本之前，Ankit曾擔任KKR合夥人，專注於醫療保健、消費品、金融服務和工業領域的投資機會。在KKR期間，他深度參與了對Max Healthcare、JB Chemicals & Pharmaceuticals、Vini Cosmetics、Reliance Retail、Jio Platforms、Infinx、Advanta Seeds和Five Star Finance的投資。此前，他曾擔任華平投資的助理。他的職業生涯始於安永會計師事務所的投資銀行家。",
        education: 'Ankit 是印度特許會計師協會 (ICAI) 的註冊會計師，擁有德里大學的商學學士學位。'
    },
    {
        name: "沙基布·艾哈邁德",
        role: "合規副總裁",
        department: "公司的",
        location: "倫敦",
        img: avatar5,
        experience: "Shakeeb Ahmed 於 2024 年加入貝恩資本。他是合規團隊的副總裁，領導歐洲團隊。<br><br>在加入貝恩資本之前，Shakeeb 曾在 Permira Credit 工作，負責合規計畫的實施。在此之前，他曾在花旗集團倫敦交易部門工作，為全球利差產品業務提供合規支援。",
        education: 'Shakeeb 獲得了威斯敏斯特大學國際關係（戰爭與衝突研究方向）的學士學位。'
    },
    {
        name: "安娜·亞歷山德里亞",
        role: "薪資福利主管",
        department: "公司的",
        location: "波士頓",
        img: avatar6,
        experience: "Anna Alessandria 於 2022 年加入貝恩資本。她是貝恩資本全球人力資源資深副總裁兼薪資福利主管。<br><br>在加入貝恩資本之前，安娜曾任韋萊韜悅（WTW）全球金融服務（GFS）業務高級總監。在此職位上，她領導GFS的資產管理業務，致力於拓展WTW面向資產管理公司和其他金融服務公司的諮詢服務。她主導了與全面薪酬、薪酬透明度、投資專業人士和高階主管薪酬相關的複雜客戶專案。在加入WTW之前，安娜曾任職於MFS投資管理公司，離職前擔任全面薪酬副總裁。",
        education: '安娜在維吉尼亞大學獲得文學學士學位，並在波士頓學院獲得工商管理碩士學位。她持有WorldatWork頒發的註冊薪酬專家（CCP）證書。'
    },
    {
        name: "塔拉·艾琳",
        role: "夥伴",
        department: "信用",
        location: "波士頓",
        img: avatar7,
        experience: "塔拉·艾琳於2010年加入貝恩資本。她是信貸業務重整團隊的合夥人。在此之前，塔拉曾是產業研究團隊的成員，專注於消費品投資領域。<br><br>此前，她曾在花旗資本顧問公司擔任高收益信貸分析師，並在花旗環球市場槓桿投資組合部門工作。",
        education: '塔拉獲得了里士滿大學的理學學士學位。'
    },
    {
        name: "格雷森·艾利森",
        role: "常務董事",
        department: "信用",
        location: "波士頓",
        img: avatar8,
        experience: "格雷森·艾利森於2017年加入貝恩資本。他是流動性及結構性信貸團隊的董事總經理兼投資組合經理，主要負責我們的CLO管理業務。此前，他曾任職於行業研究團隊，並擔任建築和化學行業的行業主管。<br><br>在加入貝恩資本之前，他曾在富達和富國銀行工作。",
        education: '格雷森獲得了北卡羅來納州立大學的文學學士學位。'
    },
    {
        name: "埃里克·安德森",
        role: "夥伴",
        department: "私募股權",
        location: "波士頓",
        img: avatar9,
        experience: "Eric Anderson 於 2017 年加入貝恩資本。他是投資組合團隊的合夥人，也是北美私募股權團隊的成員。<br><br>在加入貝恩資本之前，埃里克曾在達美樂披薩擔任多個領導職務，最近的職位是國際營運執行副總裁。在達美樂任職期間，他負責該品牌大部分國際市場、國際業務策略、國際供應鏈和全球食品安全方面的工作。在加入達美樂之前，埃里克是貝恩公司重組業務部門——貝恩企業復興集團的領導者，參與了多個行業的整體業務轉型項目。他也曾在資訊安全和建材行業擔任商業領導職務。",
        education: '艾瑞克在維吉尼亞大學達頓商學院獲得工商管理碩士學位，並曾是該校的傑諾維斯學者。他也曾在聖路易斯華盛頓大學獲得文學學士學位，並曾是該校的洛伊學者。'
    },
    {
        name: "派崔克安德魯斯",
        role: "聯繫",
        department: "技術機會",
        location: "舊金山",
        img: avatar10,
        experience: "Patrick Andrews 於 2024 年加入貝恩資本。他是科技機會團隊的助理。<br><br>在加入貝恩資本之前，帕特里克曾擔任貝恩公司紐約辦事處的高級諮詢顧問。此前，他曾在Folio公司工作，該公司為酒店業提供採購到付款軟體解決方案。",
        education: '派崔克畢業於聖路易斯華盛頓大學，獲得數學學士學位，輔修電腦科學和金融學。'
    }
];
</script>

<template>
    <div class="cont">
        <headerTop :top="isTop" :white="true" :opacity="isTop"></headerTop>
        <div class="bodybox">
            <div class="container" v-if="peopledet">
                <h2 class="ftitle">{{ $lang('我們的人民') }}</h2>
                <h1 class="stitle">{{ t(peopledet.name) }}</h1>
                <div class="content">
                    <div class="left">
                        <img :src="peopledet.img" alt="">
                    </div>
                    <div class="right">
                        <article class="article-container">
                            <div class="article-body">
                                <section class="content-text">
                                    <p><span style="font-weight: 700;">{{ t(peopledet.role) }}</span>
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p><span style="font-weight: 700;">{{ t(peopledet.department) }}</span>
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p><span style="font-weight: 700;">{{ t(peopledet.location) }}</span>
                                    </p>
                                </section>
                                <div v-if="peopledet.experience" class="alti">{{ $lang('經驗') }}</div>
                                <section v-if="peopledet.experience" class="content-text">
                                    <p v-html="t(peopledet.experience)">
                                    </p>
                                </section>
                                <div v-if="peopledet.education" class="alti">{{ $lang('教育') }}</div>

                                <section v-if="peopledet.experience" class="content-text">
                                    <p>{{ t(peopledet.education) }}
                                    </p>
                                </section>
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
  background-color: #fefcf5 // 匹配圖片中的米黃色背景
  color: #1b215a
  line-height: 1.2 // 匹配圖片中較寬的行間距
  font-size: 22px
  font-weight: 400 !important
  @media (max-width: 768px)
    font-size: 16px
    width: 100%

.article-body
  .alti
    font-size: 18px
    color: #4e8dc4
    margin-top: 40px
    margin-bottom: 20px
    @media (max-width: 768px)
      font-size: 14px

  .content-text
    margin-bottom: 25px
    color: #1c2156
    @media (max-width: 768px)
        margin-bottom: 0
    p
      margin-bottom: 20px
      line-height: 30px
      text-align: justify // 兩端對齊
      @media (max-width: 768px)
        margin-bottom: 5px

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
    
    p
      font-size: 22px
      color: #1b215a
      @media (max-width: 768px)
        font-size: 16px
    
    .social-links
      font-size: 22px
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
    padding-bottom: 150px
    @media (max-width: 768px)
        padding-top: 70px
        padding-bottom: 0
    .stitle
      font-size: 84px
      color: #1b215a
      font-weight: 300
      @media (max-width: 768px)
        font-size: 36px
    .ftitle
      font-size: 20px
      margin-top: 30px
      color: #1b215a
      width: 600px
      font-weight: 500
      @media (max-width: 768px)
        font-size: 16px
      span
        color: #001aff
    .content
        margin-left: 300px
        display: flex
        gap: 50px
        width: 1200px
        margin-top: 70px
        max-width: 100%
        @media (max-width: 768px)
            margin-left: 0
            display: block
            margin-top: 50px
        .left
            color: #8285a5
            width: 35%
            @media (max-width: 768px)
                width: 100%
            img
                border-radius: 5px
                margin-bottom: 70px
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
<script lang="ts" setup>
import { ref, onMounted, onUnmounted } from 'vue'
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
  timer.value = setInterval(() => {
    bannerIndex.value++
    if (bannerIndex.value > 2) bannerIndex.value = 0
  }, 3000)
  document.documentElement.scrollTop = 0
  if (window) {
    console.log('window', window.innerWidth)
    window.addEventListener('scroll', handleScroll)
  }
  windowHeight.value = window.innerHeight
  window.addEventListener('resize', () => {
    windowHeight.value = window.innerHeight
  })
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
const bannerIndex = ref(0)
</script>

<template>
  <div class="cont">
    <headerTop></headerTop>
    <div class="bodybox">
      <section class="banner">
        <div
          :class="bannerIndex == 0 ? 'banneractive' : ''"
          class="item bgimg1"
        >
          <h2>独具一格</h2>
          <p>
            作为率先在中国开展风险投资业务的投资机构，IDG
            资本已发展成为一家扎根中国市场、具备全球化视野的私募股权投资机构。
          </p>
        </div>
        <div
          :class="bannerIndex == 1 ? 'banneractive' : ''"
          class="item bgimg2"
        >
          <h2>深度互信</h2>
          <p>
            IDG
            资本与包括主权基金/国家级出资平台、养老基金、专业金融机构、产业资本以及家族办公室等合作伙伴保持长期稳定的合作关系。
          </p>
        </div>
        <div
          :class="bannerIndex == 2 ? 'banneractive' : ''"
          class="item bgimg3"
        >
          <h2>卓越业绩</h2>
          <p>
            IDG 资本已扶植逾 600
            家企业通过在中国大陆、中国香港、美国、欧洲资本市场 IPO 或 M&A
            形式成功实现退出，支持了中国近一半的独角兽企业。
          </p>
        </div>
        <div class="drop">
          <div
            :class="bannerIndex == 0 ? 'dropactive' : ''"
            class="dropitem"
            @click="bannerIndex = 0"
          ></div>
          <div
            :class="bannerIndex == 1 ? 'dropactive' : ''"
            class="dropitem"
            @click="bannerIndex = 1"
          ></div>
          <div
            :class="bannerIndex == 2 ? 'dropactive' : ''"
            class="dropitem"
            @click="bannerIndex = 2"
          ></div>
        </div>
      </section>
      <section class="section2">
        <h2>我们的使命</h2>
        <div class="content">
          <div class="smitem">
            <img src="@/assets/images/indexb/icon-yj.svg" alt="" />
            <div>
              <h3>预见</h3>
              <p>正在发生的巨大变化</p>
            </div>
          </div>
          <div class="smitem">
            <img src="@/assets/images/indexb/icon-pb.svg" alt="" />
            <div>
              <h3>陪伴</h3>
              <p>有梦想有格局的未来开拓者</p>
            </div>
          </div>
          <div class="smitem">
            <img src="@/assets/images/indexb/icon-td.svg" alt="" />
            <div>
              <h3>推动</h3>
              <p>创造社会价值</p>
            </div>
          </div>
        </div>
      </section>
      <section class="section2">
        <h2>机构简介</h2>
        <p style="color: #666; line-height: 180%">
          IDG 资本自 1993
          年起扎根中国开展风险投资业务，是中国市场最活跃的私募股权基金管理人之一。2017
          年，IDG 资本完成收购 International Data Group（IDG
          集团）旗下的投资业务。这一举措标志着 IDG 资本已从 IDG
          集团完全拆分出来，并与 IDG
          集团旗下的其他出版、数据研究及会展等业务公司各自独立。自此，IDG
          资本的全球投资覆盖得以进一步扩展，跨境资源整合能力显著提升。
          <br />
          <br />
          IDG
          资本拥有业界最完整、经验最丰富的专业团队之一。团队成员具有多元化的行业背景以及全球化的投资视角和资源，教育及工作背景覆盖技术、市场、财务、法律、管理咨询、投资银行等多个行业。
          <br />
          <br />
          自 2001 年清科研究中心进行风险投资机构评选以来，IDG
          资本是唯一一家连续位居榜单 TOP5 的机构。
        </p>
      </section>
      <section class="section3">
        <h2>业务范围</h2>
        <div class="content">
          <div class="left">
            <img src="@/assets/images/indexb/business.jpg" alt="" />
            <div class="list">
              <div class="item3 itembg1"><span>种子期</span></div>
              <div class="item3 itembg2"><span>早期</span></div>
              <div class="item3 itembg3"><span>成长期</span></div>
              <div class="item3 itembg4"><span>并购期</span></div>
              <div class="item3 itembg5"><span>公开市场</span></div>
            </div>
          </div>
          <div class="right">
            <div class="ribox">
              <p>已开展投资：</p>
              <h4><span>30+</span>年</h4>
            </div>
            <div class="ribox">
              <p>IPO 及并购退出：</p>
              <h4><span>600+</span></h4>
            </div>
          </div>
        </div>
      </section>
      <section class="section4">
        <h2>投资领域</h2>
        <p>我们的投资主要集中在以下最具活力与成长性的行业：</p>
        <div class="content">
          <div class="item4">
            <img src="@/assets/images/indexb/tmt.svg" alt="" />
            消费科技
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/healthcare.svg" alt="" />
            大健康
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/consumer.svg" alt="" />
            消费
          </div>
        </div>
      </section>
      <section class="section4">
        <h2>我们的服务</h2>
        <p>
          除为企业发展提供资金以外，我们还在企业管理、全球化布局、退出策略、人力资源、法律与财务、品牌与市场等多方面为企业提供专业支持、经验和资源，帮助被投企业实现长足发展。
        </p>
        <div class="content">
          <div class="item4">
            <img src="@/assets/images/indexb/icon-qygl.svg" alt="" />
            企业管理
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/oversea.svg" alt="" />
            全球化布局
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/marketing.svg" alt="" />
            退出策略
          </div>
        </div>
        <div class="content">
          <div class="item4">
            <img src="@/assets/images/indexb/human.svg" alt="" />
            人力资源
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/icon-flcw.svg" alt="" />
            法律与财务
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/branding.svg" alt="" />
            品牌与市场
          </div>
        </div>
      </section>
      <div class="statement">
        <img src="@/assets/images/indexb/image.png" alt="" />
      </div>
    </div>
    <FooterBottom></FooterBottom>
  </div>
</template>

<style scoped lang="sass">

.bodybox
  max-width: 1120px
  padding: 96px 0
  margin: 0 auto
  position: relative
  .statement
    position: fixed
    top: 96px
    left: 50%
    width: 66px
    img
      margin-left: 580px
  .banner
    height: 395px
    position: relative
    .item
      position: absolute
      top: 0
      left: 0
      width: 100%
      height: 100%
      background-size: cover
      background-position: center
      padding: 0 80px
      padding-top: 100px
      color: #fff
      transition: opacity 1.2s
      background-repeat: no-repeat
      opacity: 0
      h2
        font-size: 60px
        text-shadow: 0 3px 2px rgba(0,0,0,0.25)
        margin-bottom: 20px
      p
        width: 460px
    .banneractive
      opacity: 1 !important
    .drop
      margin-top: 50px
      display: flex
      gap: 8px
      position: absolute
      left: 80px
      bottom: 60px
      .dropitem
        width: 40px
        height: 4px
        background-color: #817775
      .dropactive
        background-color: #bc171d
    .bgimg1
      background-image: url('@/assets/images/indexb/banner2.jpg')
    .bgimg2
      background-image: url('@/assets/images/indexb/homepage2-1600.jpg')
    .bgimg3
      background-image: url('@/assets/images/indexb/homepage4-1600.jpg')
  .section2
    margin-top: 100px

    .content
      display: flex
      justify-content: space-between
      padding: 20px 50px
      .smitem
        display: flex
        align-items: center
        gap: 32px
        h3
          margin: 0 0 10px
          color: #d92d3d
          font-size: 22px
        p
          color: #666
  .section3
    margin-top: 100px
    .content
      display: flex
    .left
      width: 69.6%
      .list
        display: flex
        background-color: #f4f6f7
        height: 200px
        overflow: hidden
        .item3
          width: 100%
          position: relative
          span
            position: absolute
            left: 50%
            top: 50%
            transform: translate(-50%,-50%)
            z-index: 3
            color: #656c6e
            transition: all .3s
          &::before
            content: ""
            width: 100%
            height: 100%
            position: absolute
            top: 0
            left: 0
            transform: translate3d(0, 100%, 0)
            transition: transform 0.25s
            background-repeat: no-repeat
            background-size: cover
            background-position: center center
            z-index: 1
          &::after
            content: ""
            width: 100%
            height: 100%
            position: absolute
            top: 0
            left: 0
            transform: translate3d(0, 100%, 0)
            transition: transform 0.25s
            background-repeat: no-repeat
            background-size: cover
            background-position: center center
            background-color: rgba(184, 21, 21, 0.85)
            z-index: 2
          &:hover
            &::after
              transform: translate3d(0, 0, 0)
            &::before
              transform: translate3d(0, 0, 0)
            span
              color: #fff
        .itembg1
          &::before
            background-image: url('@/assets/images/indexb/pic-1@2x.jpg')
        .itembg2
          &::before
            background-image: url('@/assets/images/indexb/pic-2@2x.jpg')
        .itembg3
          &::before
            background-image: url('@/assets/images/indexb/pic-3@2x.jpg')
        .itembg4
          &::before
            background-image: url('@/assets/images/indexb/pic-4@2x.jpg')
        .itembg5
          &::before
            background-image: url('@/assets/images/indexb/pic-5@2x.jpg')
    .right
      width: 300px
      padding-left: 70px

      .ribox
        color: #7a7a7a
        font-size: 20px
        border-bottom: 1px solid #dcdfe0
        padding: 35px 0
        span
          font-size: 60px
          font-weight: 100
          color: #333
  .section4
    margin-top: 100px
    p
      color: #666
      margin-bottom: 15px
    .content
      display: flex
      width: 100%
      border-bottom: 1px solid #d9dee1
      &:last-child
        border: 0px
      .item4
        width: 100%
        display: flex
        align-items: center
        height: 98px
        padding-left: 60px
        background-color: #f4f6f7
        color: #3d3c3c
        border-right: 1px solid #d9dee1
        &:last-child
          border: 0px
        img
          margin-right: 25px

  h2
    margin-bottom: 40px
    color: #2d292a
    padding-bottom: 10px
    font-weight: bold
    &::after
      width: 46px
      background-color: #bc171d
      overflow: hidden
      height: 2px
      position: absolute
      bottom: 0
      left: 0
      content: ""
</style>

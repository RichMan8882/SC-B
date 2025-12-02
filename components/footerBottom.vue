<script lang="ts" setup>
const siteStore = useSiteStore()
const { isLogin, signout } = useAuthStore()
const route = useRoute()
const routeName = route.matched[1].path
const menulist = ref([
  {
    title: '首頁',
    link: '/'
  },
  // {
  //   title: '被投企業',
  //   link: '/portfolio'
  // },
  {
    title: '企業責任',
    link: '/responsibility'
  },
  {
    title: '聯係我們',
    link: '/about'
  }
])
const footeraddresslist = ref([
  '香港',
  '北京',
  '上海',
  '广州',
  '深圳',
  '纽约',
  '波士顿',
  '新加坡市',
  '首尔',
  '河内',
  '胡志明市'
])
const activeindex = ref(0)
const tomenu = (item, index) => {
  // navigateTo(item)
  activeindex.value = index
}
</script>
<template>
  <footer>
    <div class="footer-bottom">
      <div class="content">
        <div class="introduce">
          <div class="footer-logo">
            <img :src="siteStore.siteData?.logo" alt=""></img>
          </div>
        </div>
        <div class="links">
          <dl>
            <dt>博裕 投資</dt>
            <dd v-for="(item, index) in menulist" :class="routeName == item.link ? 'active' : ''">
              <a href="javascript:void(0)" @click="tomenu(item.link, index)">{{ item.title }}</a>
            </dd>
          </dl>
          <!-- <dl>
            <dt>办公室</dt>
            <dd v-for="item in footeraddresslist">
              <a href="javascript:void(0)" @click="navigateTo('/')">{{ item }}</a>
            </dd>
          </dl> -->
        </div>
      </div>
      <div style="font-size: 14px;">
        {{ siteStore.siteData?.copyRight }}
      </div>
      <div class="line"></div>
      <div class="text">
        <span>透明與披露</span> |
        <span>法律責任</span> |
        <span>隱私説明</span>
      </div>
    </div>
  </footer>
</template>
<style scoped lang="sass">
footer
  background: #fff
  background: #3d3c3c
  padding: 30px 0
  color: #fff
  @media (max-width:768px)
    padding-top: 40px
    padding-bottom: 30px
  .footer-bottom
    width: 1120px
    margin: 0 auto
    
    .content
      display: flex
      justify-content: space-between
      flex-wrap: wrap
    @media (max-width: 1200px)
      width: 100%
      padding: 0 20px
    @media (max-width: 768px)
    .introduce
      max-width: 25%
      margin-bottom: 20px
      @media (max-width: 768px)
        max-width: 100%
        width: 100%
      .footer-logo
        height: 55px
        margin-bottom: 30px
        img
          height: 100%
      .footer-info
        font-size: 14px
    .links,.connect
      display: flex
      @media (max-width: 768px)
        width: 100%
        justify-content: space-around
        dl
          margin-left: 0 !important
      dl
        margin-left: 70px
        dt
          font-size: 21px
          color: #fff
          margin-bottom: 25px
          &::after
            content: ""
            display: block
            margin-top: 10px !important
            width: 30px !important
            height: 1px !important
            background: #d62328
        .active
          color: #d62334
        dd
          font-size: 14px
          margin-bottom: 8px
          .icon
            fill: #b6b6b6
            margin-right: 8px
            width: 16px
            height: 16px
            display: inline-block
          a
            transition: color .3s ease
            &:hover
              color: #fff
    .line
      border-top: 1px solid #fff
      margin: 20px 0
    .text
      font-size: 14px
      color: #999
      span
        &:hover
          color: #fff
</style>

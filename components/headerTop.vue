<script lang="ts" setup>
const siteStore = useSiteStore()
const { isLogin, signout } = useAuthStore()
const PlayerStore = usePlayerStore()
const route = useRoute()
const routeName = route.matched[1].path
const emit = defineEmits(['onPopupState'])
const props = defineProps({
  opaque: { type: Boolean, default: false },
  absolute: { type: Boolean, default: false },
  top: { type: Boolean, default: false },
  menu: { type: Boolean, default: true },
  styles: { type: String, default: '' },
  routerCrt: { type: String, default: '/' },
  headerW100: { type: String, default: '' }
})
const playerWalletBalance = computed(() => {
  if (!isLogin()) {
    return 0
  }
  console.log(PlayerStore.playerInfo, 'PlayerStore.playerInfo')

  const findWallet = PlayerStore.playerInfo?.wallet.find(
    (wallet: any) => wallet.type === 1
  )
  console.log(findWallet)

  if (findWallet) {
    return Number(findWallet.balance)
  } else {
    return 0
  }
})

const isCont = ref(false)
const isShw = ref(false)

const onPopup = () => {
  isShw.value = !isShw.value
  setTimeout(() => {
    isCont.value = !isCont.value
  }, 100)
}
const onClose = () => {
  isCont.value = !isCont.value
  setTimeout(() => {
    isShw.value = !isShw.value
  }, 300)
}
watch(
  () => isCont.value,
  (newVal) => {
    console.log('isCont.value', newVal)
    emit('onPopupState', newVal)
  }
)
const menulist = ref([
  {
    title: '首頁',
    link: '/'
  },
  {
    title: '被投企業',
    link: '/portfolio'
  },
  {
    title: '企業責任',
    link: '/responsibility'
  },
  {
    title: '聯係我們',
    link: '/about'
  }
])
const tomenu = (item) => {
  navigateTo(item)
}
</script>
<template>
  <div>
    <div class="header">
      <div class="content">
        <img :src="siteStore.siteData.logo" alt="" />
        <div class="btn-menu">
          <div
            class="item"
            :class="routeName == item.link ? 'active' : ''"
            v-for="item in menulist"
            @click="tomenu(item.link)"
          >
            {{ item.title }}
          </div>
        </div>
      </div>
    </div>
    <!-- popup -->
    <div v-show="isShw" class="popup-wrapper" @click.self="onClose">
      <div
        class="popup-content"
        :class="{
          'cont-left': isCont,
          dark:
            routerCrt == '/game/cointrading' ||
            routerCrt == '/game/perpetualcontract'
        }"
        @click.stop=""
      >
        <div class="popup-title">
          <span>
            <span v-if="isLogin() && menu">
              NT
              <i class="fa-solid fa-dollar-sign"></i>
              {{ new Intl.NumberFormat('zh-TW').format(playerWalletBalance) }}
            </span>
            <span v-if="isLogin() && !menu">
              {{ PlayerStore.playerInfo?.account }}
            </span>
          </span>
          <img
            src="data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjEiIGhlaWdodD0iMjAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PGcgc3Ryb2tlPSIjOEI5NUEwIiBzdHJva2Utd2lkdGg9IjIiIGZpbGw9Im5vbmUiIGZpbGwtcnVsZT0iZXZlbm9kZCIgc3Ryb2tlLWxpbmVjYXA9InNxdWFyZSI+PHBhdGggZD0iTTIuNSAxLjVsMTYuMjYzIDE2LjI2M00xOC41IDEuNUwyLjIzNyAxNy43NjMiLz48L2c+PC9zdmc+"
            alt=""
            @click="onClose"
          />
        </div>
        <div class="popup-menus">
          <ul class="menus" v-if="menu">
            <li class="menu-thumb">
              <a @click="navigateTo('/')">
                <span>首頁</span>
              </a>
            </li>
            <li>
              <a @click="navigateTo('/about')"> 關於我們 </a>
            </li>
            <li>
              <a @click="navigateTo('/service')">我們的服務</a>
            </li>
            <li>
              <a :href="siteStore.chatbox" target="_blank"> 聯絡我們 </a>
            </li>

            <li>
              <a @click="navigateTo('/user/info')"> 成員中心 </a>
            </li>
            <li v-if="isLogin()" class="menu-thumb">
              <a @click="navigateTo('/game')">
                <span>互動平臺</span>
              </a>
            </li>

            <li v-if="isLogin()">
              <a class="logout" @click="signout">Logout</a>
            </li>
          </ul>
          <ul class="menus" v-if="!menu">
            <li class="has-dropdown menu-thumb">
              <a
                @click="navigateTo('/game')"
                :style="{ color: routerCrt == '/' ? '#7354ff !important' : '' }"
                >首頁</a
              >
            </li>
            <li class="has-dropdown menu-thumb">
              <a
                @click="navigateTo('/game/cointrading')"
                :style="{
                  color:
                    routerCrt == '/game/cointrading' ? '#7354ff !important' : ''
                }"
              >
                幣幣交易
              </a>
            </li>
            <li>
              <a
                @click="navigateTo('/game/perpetualcontract')"
                :style="{
                  color:
                    routerCrt == '/game/perpetualcontract'
                      ? '#7354ff !important'
                      : ''
                }"
                >永續合約</a
              >
            </li>
            <li>
              <a :href="siteStore.chatbox" target="_blank"> 聯絡我們 </a>
            </li>
            <li v-if="isLogin()">
              <a class="logout" @click="signout">Logout</a>
            </li>
          </ul>
        </div>
        <div class="popup-btn"></div>
      </div>
    </div>
  </div>
</template>
<style scoped lang="sass">
.header
  position: fixed
  z-index: 12
  left: 0
  top: 0
  width: 100%
  height: 96px
  background-color: #fff
  .content
    max-width: 1120px
    margin: 0 auto
    display: flex
    height: 100%
    justify-content: space-between
    align-items: center
    img
      height: 50px
    .btn-menu
      display: flex
      height: 100%
      justify-content: flex-end
      .item
        display: flex
        align-items: center
        height: 100%
        margin-left: 60px
        color: #2d292a
        cursor: pointer
      .active
        border-top: 6px solid #d62334
        color: #d62334
        height: calc( 100% - 6px )
</style>
<style scoped lang="sass">
.dark
  background-color: #14171a !important
  color: #fff !important
  .menu-thumb,a
    color: rgba(255,255,255, 0.6) !important
    transition: all 0.2s ease-in-out
    &:hover
      color: rgba(255,255,255, 0.9) !important
.opaque
  background: #FFFFFF
  color: #111
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1)
  .header .menu-btn
    min-width: 4.0625rem !important
    .icon,.edit-icons
      fill: #111 !important
      color: #111 !important
    .edit-icons
      fill: #11111199 !important
      &:hover
        fill: #111 !important
    .menu-log
      border: 1px solid #333 !important
      &:hover
        border: 1px solid #7354ff !important
    .menu-login
      border: 1px solid #7354ff !important
      &:hover
        background: #7354ff
        color: #fff !important
.absolute
  position: absolute
  z-index: 9
.popup-wrapper
  position: fixed
  top: 0
  left: 0
  width: 100%
  height: 100%
  background: rgba(0, 0, 0, 0.2)
  z-index: 100
  display: flex
  justify-content: center
  align-items: center
  @media (min-width: 1200px)
    display: none
  .popup-content
    overflow-y: scroll
    position: absolute
    top: 0
    background-color: #fff
    width: 100%
    transform: translateY(-100%)
    transition: all 0.3s ease-in-out
    .popup-title
      display: flex
      justify-content: space-between
      align-items: center
      padding-block-start: 1rem
      &>span
        margin-left: 15px
      img
        width: 1rem
        height: 1rem
        margin-inline: 1rem
        cursor: pointer
    .popup-menus
      .menus
        list-style: none
        padding: 20px 0 0
        margin-block-end: 1.5625rem
        &>li
          margin-inline: 15px
          cursor: pointer
          // border-block-end: 1px solid #ccc
          color: #11111199
          min-height: 40px
          overflow: hidden
          transition: all 0.5s ease-in-out
          font-size: .9rem
          &>a
            display: flex
            justify-content: space-between
            align-items: center
            text-decoration: none
            height: 40px
            transition: all .2s
            &:hover
              color: #000
            .icon
              width: 1.5rem
              height: 1.5rem
              transition: all 0.2s ease-in-out
          .submenu
            &>li
              height: 46px
              line-height: 46px
              padding-inline: 15px
              &:hover
                color: #333333
        .logout
          width: 100%
          border: 1px solid #ccc
          height: 46px
          line-height: 46px
          border-radius: .4rem
          margin-block: .8rem
          color: #7354ff99
          text-align: center
          justify-content: center
          font-size: 1.2rem
          transition: all 0.2s ease-in-out
          &:hover
            border: 1px solid #7354ff99
            background: #7354ff
            color: #fff
        .has-dropdown:hover
          max-height: 999px
          a .icon
            transform: rotate(180deg) !important
  .cont-left
    transform: translateX(0%)
</style>

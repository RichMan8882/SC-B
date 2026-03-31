<script lang="ts" setup>
const siteStore = useSiteStore()
const { queryChatbox } = siteStore
const { signin } = useAuthStore()
const passwordEyes = ref(false)
const recaptchaCode = ref('')
const recaptchaCheckFunction = ref(null)
const { t } = useI18n()

const fetchSigninApi = ref({
  account: '',
  password: ''
})

const showPassword = (type: boolean) => {
  passwordEyes.value = type
}

const setLogin = async () => {
  if (!fetchSigninApi.value.account) {
    ElMessage({
      message: t('請輸入帳號'),
      type: 'error'
    })
    return
  }
  if (!fetchSigninApi.value.password) {
    ElMessage({
      message: t('請輸入密碼'),
      type: 'error'
    })
    return
  }
  const recaptchaCheck = await recaptchaCheckFunction.value?.validate(
    recaptchaCode.value
  )
  if (!recaptchaCheck) {
    ElMessage({
      message: t('驗證碼錯誤'),
      type: 'error'
    })
  } else {
    const res = await signin(fetchSigninApi.value)

    if (res.success) {
      navigateTo('/')
    }
  }
}
const checkHepler = async (data) => {
  recaptchaCheckFunction.value = data
}

await useAsyncData(async () => {
  if (!router.currentRoute.value.name.inCludes('model')) {
    if (isLogin()) {
      navigateTo('/')
    }
  }
})
const timer = ref()
onMounted(async () => {
  timer.value = setInterval(() => {
    bannerIndex.value++
    if (bannerIndex.value > 9) bannerIndex.value = 0
  }, 3000)
  const queryChatboxPromise = queryChatbox()
  queryChatboxPromise
    .then((queryChatboxRes) => {
      // 處理響應結果
      console.log('queryChatboxRes', queryChatboxRes.data)
    })
    .catch((error) => {
      console.error('Error loading queryChatboxRes data:', error)
    })
})

definePageMeta({
  layout: 'auth'
})
const openChatBox = () => {
  window.open(siteStore.chatbox, '_blank')
}
const bannerIndex = ref(0)
</script>

<template>
  <div class="layouts-auth">
    <div class="layouts-auth__video">
      <img src="@/assets/images/Background.png" alt="">
    </div>
    <div class="main-icon">
      <!-- <img :src="siteStore?.siteData.logo" /> -->
      <img src="@/assets/images/bain-capital-logo.svg" alt="">
    </div>
    <div class="header-main">
      <div class="header-left-bottom">
        <div class="title">
          {{ $lang('客戶端登入') }}
        </div>
        <div class="icon1">
          <span style="font-weight: bold">{{ $lang('金流帳號') }}</span>
          <input v-model="fetchSigninApi.account" v-trim-input type="text" name="acc" class="inputStyle" />
        </div>
        <div class="icon1">
          <span style="font-weight: bold">{{ $lang('輸入密碼') }}</span>
          <input v-model="fetchSigninApi.password" v-trim-input type="password" name="pass" class="inputStyle" />
        </div>

        <div class="icon1">
          <recaptcha @check-hepler="checkHepler"></recaptcha>
        </div>
        <div class="icon1">
          <span style="font-weight: bold">{{ $lang('驗證碼') }}</span>
          <input v-model="recaptchaCode" v-trim-input type="text" class="inputStyle" @keyup.enter="setLogin" />
        </div>
        <div class="textl">
          {{ $lang('如果您是第一次登入數位資料交換平台，請前往解鎖帳戶。') }}
        </div>

        <div class="loginbox">
          <div class="btn" @click="setLogin">{{ $lang('提交') }}</div>
        </div>
        <div class="links">
          <div>
            <span @click="navigateTo('/')">{{ $lang('返回首頁') }}</span> |
            <span>{{ $lang('客戶端登入') }}</span> |
            <span>{{ $lang('技術支援') }}</span>
          </div>
          <div>
            <span @click="openChatBox()">{{ $lang('忘記密碼了嗎？') }}</span> |
            <span>{{ $lang('忘記郵件地址？') }}</span> |
            <span @click="navigateTo('/register')">{{ $lang('解鎖帳戶') }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="sass">
@keyframes backgroundSwitch
  from
    transform: translateX(0)
  to
    transform: translateX(-100%)
.layouts-auth
  position: relative
  width: 100%
  min-height: 100dvh
  &__video
    // position: absolute
    // top: 0
    height: 100vh
    // right: 0
    // bottom: 0
    // left: 0

    // width: auto

    // overflow: hidden
    // display: flex
    //background-position: center
    //background-size: cover
    //filter: grayscale(1)
    //> video
    //  width: 100%
    //  height: 100%
    //  object-fit: cover
    //  object-position: center
  &__view
    position: absolute
    top: 0
    right: 0
    bottom: 0
    left: 0
    overflow-x: hidden
    overflow-y: auto
  .up,.up2
    height: 50vh
    display: flex
    flex-wrap: nowrap
    .bgimg
      display: flex
      flex-wrap: nowrap
      animation: backgroundSwitch 35s linear infinite
      img
        width: auto
        max-width: 99999px
        height: 50vh
        flex-shrink: 0
        // object-fit: cover
</style>

<style scoped lang="sass">
@import '@/assets/sass/login/model4/page.sass'

.page-login
  padding-top: 75px
  &__form
    @include form-section()
    margin: 0 auto
    &-title
      @include page-font()
      color: $primary-color
      text-align: center
      font-size: 28px
      margin-bottom: 34px
    &-fields
      margin-bottom: 44px
    &-input
      &:not(:last-child)
        margin-bottom: 28px
      &--text
        @include form-input(26px, 26px)
      &--code
        @include form-input(100px, 44px)
    &-submit
      display: flex
      justify-content: center
      width: 100%
      margin-bottom: 20px
      > button
        @include page-button-font()
        width: 100%
        max-width: 227px
        line-height: 21px
        padding: 15px 16px
        color: $primary-color
        background-color: rgba(0,0,0,0)
        border: 1px solid $primary-color
        outline: none
    &-actions
      display: flex
      flex-direction: column
      align-items: center
      margin-bottom: 20px
      &-wrap
        display: flex
        flex-direction: row
        > *:not(:last-child)
          margin-right: 20px
    &-divide
      width: 100%
      height: 1px
      background-color: $primary-color
      margin: 30px 0 40px
    &-button
      font-family: -apple-system, "system-ui", "Microsoft Jheng Hei", PingFang, 蘋方, 微軟正黑體, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol"
      font-size: 15px
      line-height: 22.5px
      color: $primary-color
      outline: none
</style>
<style scoped lang="sass">
// .bg-layer
//   background: rgba(0, 0, 0, 50%)
//   min-height: 100vh


.header-main
  width: 450px
  z-index: 999
  background: #1c2156
  position: absolute
  top: 50%
  left: 50%
  transform: translate(-50%,-50%)
  max-width: 100%

.main-icon
  text-align: center
  margin: 0 auto 20px
  position: absolute
  z-index: 999
  left: 28px
  top: 28px

  img
    width: 100%
img
  max-width: 100%
.loginbox
  width: 100%
  display: flex
  justify-content: flex-end
.textl
  padding: 12px 40px 20px 10px
  color: #fff
  font-size: 12px
  text-align: center
.icon1
  // margin: 0 0 1em
  padding: 6px 1em
  color: black
  display: flex
  align-items: center
  justify-content: center
  color: #fff
  input
    color: #000
  span
    min-width: 64px !important
    font-size: 14px
    text-align: right
    // white-space: nowrap

.bottom
  margin: 1em 0 0
.header-left-bottom
  .title
    padding: 10px 15px
    font-size: 24px
    color: #fff
    margin-bottom: 10px
.header-left-bottom .btn
  background: #0047bb
  color: #fff
  font-size: 14px
  // transition: 0.5s all
  cursor: pointer
  margin: 10px 10px 10px 20px
  width: 78px
  height: 36px
  display: flex
  align-items: center
  justify-content: center
  &:hover
    background: #e52823
a
  color: #585858
  margin: 0em

.header-left-bottom p
  font-size: 17px
  color: #000
  display: inline-block
  width: 50%
  margin: 20px 0 0
  letter-spacing: 1px
  float: left

  a
    font-size: 16px
    font-weight: bold
    color: #000000
    text-transform: uppercase
.links
  cursor: pointer
  border-top: 1px solid #e7e7e7
  padding: 15px 0
  color: #fff
  text-align: center
  font-size: 14px
  span
    &:hover
      text-decoration: underline
      text-decoration-color: #fff
  .right
    text-align: right
.inputStyle
  width:100%
  padding: 8px
  margin-left: 10px
  border: 1px solid black
  // opacity: 0.4
  background-color: #abcae9
  height: 30px
  width: 270px
  border-radius: 5px
.banneractive
  opacity: 1 !important
.swimg
  position: absolute
  top: 0
  left: 0
  height: 100%
  width: 100dvw
  opacity: 0
  transition: opacity 1.2s
  object-fit: cover
</style>

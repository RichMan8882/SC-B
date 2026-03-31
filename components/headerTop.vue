<script lang="ts" setup>
const siteStore = useSiteStore()
const { queryChatbox } = siteStore
const { isLogin, signout } = useAuthStore()
const PlayerStore = usePlayerStore()
const emit = defineEmits(['onPopupState'])
const route = useRoute()
const routeName = route.matched[1].path
const props = defineProps({
  opacity: { type: Boolean, default: true },
  white: { type: Boolean, default: false },
  opaque: { type: Boolean, default: true },
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
onMounted(() => {
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
console.log(props.styles, 'stylesstyles');
const ismore = ref(false)
const isWhite = ref(false)
const goLink = (link) => {
  window.open(link)
}
const searchbox = ref(false)
const openmore = (e) => {
  isShw.value = e
  isCont.value = e
  ismore.value = e
  isWhite.value = e
  searchbox.value = false
  console.log(searchbox.value, 'searchbox.value');
}
const menuIndex = ref(1)
const { locale } = useI18n()
const changeLang = (value) => {
  console.log(value);
  locale.value = value
}
console.log(props.menu, 'menu');
const closeAll = () => {
  isShw.value = false
  isCont.value = false
}
</script>
<template>
  <div>
    <header :class="{
      opaque: props.opaque,
      absolute: absolute,
      opacity: opacity,
      top: top,
      white: white || isWhite || isShw
    }" :style="styles">
      <div v-if="menu" class="topmore">
        <div class="left"><span v-if="!ismore" @click="openmore(true)">{{ $lang('更多的') }}</span><span
            @click="openmore(false)" v-else>{{ $lang('關閉') }}</span> <span class="caret"
            :class="ismore ? 'xuanzhuan' : ''"></span>
        </div>
        <div class="right">
          <div @click="navigateTo('/login')" class="sstop">{{ $lang('投資者登入') }}
            <div class="bgbbox"></div>
            <div class="texttop">{{ $lang('投資者登入') }}</div>
          </div>
          <div @click="goLink('https://www.baincapital.com/locations')" class="sstop">{{ $lang('地點') }}
            <div class="bgbbox"></div>
            <div class="texttop">{{ $lang('地點') }}</div>
          </div>
          <div v-if="!searchbox" @click="searchbox = true, isShw = true, ismore = false, isWhite = true" class="sstop">
            {{ $lang('搜尋') }}<i style="margin-left: 3px;" class="fa-solid fa-magnifying-glass"></i></div>
          <div v-else @click="searchbox = false, isShw = false, openmore(false)" class="sstop closesstop">
            {{ $lang('關閉') }}<img src="@/assets/images/close.svg" alt="">
          </div>
        </div>
      </div>
      <div class="header" :style="{ height: white || isWhite || isShw ? '58px' : '90px' }">
        <div class="logo"
          :style="{ width: white || isWhite ? '200px' : '', paddingTop: white || isWhite || isShw ? '15px' : '30px' }"
          @click="navigateTo('/')">
          <!-- <img src="@/assets/images/bain-capital-logo.svg" alt=""> -->
          <img :src="siteStore?.siteData.logo" />
        </div>
        <ul class="menu menu-pc "
          :class="[(white || isWhite ? 'noline' : 'blueline'), { 'englishmenu': locale == 'en_US' }]" v-if="menu">
          <li :class="routeName == '/about' ? 'active' : ''">
            <a @click="navigateTo('/about')">{{ $lang('關於我們') }}</a>
            <div class="menumask" :class="white ? 'iszhetou' : ''"></div>
            <div class="menu-point"></div>
            <div class="topmenubox">
              <div class="main">
                <div class="menul">
                  <div class="menurte" style="margin:0;margin-bottom: 10px;">{{ $lang('關於我們') }}</div>
                  <div class="menurlink">{{ $lang('探索') }}<div class="arrow-outline outlines">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="meleli">{{ $lang('概述') }}</div>
                  <div class="meleli">{{ $lang('宗旨和價值觀') }}</div>
                  <div class="meleli">{{ $lang('我們如何合作') }}</div>
                  <div class="meleli">{{ $lang('我們的全球佈局') }}</div>
                </div>
                <div class="menur" style="margin-left: 12px;">
                  <div class="temte" style="font-size: 16px;color: #000;font-weight: 600;">{{ $lang('致力於產生持久影響') }}
                  </div>
                  <div class="imgbox">
                    <img src="@/assets/images/homepage-banner.jpg" alt="">
                  </div>
                  <div class="meleli" style="font-size: 18px;font-weight: 600;color: #001aff;">{{
                    $lang('用我們的話語來說，我們的宗旨') }}</div>
                </div>
              </div>
            </div>
          </li>
          <li class="has-dropdown menu-thumb" :class="routeName == '/' ? 'active' : ''">
            <a @click="navigateTo('/')">{{ $lang('企業') }}</a>
            <div class="menumask" :class="white ? 'iszhetou' : ''"></div>
            <div class="menu-point"></div>
            <div class="topmenubox">
              <div class="main">
                <div class="menul">
                  <div @mouseenter="menuIndex = 1" :style="{ color: menuIndex == 1 ? '#1b215a' : '' }" class="mlti">{{
                    $lang('私募股權') }}
                  </div>
                  <div @mouseenter="menuIndex = 2" :style="{ color: menuIndex == 2 ? '#1b215a' : '' }" class="mlti">
                    {{ $lang('成長與創投') }}</div>
                  <div @mouseenter="menuIndex = 3" :style="{ color: menuIndex == 3 ? '#1b215a' : '' }" class="mlti">
                    {{ $lang('資本解決方案') }}
                  </div>
                  <div @mouseenter="menuIndex = 4" :style="{ color: menuIndex == 4 ? '#1b215a' : '' }" class="mlti">{{
                    $lang('信用') }}
                  </div>
                  <div @mouseenter="menuIndex = 5" :style="{ color: menuIndex == 5 ? '#1b215a' : '' }" class="mlti">{{
                    $lang('實體資產') }}
                  </div>
                </div>
                <div v-if="menuIndex == 1" class="menur">
                  <div class="menurt">{{ $lang('私募股權') }}</div>
                  <div class="menurte">{{ $lang('我們如何創造價值') }}</div>
                  <div class="menurcon">{{ $lang('憑藉著深厚的產業專業知識與能力，協助企業轉型升級。') }}</div>
                  <div class="menurte">{{ $lang('我們如何投資') }}</div>
                  <div class="menurlink">{{ $lang('全球私募股權') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="menurlink">{{ $lang('雙重衝擊') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="menurlink">{{ $lang('保險') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                </div>
                <div v-if="menuIndex == 2" class="menur">
                  <div class="menurt">{{ $lang('成長與創投') }}</div>
                  <div class="menurte">{{ $lang('我們如何創造價值') }}</div>
                  <div class="menurcon">{{ $lang('與富有遠見的領導者合作，加速從種子輪到規模化成長。') }}</div>
                  <div class="menurte">{{ $lang('我們如何投資') }}</div>
                  <div class="menurlink">{{ $lang('創投') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="menurlink">{{ $lang('生命科學') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="menurlink">{{ $lang('技術機會') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="menurlink">{{ $lang('加密貨幣') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                </div>
                <div v-if="menuIndex == 3" class="menur">
                  <div class="menurt">{{ $lang('資本解決方案') }}</div>
                  <div class="menurte">{{ $lang('我們如何創造價值') }}</div>
                  <div class="menurcon">{{ $lang('針對不同類型的資產、產業、市場和業務生命週期，建構客製化解決方案。') }}</div>
                  <div class="menurte">{{ $lang('我們如何投資') }}</div>
                  <div class="menurlink">{{ $lang('特殊情況') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                </div>
                <div v-if="menuIndex == 4" class="menur">
                  <div class="menurt">{{ $lang('信用') }}</div>
                  <div class="menurte">{{ $lang('我們如何創造價值') }}</div>
                  <div class="menurcon">{{ $lang('透過嚴謹的分析和涵蓋整個信貸領域的解決方案，創造投資機會。') }}</div>
                  <div class="menurte">{{ $lang('我們如何投資') }}</div>
                  <div class="menurlink">{{ $lang('信用') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                </div>
                <div v-if="menuIndex == 5" class="menur">
                  <div class="menurt">{{ $lang('實體資產') }}</div>
                  <div class="menurte">{{ $lang('我們如何創造價值') }}</div>
                  <div class="menurcon">{{ $lang('建構下一代房地產資產。') }}</div>
                  <div class="menurte">{{ $lang('我們如何投資') }}</div>
                  <div class="menurlink">{{ $lang('房地產') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="menurlink">{{ $lang('特殊情況') }}<div class="arrow-outline">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </li>
          <li :class="routeName == '/sustainability' ? 'active' : ''">
            <a @click="navigateTo('/sustainability')">{{ $lang('永續性與影響') }}</a>
            <div class="menumask" :class="white ? 'iszhetou' : ''"></div>
            <div class="menu-point"></div>
            <div class="topmenubox">
              <div class="main">
                <div class="menul">
                  <div class="menurte" style="margin:0;margin-bottom: 10px;">{{ $lang('永續性與影響') }}</div>
                  <div class="menurlink">{{ $lang('探索') }}<div class="arrow-outline outlines">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="meleli">{{ $lang('積極的治理與管理') }}</div>
                  <div class="meleli">{{ $lang('永續成長和減少氣候影響') }}</div>
                  <div class="meleli">{{ $lang('公平就業、參與和福祉') }}</div>
                  <div class="meleli">{{ $lang('多元化、公平性和包容性') }}</div>
                  <div class="meleli">{{ $lang('社區參與') }}</div>
                </div>
                <div class="menur" style="margin-left: 12px;">
                  <div class="temte">2025{{ $lang('年報告') }} - 2025{{ $lang('年') }}6{{ $lang('月') }}26{{ $lang('日') }}
                  </div>
                  <div class="imgbox">
                    <img src="@/assets/images/indexbanner0.jpg" alt="">
                  </div>
                  <div class="meleli" style="font-size: 18px;font-weight: 500;">{{ $lang('社區參與') }}</div>
                </div>
              </div>
            </div>
          </li>
          <li :class="routeName == '/people' ? 'active' : ''">
            <a @click="navigateTo('/people')"> {{ $lang('人們') }} </a>
          </li>
          <li :class="routeName == '/careers' ? 'active' : ''">
            <a @click="navigateTo('/careers')">{{ $lang('職業生涯') }}</a>
            <div class="menumask" :class="white ? 'iszhetou' : ''"></div>
            <div class="menu-point"></div>
            <div class="topmenubox">
              <div class="main">
                <div class="menul">
                  <div class="menurte" style="margin:0;margin-bottom: 10px;">{{ $lang('職業生涯') }}</div>
                  <div class="menurlink">{{ $lang('探索') }}<div class="arrow-outline outlines">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="meleli">{{ $lang('機會') }}</div>
                  <div class="meleli">{{ $lang('生長') }}</div>
                  <div class="meleli">{{ $lang('加入我們') }}</div>
                </div>
                <div class="menur" style="margin-left: 12px;">
                  <div class="temte" style="font-size: 16px;color: #000;font-weight: 600;">{{ $lang('發揮你的潛力') }}</div>
                  <div class="imgbox">
                    <img src="@/assets/images/bc-tvp-video-menu.jpg" alt="">
                  </div>
                  <div class="meleli" style="font-size: 18px;font-weight: 600;color: #001aff;">{{
                    $lang('我們的人才是我們優勢的核心。') }}</div>
                </div>
              </div>
            </div>
          </li>
          <li :class="routeName == '/news' ? 'active' : ''">
            <a @click="navigateTo('/news')">{{ $lang('訊息') }}</a>
            <div class="menumask" :class="white ? 'iszhetou' : ''"></div>
            <div class="menu-point"></div>
            <div class="topmenubox">
              <div class="main">
                <div class="menul">
                  <div class="menurte" style="margin:0;margin-bottom: 10px;">{{ $lang('訊息') }}</div>
                  <div class="menurlink">{{ $lang('探索') }}<div class="arrow-outline outlines">
                      <i class="fa-solid fa-angle-right icol"></i>
                    </div>
                  </div>
                  <div class="meleli">{{ $lang('新聞稿') }}</div>
                  <div class="meleli">{{ $lang('新聞報道') }}</div>
                </div>
                <div class="menur" style="margin-left: 12px;">
                  <div class="temte" style="font-size: 12px;color: #1c2156;font-weight: 600;">{{ $lang('新聞稿 私募') }}
                    <span style="color: #8e90ab;margin-left: 8px;"> {{ $lang('股權') }}
                      2026{{ $lang('年') }}3{{ $lang('月') }}21{{ $lang('日') }}</span>
                  </div>
                  <div class="imgbox">
                    <img src="@/assets/images/GettyImages-1942702729_0.jpg" alt="">
                  </div>
                  <div class="meleli" style="font-size: 18px;font-weight: 600;color: #001aff;">
                    {{ $lang('貝恩資本完成第十四期旗艦私募股權基金募集，規模達140億美元') }}</div>
                </div>
              </div>
            </div>
          </li>
          <li>
            <a>{{ $lang('語言選擇') }}</a>
            <div class="menumask" :class="white ? 'iszhetou' : ''"></div>
            <div class="menu-point"></div>
            <div class="topmenubox" style="width: 300px;">
              <div class="main">
                <div class="menul" style="width: 100%;border: none;">
                  <div class="menurte" style="margin:0;margin-bottom: 10px;">{{ $lang('語言選擇') }}</div>
                  <div class="meleli" @click="changeLang('en_US')">English</div>
                  <div class="meleli" @click="changeLang('zh_TW')">繁體中文</div>
                </div>
              </div>
            </div>
          </li>
          <li>
            <a :href="siteStore.chatbox" target="_blank"> {{ $lang('聯絡我們') }} </a>
          </li>
          <li :class="routeName == '/user/info' ? 'active' : ''">
            <a @click="navigateTo('/user/info')"> {{ $lang('成員中心') }} </a>
          </li>
          <li v-if="isLogin()">
            <a @click="navigateTo('/game')">{{ $lang('互動平臺') }}</a>
          </li>
          <li v-if="!isLogin()">
            <a class="logout" @click="navigateTo('/login')">Login</a>
          </li>
          <li v-else>
            <a class="logout" @click="signout">{{ $lang('登出') }}</a>
          </li>
        </ul>
        <ul class="menu" v-if="!menu">
          <li class="has-dropdown active menu-thumb">
            <a @click="navigateTo('/game')" :style="{ color: routerCrt == '/' ? '#7354ff' : '' }">{{ $lang('首頁') }}</a>
          </li>
          <li class="has-dropdown active menu-thumb">
            <a @click="navigateTo('/game/cointrading')" :style="{
              color: routerCrt == '/game/cointrading' ? '#7354ff' : ''
            }">
              {{ $lang('幣幣交易') }}
            </a>
          </li>
          <li>
            <a @click="navigateTo('/game/perpetualcontract')" :style="{
              color: routerCrt == '/game/perpetualcontract' ? '#7354ff' : ''
            }">{{ $lang('永續合約') }}</a>
          </li>
          <li>
            <a :href="siteStore.chatbox" target="_blank"> {{ $lang('聯絡我們') }} </a>
          </li>
        </ul>
        <div class="menu-btn">
          <div v-if="!isShw" @click="onPopup" class="righticon">
            <div></div>
            <div style="margin-left: 5px;width: 15px;"></div>
            <div></div>
          </div>
          <div v-else @click="closeAll" class="close"><i class="fa-solid fa-xmark"></i>
          </div>
        </div>
      </div>
    </header>
    <div v-show="isShw" class="popup-wrapper" @click.self="onClose" data-lenis-prevent>
      <div class="popup-content" :class="{
        'cont-left': isCont,
        dark:
          routerCrt == '/game/cointrading' ||
          routerCrt == '/game/perpetualcontract'
      }" @click.stop="">
        <div class="popup-flex">
          <div class="left">
            <div class="main">
              <div class="mainle">
                <h4>{{ $lang('貝恩資本') }}</h4>
                <div @click="navigateTo('/about'), closeAll" class="maintitle">{{ $lang('關於我們') }}</div>
                <div @click="navigateTo('/sustainability'), closeAll" class="maintitle">{{ $lang('永續性與影響') }}</div>
                <div @click="navigateTo('/people'), closeAll" class="maintitle">{{ $lang('人們') }}</div>
                <div @click="navigateTo('/careers'), closeAll" class="maintitle">{{ $lang('職業生涯') }}</div>
                <div @click="navigateTo('/news'), closeAll" class="maintitle">{{ $lang('訊息') }}</div>
                <div @click="changeLang('en_US')" class="maintitle">English</div>
                <div @click="changeLang('zh_TW')" class="maintitle">{{ $lang('繁體中文') }}</div>
                <div class="maintitle"><a :href="siteStore.chatbox" target="_blank"> {{ $lang('聯絡我們') }} </a></div>
                <div @click="navigateTo('/user/info'), closeAll" class="maintitle">{{ $lang('成員中心') }}</div>
                <div @click="navigateTo('/game'), closeAll" class="maintitle">{{ $lang('互動平臺') }}</div>
                <div @click="navigateTo('/login'), closeAll" class="maintitle">Login</div>

                <div @click="goLink('https://www.baincapital.com/locations')" class="maintitle">{{ $lang('地點') }}</div>
                <h4 style="margin-top: 30px;">{{ $lang('本地網站') }}</h4>
                <div @click="goLink('https://www.baincapital.co.jp/')" class="maintitle ritext">{{ $lang('日本 - 日本') }}
                </div>
              </div>
              <div class="mainri">
                <h4>{{ $lang('我們的業務') }}</h4>
                <div @click="goLink('https://www.baincapitalprivateequity.com/')">{{ $lang('私募股權') }}</div>
                <div @click="goLink('https://www.baincapitalcredit.com/')">{{ $lang('信用') }}</div>
                <div @click="goLink('https://www.baincapital.com/ventures')">{{ $lang('創投') }}</div>
                <div @click="goLink('https://www.baincapitalrealestate.com/')">{{ $lang('房地產') }}</div>
                <div @click="goLink('https://baincapitalspecialsituations.com/')">{{ $lang('特殊情況') }}</div>
                <div @click="goLink('https://www.baincapitallifesciences.com/')">{{ $lang('生命科學') }}</div>
                <div @click="goLink('https://www.baincapitaltechopportunities.com/')">{{ $lang('技術機會') }}</div>
                <div @click="goLink('https://www.baincapitaldoubleimpact.com/')">{{ $lang('雙重衝擊') }}</div>
                <div @click="goLink('https://www.baincapitalinsurance.com/')">{{ $lang('保險') }}</div>
                <div @click="goLink('https://www.baincapital.com/crypto')">{{ $lang('加密貨幣') }}</div>
              </div>
            </div>
            <div class="botpopu">
              <div class="botpopubq">
                © 2012-2026 {{ $lang('貝恩資本有限合夥公司。貝恩資本方形標誌是貝恩資本有限合夥公司的商標。版權所有。') }}</div>
              <div class="ftrtext">
                <div @click="goLink('https://www.baincapital.com/privacy-policy')">{{ $lang('隱私權政策') }}</div>
                <div @click="goLink('https://www.baincapital.com/terms-use')">{{ $lang('使用條款') }}</div>
                <div @click="goLink('https://www.baincapital.com/regulatory-disclosures')">{{ $lang('監理揭露') }}</div>
                <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning')">
                  {{ $lang('詐欺和網路安全警告') }}</div>
                <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning-chinese')">
                  {{ $lang('警告：網路詐騙及網路釣魚') }}</div>
                <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning-spanish')">
                  {{ $lang('網路安全詐欺和廣告') }}</div>
              </div>
            </div>
          </div>
          <div class="right">
            <div class="main">
              <div class="showbox">
                <div class="shou"><img src="@/assets/images/search-icon.svg" alt="">{{ $lang('搜尋') }}</div>
                <input type="text" :placeholder="$lang('你要買什麽？')">
              </div>
              <div class="botlogin">
                <h2>{{ $lang('致 投 資 者') }}</h2>
                <div class="logtext">{{ $lang('登入即可查看您的帳戶資訊。如有任何帳戶相關問題，請聯絡') }}<a :href="siteStore.chatbox"
                    target="_blank"> {{
                      siteStore.chatbox }}
                  </a>
                </div>
                <div class="loginbox" @click="navigateTo('/login')">{{ $lang('登入您的帳戶') }}
                  <img src="@/assets/images/blue-right-arrow.png" alt="">
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="popup-menus">
          <ul class="menus" v-if="menu">
            <li class="menu-thumb" :class="routeName == '/' ? 'active' : ''">
              <a @click="navigateTo('/')">
                <span>{{ $lang('首頁') }}</span>
              </a>
            </li>
            <li :class="routeName == '/responsibility' ? 'active' : ''">
              <a @click="navigateTo('/responsibility')">{{ $lang('企業責任') }}</a>
            </li>
            <li>
              <a :href="siteStore.chatbox" target="_blank"> {{ $lang('聯絡我們') }} </a>
            </li>

            <li :class="routeName == '/user/info' ? 'active' : ''">
              <a @click="navigateTo('/user/info')"> {{ $lang('成員中心') }} </a>
            </li>
            <li v-if="isLogin()" class="menu-thumb">
              <a @click="navigateTo('/game')">
                <span>{{ $lang('互動平臺') }}</span>
              </a>
            </li>
            <li v-if="!isLogin()" class="menu-thumb">
              <a @click="navigateTo('/login')">
                <span>{{ $lang('登入') }}</span>
              </a>
            </li>

          </ul>
          <ul class="menus" v-if="!menu">
            <li class="has-dropdown menu-thumb">
              <a @click="navigateTo('/game')" :style="{ color: routerCrt == '/' ? '#7354ff !important' : '' }">{{
                $lang('首頁') }}</a>
            </li>
            <li class="has-dropdown menu-thumb">
              <a @click="navigateTo('/game/cointrading')" :style="{
                color:
                  routerCrt == '/game/cointrading' ? '#7354ff !important' : ''
              }">
                {{ $lang('幣幣交易') }}
              </a>
            </li>
            <li>
              <a @click="navigateTo('/game/perpetualcontract')" :style="{
                color:
                  routerCrt == '/game/perpetualcontract'
                    ? '#7354ff !important'
                    : ''
              }">{{ $lang('永續合約') }}</a>
            </li>
            <li>
              <a :href="siteStore.chatbox" target="_blank"> {{ $lang('聯絡我們') }} </a>
            </li>
            <li v-if="!isLogin()" class="menu-thumb">
              <a @click="navigateTo('/login')">
                <span>{{ $lang('登入') }}</span>
              </a>
            </li>

          </ul>
        </div>
      </div>
      <div v-if="searchbox" class="searchmain">
        <input type="text" :placeholder="$lang('你在找什麽？')">
      </div>
    </div>

  </div>
</template>
<style scoped lang="sass">
.dark
  background-color: #14171a !important
  color: #fff !important
  .menu-thumb,a
    color: rgba(255,255,255, 0.6) !important
    transition: all 0.2s
    &:hover
      color: rgba(255,255,255, 0.9) !important
.opaque
  // background: #FFFFFF
  color: #111
  @media (max-width: 768px)
    height: 90px
    // background-color: #fff
  .topmore
    background-color: #fff
    display: flex
    color: #315d90
    padding: 0 100px
    font-weight: bold
    justify-content: space-between
    align-items: center
    height: 40px
    @media (max-width: 768px)
      display: none
    .left
      display: flex
      align-items: center
      padding: 9px 0
      font-size: 14px
      cursor: pointer
      .caret
        border-left: 6px solid transparent
        border-right: 6px solid transparent
        border-top: 10px dashed
        border-bottom: 0
        margin: 0 0 0 5px
        line-height: 1
        width: 0
        height: 0
        display: inline-block
        transform: rotate(0deg)
        transition: all .3s
      .xuanzhuan
        transform: rotate(180deg)
    .right
      display: flex
      font-size: 12px
      
      .closesstop
        background-color: #abcae9
        padding: 12px 30px !important
      .sstop
        padding: 12px
        position: relative
        cursor: pointer
        color: transparent
        transition: all .3s
        display: flex
        align-items: center
        img
          width: 9px
          height: 9px
          margin-left: 3px
        &:last-child
          color: #315d90
          &:hover
            color: #1b215a
        &:hover
          .bgbbox
            height: 100%
          .texttop
            color: #fff
        .texttop
          position: absolute
          top: 50%
          left: 50%
          transform: translate(-50%,-50%)
          color: #315d90
          pointer-events: none
          white-space: nowrap
          transition: all .3s
        .bgbbox
          position: absolute
          background-color: #0047bb
          width: 100% !important
          height: 0
          bottom: 0
          left: 0
          transition: all .3s
          
        
  .header .menu-btn
    min-width: 1rem !important
    .close
      color: #1c2156
      font-size: 25px
    .righticon
      div
        width: 20px
        background-color: #1c2156
        margin-top: 4px
        height: 2px
        &:first-child
          margin-top: 0px
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
.top
  top: -15%
.opacity
  opacity: 0
.white
  background-color: #fff
  @media (max-width: 768px)
    height: 60px
header
  position: fixed
  z-index: 6666
  color: #fff
  top: 0
  left: 0
  right: 0
  width: 100%
  font-size: 1rem
  transition: all 0.5s
  .header
    height: 90px
    display: flex
    align-items: center
    justify-content: space-between
    // width: 1200px
    margin: 0 auto
    width: 90%
    .logo
      height: 100%
      padding-top: 30px
      // max-height: 4.0625rem
      width: 358px
      flex-shrink: 0
      transition: all .5s
      @media (max-width: 768px)
        width: 180px
      img
        width: 100%
        // height: 100%
    @media (max-width: 1200px)
      width: 100%
      padding: 0 1.2rem
    ul.menu
      // list-style: none
      padding: 0
      margin: 0
      display: flex
      border-bottom: 1px solid #1c2156
      font-size: 20px
      flex: 1
      margin-left: 20px
      justify-content: flex-end
      cursor: pointer
      @media (max-width: 768px)
        border: none
      &>li
        position: relative
        margin-left: 2rem
        display: flex
        transition: all 0.3s
        color: #1c2156
        &::after
          width: 0px
          height: 4px
          content: ''
          position: absolute
          left: 50%
          transform: translateX(-50%)
          bottom: -2px
          background-color: #212355
          
        &:hover
          color: #7354ff
          .menumask
            background-color: rgba(0,0,0,0.4) !important
          .menu-point
            background-color: #fff !important
          .topmenubox
            pointer-events: auto !important
            .main
              opacity: 1 !important
          &::after
            width: 100%
            transition: all .3s 
        &>a
          height: 58px
          // line-height: 58px
          display: flex
          align-items: center
        .submenu
          position: absolute
          top: calc(100% + 1.5rem)
          left: 0
          display: grid
          opacity: 0
          visibility: hidden
          grid-template-columns: 1fr 1fr
          background: #fff
          box-shadow: 0 0 10px rgba(0, 0, 0, 0.1)
          color: #111
          padding: 1rem 1rem
          transition: all 0.5s
          li
            flex: 1 1 auto
            padding-inline: 1rem
            padding-block: 1rem
            a
              display: flex
              flex-direction: column
              align-items: center
              text-align: center
              justify-content: center
              transition: all 0.3s
              &:hover
                color: #7354ff
              img
                margin-inline: 3rem
                width: 49px
                height: 49px
              span
                margin-block-start: 8px
          .solid-right
            border-right: 1px solid #ccc
          .solid-bottom
            border-bottom: 1px solid #ccc
        @media (max-width: 1200px)
          display: none

    .menu-btn
      min-width: 4.0625rem
      display: flex
      justify-content: flex-end
      align-items: center
      gap: .5rem
      display: none
      @media (max-width: 1200px)
        display: block
      .icon
        fill:#111
        width: 24px
        height: 24px
        cursor: pointer
       
      .edit-icons
        fill: #ffffff99
        cursor: pointer
        width: 1.2rem
        height: 1.2rem
        transition: all 0.3s
        &:hover
          fill: #fff
        @media (max-width: 1200px)
          display: none
      .menu-acc
        display: flex
        align-items: center
        //@media (max-width: 1200px)
          //display: none
        .user-con
          transition: all 0.3s
          margin-inline-end: 1rem
          font-size: .8rem
          .account
            color: #7354ff
        .menu-log
          padding: .2rem .8rem
          transition: all 0.3s
          border: 1px solid #ffffff00
          border-radius: 5px
          &:hover
            color: #7354ff
            border: 1px solid #7354ff
        .menu-login
          color: #7354ff
          border: 1px solid #7354ff
          &:hover
            background: #7354ff
            color: #fff !important
        .menu-logout
          color: #7354ff
          border: 1px solid #7354ff
          @media (max-width: 1200px)
            display: none
          &:hover
            background: #7354ff
            color: #fff !important
.menumask
  position: fixed
  bottom: 0
  right: 0
  width: 100%
  height: calc( 100% - 40px )
  z-index: 11
  background-color: rgba(0,0,0,0)
  pointer-events: none
  transition: all .3s
.menu-point
  position: absolute
  width: 20px
  height: 12px
  clip-path: polygon(0% 100%, 50% 0%, 100% 100%)
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.07)
  top: calc(100% + 10px)
  left: 50%
  transform: translateX(-50%)
  background-color: rgba(0,0,0,0)
  z-index: 9999
  pointer-events: none
  transition: all .3s
.topmenubox
  position: absolute
  // right: 100px
  // top: 115px
  top: 58px
  width: 650px
  padding-top: 20px
  z-index: 12
  pointer-events: none
  
  .main
    background-color: #fff
    opacity: 0
    transition: all .3s
    border-radius: 10px
    padding: 30px
    width: 100%
    display: flex
    .menul
      width: 40%
      border-right: 1px solid #E6E6E3
      color: #9497b1
      font-weight: 500
      
      .mlti
        transition: all .3s
        margin-bottom: 5px
        &:hover
          color: #1b215a
    .meleli
      color: #1c2156
      font-size: 16px
      margin-bottom: 10px
      transition: all .3s
      &:hover
        color: #0749c4
    .menur
      margin-left: 30px
    .temte
      font-size: 12px
      color: #1C2156
    .imgbox
      width: 283px
      height: 195px
      border-radius: 5px
      overflow: hidden
      margin: 8px 0
      img
        transition: all .3s
        &:hover
          transform: scale(1.1)
    .menurt
      color: #212529
      font-size: 30px
    .menurte
      font-size: 12px
      color: #a4a6bb
      margin-top: 25px
      margin-bottom: 10px
    .menurcon
      color: #212529
      font-size: 16px
    .menurlink
      font-size: 17px
      color: #001aff
      display: flex
      font-weight: 500
      margin-bottom: 7px
      &:hover
        color: #1b215a
        .icol
          color: #fff !important
        .arrow-outline
          background-color:  #1b215a
          border: 2px solid #1b215a
      .arrow-outline
        margin-left: 7px
        transition: all .3s
        width: 16px
        height: 16px
        margin: 4px 0 0 8px
        border: 2px solid #001aff
        border-radius: 50%
        display: flex
        align-items: center
        justify-content: center
        fill: #001aff
        font-size: 11px
        padding-left: 1px
      .outlines
        color: #fff !important
        background-color: #001aff
        margin-bottom: 25px
.iszhetou
  height: calc( 100% - 98px )
.searchmain
  position: fixed
  top: 0
  right: 0
  width: 100%
  height: 100%
  z-index: 55
  background-color: #0077ff
  padding-left: 200px
  display: flex
  align-items: center
  font-size: 60px
  color: #fff
  font-weight: 300
  input
    background-color: transparent
    &::placeholder
      color: #fff
.popup-wrapper
  position: fixed
  top: 0
  right: 0
  width: 100%
  height: 100%
  background: rgba(0, 0, 0, 0.2)
  z-index: 55
  display: flex
  justify-content: center
  align-items: center
  // @media (min-width: 1200px)
  //   display: none
  .popup-content
    overflow-y: scroll
    overscroll-behavior: contain
    position: absolute
    top: 0
    bottom: 0
    background-color: #fff
    width: 100%
    transform: translateX(100%)
    transition: all 0.3s
    .popup-title
      display: flex
      justify-content: space-between
      align-items: center
      padding-block-start: 1rem
      &>span
        margin-left: 15px
      img
        width: 1.5rem
        height: 1.5rem
        margin-inline: 1.2rem
        cursor: pointer
    .popup-flex
      display: flex
      height: auto
      @media (max-width: 768px)
        height: auto
        display: block
      .left
        width: 65%
        background-color: #1b2c46
        height: auto
        padding-bottom: 50px
        @media (max-width: 768px)
          width: 100%
          padding-bottom: 1px
        .main
          display: flex
          color: #fff
          @media (max-width: 768px)
            display: block
            padding-bottom: 30px
          h4
            color: #5d8bbf
            font-size: 18px
            font-weight: 600
          .mainle
            font-size: 60px
            padding-left: 100px
            padding-top: 170px
            width: 50%
            @media (max-width: 768px)
              width: 100%
              font-size: 25px
              padding-top: 80px
              padding-left: 25px
            .maintitle
              // margin-top: 18px
              line-height: 80px
              transition: all .3s
              cursor: pointer
              @media (max-width: 768px)
                line-height: 40px
              &:hover
                color: #1ca6df
            .ritext
              font-size: 30px
              margin-top: -10px
              @media (max-width: 768px)
                font-size: 25px
                margin-top: 10px
          .mainri
            font-size: 30px
            padding-left: 100px
            padding-top: 170px
            width: 50%
            @media (max-width: 768px)
              padding-top: 30px
              padding-left: 25px
              font-size: 25px
            div
              transition: all .3s
              cursor: pointer
              &:hover
                color: #1ca6df
        .botpopu
          margin-top: 40px
          margin-left: 100px
          color: #abcae9
          @media (max-width: 768px)
            // display: none
            margin: 25px
            border-top: 1px solid #abcae9
            padding-top: 50px
            font-size: 15px
            margin-top: 450px
          .botpopubq
            padding-right: 30px
          .ftrtext
            display: flex
            margin-top: 8px
            @media (max-width: 768px)
              flex-wrap: wrap
            div
              margin-right: 30px
              border-bottom: 1px solid #abcae9
              transition: all .3s
              cursor: pointer
              @media (max-width: 768px)
                margin-bottom: 8px
              &:hover
                border-bottom: 1px solid #1b2c46 !important
                color: #1b8bdf
      .right
        width: 35%
        background-color: #5d8bbf
        height: auto
        @media (max-width: 768px)
          // display: none
          width: 100%
          height: auto
          margin-top: -720px
        .main
          padding-left: 50px
          padding-top: 170px
          @media (max-width: 768px)
            padding: 0
            background-color: #fff
          .showbox
            padding: 25px
          input
            background-color: transparent
            width: 100%
            height: 60px
            font-size: 60px
            margin-top: 15px
            font-weight: 300
            caret-color: white
            &::placeholder
              color: #fff
            @media (max-width: 768px)
              font-size: 22px
              &::placeholder
                color: #1c2156 !important
          .shou
            display: flex
            align-items: center
            color: #212355
            font-weight: 600
            img
              width: 24px
              margin-right: 12px
              height: 24px
          .botlogin
            border-top: 1px solid #1c2156
            margin-top: 350px
            color: #fff
            width: 80%
            font-size: 20px
            @media (max-width: 768px)
              background-color: #0076a9
              width: 100%
              padding: 25px
              font-size: 16px
              margin-top: 0px
            a
              text-decoration: underline
            .logtext
              @media (max-width: 768px)
                width: 80%
            h2
              margin: 20px 0
              font-weight: 600
              color: #212355
              font-size: 18px
              @media (max-width: 768px)
                font-size: 16px
            .loginbox
              margin-top: 20px
              width: 100%
              text-align: left
              background: #bbddfc
              font-size: 20px
              color: #1c2156
              box-shadow: none
              border: none
              padding: 11px 40px 14px 20px
              border-radius: 10px
              display: flex
              justify-content: space-between
              align-items: center
              font-weight: 500
              cursor: pointer
              @media (max-width: 768px)
                font-size: 16px
    .popup-menus
      // @media (max-width: 768px)
      display: none
      .menus
        // list-style: none
        padding: 20px 0 0
        border-bottom: 1px solid #1c2156
        // margin-block-end: 1.5625rem
        &>li
          margin-inline: 15px
          cursor: pointer
          // border-block-end: 1px solid #ccc
          color: #11111199
          min-height: 40px
          overflow: hidden
          transition: all 0.5s
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
              transition: all 0.2s
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
          transition: all 0.2s
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
.menu-pc
  li
    &:hover
      color: #212355 !important
.englishmenu
  li
    font-size: 18px
    margin-left: 16px !important
.blueline
  border-bottom: 1px solid #1c2156 !important
  @media (max-width: 768px)
    border: none !important
.noline
  border: none !important
.active
  position: relative
  color: #212355 !important
  &::before
    content: ''
    position: absolute
    left: 50%
    width: 100%
    transform: translateX(-50%)
    height: 4px
    background: #212355
    bottom: -2px
    @media (max-width: 768px)
      display: none

</style>

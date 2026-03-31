<script lang="ts" setup>
import Lenis from "@studio-freight/lenis"
const { t } = useI18n()
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
const goLink = (link) => {
    window.open(link)
}
</script>

<template>
    <div class="cont">
        <headerTop :top="isTop" :white="true" :opacity="isTop"></headerTop>
        <div class="bodybox">
            <div class="container">
                <h1 class="stitle">隱私權政策</h1>
                <div class="content">
                    <div class="right">
                        <article class="article-container">
                            <div class="article-body">
                                <section class="content-text">
                                    <p>最後更新：2025年11月</p>
                                </section>
                                <section class="content-text">
                                    <p>貝恩資本有限合夥公司（Bain Capital, LP）位於美國麻薩諸塞州波士頓克拉倫登街200號（200 Clarendon St, Boston, MA
                                        02116），是全球領先的私募投資公司之一。在貝恩資本有限合夥公司（及其子公司和關聯公司，統稱「貝恩資本」），我們非常重視您的隱私。本隱私權政策（「政策」）描述並規範我們作為資料控制者，如何使用和揭露透過貝恩資本網站
                                        （ <a href="https://www.baincapital.com/">https://www.baincapital.com/</a>
                                        ，簡稱「網站」）收集的個人信息，以及我們在管理業務過程中收集的個人信息，包括來自聯繫我們的人員、供應商、潛在投資者和潛在員工的資訊。</p>
                                </section>
                                <section class="content-text">
                                    <p>對於位於歐洲經濟區（「EEA」）和英國（「UK」）以外地區的網站用戶，您使用本網站即表示接受本政策的條款。如果您位於歐洲經濟區或英國，本政策僅供參考。本政策中使用的未定義大寫術語應具有我們在《
                                        <a href="https://www.baincapital.com/terms-use">使用條款》</a>中規定的定義。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>如果您是貝恩資本的投資者或投資者代表，請參閱我們投資者入口網站上的《投資者隱私權聲明》，以了解我們如何收集、使用和分享投資者資訊。此外，我們投資者入口網站提供者的政策也適用於我們投資者入口網站所收集的資訊。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">1. 我們收集的個人資訊</p>
                                </section>
                                <section class="content-text">
                                    <p>a. 您直接向我們提供的個人信息</p>
                                </section>
                                <section class="content-text">
                                    <p>目前，我們不允許使用者透過本網站直接向我們提供個人資訊。但是，您可以為了存取某些服務、向我們提供服務或向我們索取資訊而直接向我們提供個人資訊。這些資訊可能包括您的姓名、聯絡資訊、履歷資訊、付款資訊或其他與您相關的資訊。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>除非我們根據美國外國資產管制辦公室（OFAC）及類似法律法規的規定需要對個人進行審查，否則您沒有法定義務或合約義務向我們或我們的供應商提供您的個人資訊。但是，如果您不向我們提供您的訊息，我們可能無法向您提供某些資訊或服務。例如，如果沒有某些資訊，我們將無法審核您的求職申請；同樣，如果沒有某些資訊，我們將無法與潛在投資者簽訂合約。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>我們可能會收集某些資料保護法律認定為「敏感」的個人訊息，例如您登入我們投資者入口網站時的帳戶登入資訊。在這種情況下，我們只會將此類資訊用於合法用途，並遵守適用的資料保護法律，例如為您提供您所要求的服務，以及打擊惡意、欺騙性、欺詐性或非法行為。我們不會使用此類資訊來推斷您的個人特徵。在適用法律要求的情況下，我們會在處理此類資訊之前徵得您的同意。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>b. 我們從第三方收集的個人信息</p>
                                </section>
                                <section class="content-text">
                                    <p>我們也可能從第三方收集個人信息，例如從招聘公司收到的簡歷、從背景調查機構收到的背景信息、我們在社交媒體上看到的信息，或從公開的受貿易限制人員名單中獲取的信息。我們也會從業務合作夥伴和供應商收集信息，以支持我們提供投資服務。我們從這些第三方收集的資料通常以匯總形式呈現，無法識別個人身份，但有時也可能包含個人資訊。例如，我們可能會從市場調查提供者和匯總公開資訊的供應商收集資訊。我們從這些來源取得資訊的範圍取決於第三方的特定規定。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>c. 被動或自動收集的個人訊息</p>
                                </section>
                                <section class="content-text">
                                    <p><em>i.</em> <em>設備/使用資訊</em></p>
                                </section>
                                <section class="content-text">
                                    <p>我們可能會自動收集您用於存取本網站的電腦或裝置（包括行動裝置或平板電腦）的某些信息，這些資訊可用於識別您的身分。如下文所述，我們可能會收集和分析以下資訊：(a)
                                        IP 位址、位置資訊、唯一裝置識別碼、IMEI 和 TCP/IP
                                        位址，以及關於您的電腦或裝置的其他信息，例如瀏覽器類型、瀏覽器語言、作業系統、行動裝置業者資訊以及您造訪本網站所在的州或國家/地區；(b)
                                        與您與本網站互動方式相關的資訊，例如網頁及與本網站互動URL、平台類型、點擊次數、網域名稱、登陸頁面、瀏覽的頁面和內容及其順序、關於本網站使用情況的統計資訊、在特定頁面上花費的時間、您使用本網站的日期和時間、您使用本網站的頻率、錯誤日誌以及其他類似資訊。如下文所述，我們可能會使用第三方分析提供者和技術（包括
                                        Cookie 和類似工具）來協助收集這些資訊。</p>
                                </section>
                                <section class="content-text">
                                    <p><em>二、</em> <em>Cookie 和其他電子技術</em></p>
                                </section>
                                <section class="content-text">
                                    <p>我們也可能透過網路伺服器日誌、Cookie 和/或追蹤像素收集您使用本網站的資料。網站伺服器日誌是儲存網站活動的檔案。 Cookie
                                        是您造訪網站時放置在您電腦上的小型文字文件，它使我們能夠：(a) 識別您的電腦；(b) 儲存您的偏好和設定；(c) 了解您造訪過的網頁；(d)
                                        透過提供符合您推測興趣的內容和廣告來提升您的使用者體驗；(e) 執行搜尋和分析；以及 (f)
                                        協助安全和管理功能。我們也可能在電子郵件、新聞通訊和其他電子通訊中包含追蹤像素和網路信標，以確定郵件是否已被打開，並用於其他分析、個人化和推廣目的。隨著我們採用更多技術，我們可能還會透過其他方式收集更多資訊。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>請注意，您可以變更設置，以便在設定或更新 Cookie 時收到通知，或完全封鎖 Cookie。更多信息，請參閱瀏覽器的「說明」部分（例如， <a
                                            href="http://windows.microsoft.com/en-US/windows-vista/Block-or-allow-cookies">Internet
                                            Explorer</a>、 <a
                                            href="https://support.google.com/chrome/answer/95647?hl=zh-Hant">Google
                                            Chrome</a>、 <a href="http://kb.mozillazine.org/Cookies#Firefox">Mozilla
                                            Firefox</a> 或 <a href="http://support.apple.com/kb/PH5042">Apple Safari
                                            ）。您也可以使用 Adob​​e</a><a
                                            href="http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html">網站</a>提供的
                                        Flash 管理工具來管理 Flash 技術的使用，包括 Cookie 和本機儲存物件 。請注意，封鎖任何或所有 Cookie
                                        可能會導致您無法存取本網站的某些功能或服務。</p>
                                </section>
                                <section class="content-text">
                                    <p>d. 線上分析</p>
                                </section>
                                <section class="content-text">
                                    <p>我們可能會在網站上使用第三方網路分析服務（例如 Google Analytics）來收集和分析上述信息，並用於審計、研究或報告。上文「Cookie
                                        和其他電子技術」部分所述的各種分析技術收集的資訊（包括您的 IP
                                        位址）將揭露給這些服務提供者或由其直接收集。這些服務提供者會使用這些資訊來評估您對網站的使用情況，包括記錄您造訪本網站的來源網站、分析使用趨勢、協助預防詐欺以及為您提供某些功能。若要阻止
                                        Google Analytics 將您的資訊用於分析，您可以點擊 <a
                                            href="http://tools.google.com/dlpage/gaoptout">此處</a> 安裝 Google Analytics
                                        選擇退出瀏覽器插件。</p>
                                </section>
                                <section class="content-text">
                                    <p>e. 禁止追蹤訊號</p>
                                </section>
                                <section class="content-text">
                                    <p>「請勿追蹤」（Do Not Track，簡稱「DNT」）是使用者可以在某些網頁瀏覽器中設定的隱私偏好。我們目前無法識別或回應瀏覽器發起的 DNT
                                        訊號。第三方（例如我們的分析服務提供者）可能會收集與您在我們網站上相關的資料或資訊。我們無法控制第三方對 DNT 訊號的反應。第三方對 DNT
                                        訊號的回應受其各自隱私權政策的約束。您可以點擊 <a href="http://allaboutdnt.com/">此處</a>
                                        了解更多關於「請勿追蹤」的資訊。</p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">2. 我們如何使用您的個人資訊</p>
                                </section>
                                <section class="content-text">
                                    <p>我們可能會將收集到的關於您的個人資訊用於以下用途：</p>
                                    <ul class="incremental">
                                        <li>用於您向我們或供應商提供該資訊時所指定的用途；</li>
                                        <li>提供透過本網站提供的功能和服務；</li>
                                        <li>為了開展我們的業務，並提供和改進我們的投資服務，包括評估潛在投資和管理現有投資；</li>
                                        <li>為了回應您的要求或向您發送其他訊息；</li>
                                        <li>遵守法律和監管義務；</li>
                                        <li>進行調查並分析市場趨勢和興趣；</li>
                                        <li>處理並回覆您的諮詢或徵求您的回饋意見；</li>
                                        <li>用於內部研究和報告；</li>
                                        <li>為了改進網站的內容和功能；</li>
                                        <li>用於招聘目的；</li>
                                        <li>為了執行您使用本網站的法律條款；以及</li>
                                        <li>負責網站的管理和故障排除。</li>
                                    </ul>
                                </section>
                                <section class="content-text">
                                    <p>請注意，我們可能會將我們從您收集的以及關於您的個人資訊（包括自動收集的資訊）與我們從我們的關聯公司、供應商和/或其他非關聯第三方獲得的關於您的資訊結合起來，並根據本政策使用此類結合資訊。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>我們可能會對收集到的個人資訊進行匯總和/或匿名化處理。我們可能會將匿名化和/或匯總後的資料用於任何目的，包括但不限於研究和行銷目的，也可能與任何第三方共享此類資料。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">3. 我們何時透露您的個人資訊</p>
                                </section>
                                <section class="content-text">
                                    <p>在下列情況下，我們可能會向任何非關聯第三方揭露和/或分享您的個人資訊：</p>
                                    <ul class="incremental">
                                        <li>同意。經您同意，我們可能會將您的資訊揭露給任何第三方。</li>
                                        <li>服務提供者。我們可能會向代表我們提供服務的特定第三方提供或共享您的信息，包括但不限於通訊、市場調查、客戶支援、資料儲存、分析和處理以及法律服務。
                                        </li>
                                        <li>保護貝恩資本及其他方。您承認並同意，在法律要求或貝恩資本出於善意認為本政策允許或出於以下任何原因合理必要或適當的情況下，貝恩資本可以訪問、保存和披露您提交或提供給本網站的信息：(a)
                                            根據適用法律法規的要求，包括與了解客戶要求、稅務、反洗錢、反欺詐、反恐怖主義融資和製裁令為了執行本政策、我們的使用條款或與您簽訂的其他合同，包括調查潛在的違規行為；(c)
                                            為了回應任何內容侵犯第三方權利的指控；和/或 (d)
                                            為了保護貝恩資本、其諮詢業務部門、代理人、關聯公司、投資者和公眾的權利、財產或人身安全，包括確立或捍衛貝恩資本的合法權利。這包括與其他公司和組織交換訊息，以防止詐欺、防止垃圾郵件/惡意軟體以及類似目的。
                                        </li>
                                        <li>業務轉讓。隨著我們業務的不斷發展，我們可能會收購、合併或與其他公司建立合作關係。在這些交易中（包括為進行此類交易做準備，例如盡職調查），個人資訊可能作為披露或轉讓的資產之一。如果貝恩資本的任何資產出售或轉讓給第三方，您的資訊可能成為轉讓的業務資產之一。
                                        </li>
                                    </ul>
                                </section>
                                <section class="content-text">
                                    <p class="weight">4. 處理個人資訊的法律依據</p>
                                </section>
                                <section class="content-text">
                                    <p>某些司法管轄區的法律要求公司告知您其使用或揭露您個人資訊的法律依據。在這些法律適用的範圍內，我們處理您個人資訊的法律依據如下：</p>
                                    <ul class="incremental">
                                        <li>合法權益。在許多情況下，我們處理個人資訊是基於其符合我們在商業活動中的合法權益，例如以下情況，且不會損害相關個人的利益或基本權利和自由：
                                            <ul class="incremental">
                                                <li>提供我們的投資服務</li>
                                                <li>提供和維護我們的網站</li>
                                                <li>分析並改進我們的業務和網站</li>
                                                <li>溝通，包括回覆您關於我們服務的諮詢</li>
                                                <li>滿足資訊安全需求並保護我們的投資者、貝恩資本、貝恩資本基金及其他機構。</li>
                                                <li>調查、辯護及其他法律問題處理</li>
                                            </ul>
                                        </li>
                                        <li>法律合規。我們需要以特定方式使用和揭露個人資訊，以履行我們的法律義務。</li>
                                        <li>履行我們對您的合約承諾。我們處理個人資訊的絕大部分是為了履行我們對投資者的合約義務，或應投資者要求採取措施，以期與他們簽訂合約。</li>
                                        <li>同意。如果我們從已獲得您同意的第三方收集個人信息，我們可能會基於您的同意處理您的個人資訊。</li>
                                    </ul>
                                </section>
                                <section class="content-text">
                                    <p class="weight">5. 您的選擇、資料主體權利和申訴</p>
                                </section>
                                <section class="content-text">
                                    <p>根據當地法律，您可能享有與您的個人資訊相關的某些權利。這些權利可能包括：(1) 存取、更正或要求刪除您的個人資訊；(2) 要求限制處理您的個人資訊；(3)
                                        反對處理您的個人資訊；(4) 要求將您的個人資訊與某些其他組織共用；以及/或 (5)
                                        行使與您的個人資訊相關的其他權利。如果您已同意處理您的個人資訊，您可以隨時撤回該同意。</p>
                                </section>
                                <section class="content-text">
                                    <p>如需行使上述一項或多項權利，請依照下文「<a href="#contact">聯絡資訊、申訴和有關本政策的問題</a>」（第 13 節）中的說明與我們聯絡。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>此處所述的許多權利均受適用法律的限制和例外情況約束（例如，反對處理個人資訊和撤回同意通常不具有追溯效力）。另請注意，如果我們從第三方收集了您的個人信息，您可能還需要聯絡該第三方才能向其行使您的權利。如果您希望限制接收我們發送的電子郵件，您可以按照下文第
                                        13 條所述的方式與我們聯絡。</p>
                                </section>
                                <section class="content-text">
                                    <p>如果您認為我們違反了資料保護法，或者您想就我們處理您個人資訊的方式提出投訴，請透過下文第 13
                                        節的聯絡資訊與我們聯絡。我們將審查您的投訴，並根據當地法律的要求採取措施予以回應。</p>
                                </section>
                                <section class="content-text">
                                    <p>雖然我們強烈建議您先直接向我們提出有關您個人資訊的任何問題或疑慮，但您可能有權向相關監管機構提出投訴。</p>
                                </section>
                                <section class="content-text">
                                    <p>根據《加州消費者隱私法》（經《加州隱私權法》修訂，統稱「CCPA」），加州居民可以就其個人資訊提出某些請求。具體而言，如果您是加州居民，您可以要求我們：</p>
                                    <ul class="incremental">
                                        <li>向您提供以下資訊：我們收集或揭露的關於您的個人資訊類別；此類資訊的來源類別；收集或揭露您的個人資訊的商業或業務目的；以及我們與之分享個人資訊的第三方類別。此類資訊也已在本政策中列明；
                                        </li>
                                        <li>提供您查閱和/或取得我們持有的關於您的某些資訊的副本；和/或</li>
                                        <li>刪除或更正我們掌握的關於您的某些資訊。</li>
                                    </ul>
                                </section>
                                <section class="content-text">
                                    <p>加州居民也可以指定授權代理人代表其提出請求。在回覆您或您指定代理人的請求之前，我們將採取合理措施核實您的身分。 《加州消費者隱私法案》(CCPA)
                                        也賦予您行使權利時不受歧視的權利（具體歧視規定以適用法律為準）。請注意，根據加州法律，某些資訊可能不受此類請求的約束。</p>
                                </section>
                                <section class="content-text">
                                    <p>如果您是加州居民，並且希望行使 CCPA 下的任何權利，請透過<a
                                            href="mailto:privacy@baincapital.com">privacy@baincapital.com</a>與我們聯繫。</p>
                                </section>
                                <section class="content-text">
                                    <p><span class="weight">出售和分享個人資訊。</span> 《加州消費者隱私法案》(CCPA)
                                        對出於跨情境行為廣告目的「出售」和「分享」個人資訊的企業規定了某些義務。根據 CCPA
                                        中「出售」和「共享」的定義以及現行指南，我們不從事此類活動，並且在過去十二個月內也沒有從事過此類活動，包括針對 16
                                        歲以下未成年人的活動。請注意，我們會根據「我們 <a
                                            href="https://www.baincapital.com/privacy-policy#when-we-disclose-your-information">何時揭露您的資訊</a>」部分所述，與我們的服務提供者和某些其他實體分享某些個人資訊。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>加州「陽光法案」允許加州居民每年免費索取並獲取信息，以了解上一日曆年度中哪些個人信息被披露給第三方用於直接營銷目的。未經您的同意，我們不會將您的個人資訊分發給外部機構用於其直接行銷。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">6. 致加州居民的通知</p>
                                </section>
                                <section class="content-text">
                                    <p>如果您是加州居民，根據加州法律，我們需要向您提供一些關於我們如何收集、使用和分享您的「個人資訊」（定義見《加州消費者隱私法案》(CCPA)）的補充資訊。本政策的「我們收集的個人資訊」、「
                                        <a
                                            href="https://www.baincapital.com/privacy-policy#how-we-use-your-information">我們如何使用您的個人資訊」</a>和「
                                        我們何時披露您的個人資訊」部分描述了<a
                                            href="https://www.baincapital.com/privacy-policy#information-we-collect">我們收集的資訊類別、收集此類資訊的商業目的、此類資訊的來源和用途以及</a><a
                                            href="https://www.baincapital.com/privacy-policy#when-we-disclose-your-information">我們與之共享</a>
                                        此類資訊的實體。以下是CCPA要求的其他資訊。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p><span class="weight">我們收集、使用和揭露的個人資訊類別。</span>
                                        本政策詳細討論了我們從使用者收集和關於使用者的資訊類型，以及我們如何使用和分享這些資訊。更多詳情請參閱「 <a
                                            href="https://www.baincapital.com/privacy-policy#information-we-collect">我們收集的個人資訊」</a>
                                        部分。以下是我們根據《加州消費者隱私法案》(CCPA) 收集的個人資訊類別和類型，如本政策所述，我們可能會出於業務目的使用和揭露這些資訊：</p>
                                </section>
                                <section class="content-text">
                                    <p>識別碼（例如姓名、位址、電子郵件地址、IP
                                        位址、社會安全號碼、護照號碼或其他類似識別碼）；根據某些法律被視為受保護分類的特徵（例如國籍和婚姻狀況）；商業資訊（例如交易資料）；財務資料（例如資產、收入和淨值）；職業或就業資訊（例如您的職位和工作地點）；設備或裝置資料（例如網際網路）；地址的一般地理位置資料；以及其他可以識別您或可以合理地與您關聯的資訊。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p><span class="weight">我們如何使用這些類別的個人資訊。</span>
                                        我們會根據本政策中討論的各種商業目的，使用我們收集的關於您的各類個人資訊。請參閱「 <a
                                            href="https://www.baincapital.com/privacy-policy#how-we-use-your-information">我們如何使用您的個人資訊」</a>
                                        以了解更多詳情。</p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">7. 個人資訊的轉移</p>
                                </section>
                                <section class="content-text">
                                    <p>我們的核心電腦系統目前託管於美國，您的個人資訊將在美國處理。美國的隱私權保護水準可能不如您所在司法管轄區的隱私權保護法律。貝恩資本是一家全球性機構。根據您在貝恩資本的聯絡人或我們收集您個人資訊的具體情況，您的個人資訊也可能在位於美國、加拿大、歐洲、中東和非洲地區以及亞太地區的資料中心進行處理和儲存。在這種情況下，我們將在適用資料保護法律要求的範圍內，採取一項或多項保障措施，包括相關機構批准或認可的標準合約條款，或確保相關服務提供者在被認為能夠為您的資料提供充分保護的國家/地區接收您的個人資訊。如需了解更多關於我們如何傳輸您的個人資訊的信息，包括如何取得相關保障措施的副本，請按以下方式與我們聯絡。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">8. 兒童隱私</p>
                                </section>
                                <section class="content-text">
                                    <p>本網站面向一般受眾，並非針對 16 歲以下兒童。如果我們發現未經有效家長同意而收集了 16 歲以下兒童的個人信息，我們將盡快採取合理措施將其刪除。</p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">9. 安全性</p>
                                </section>
                                <section class="content-text">
                                    <p>我們已實施行政、技術和實體安全措施，旨在防止您的個人資訊遺失、被濫用和/或被篡改。這些安全措施會根據我們收集和儲存資訊的敏感程度而有所不同。然而，儘管貝恩資本已採取這些安全措施來保護您的個人信息，但沒有任何措施能夠保證絕對安全或防止未經授權的活動。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">10. 個人資訊保留</p>
                                </section>
                                <section class="content-text">
                                    <p>我們將僅在為實現本政策所述目的所需的時間內，或在法律要求或允許的範圍內保留您的個人資訊。在決定保留您個人資訊的時間長短時，我們會考慮我們的法律和監管義務、個人資訊的數量、性質和敏感性、未經授權使用或揭露您的個人資訊可能造成的潛在風險、我們處理您個人資訊的目的（如上所述），以及我們是否可以透過其他方式實現這些目的。我們也可能根據可提起訴訟的國家/地區的訴訟時效，保留您的個人資訊以調查、抗辯或以其他方式處理潛在的法律索賠。在為備份和業務連續性目的而製作的副本中，個人資訊可能會保留更長時間。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">11. 第三方連結和服務</p>
                                </section>
                                <section class="content-text">
                                    <p>本網站可能包含第三方網站、應用程式和其他服務的連結或“框架”，包括上文所述的投資者網站。請注意，我們不對這些其他網站和服務的隱私保護措施負責。我們建議使用者在離開本網站時注意查看，並閱讀每個收集其資訊的網站的隱私權聲明。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p class="weight">12. 本政策的變更</p>
                                </section>
                                <section class="content-text">
                                    <p>我們將持續評估本政策，並可能據此進行相應修改。任何修改都將在此處發布，請您定期查看此頁面以獲取更新。如果我們對本政策做出重大修改，我們將根據法律要求更新此通知。
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p id="contact" class="weight">13. 聯絡方式、投訴和關於本政策的問題</p>
                                </section>
                                <section class="content-text">
                                    <p>如果您對本政策有任何疑問，或者您想行使與您的個人資訊相關的權利，包括對我們處理您個人資訊的方式提出投訴，請使用以下詳細資訊與我們聯繫，並提供您的姓名、電子郵件地址和/或電話號碼，並清楚描述您的問題、請求或投訴：
                                    </p>
                                </section>
                                <section class="content-text">
                                    <p>貝恩資本法律與合規</p>
                                    <p>麻薩諸塞州波士頓克拉倫登街200號，郵編：02116</p>
                                    <p><a href="mailto:privacy@baincapital.com">privacy@baincapital.com</a></p>
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
                            © 2012-2026 貝恩資本有限合夥公司。貝恩資本方形標誌是貝恩資本有限合夥公司的商標。版權所有。</div>
                        <div class="ftrtext">
                            <div @click="goLink('https://www.baincapital.com/privacy-policy')">隱私權政策</div>
                            <div @click="goLink('https://www.baincapital.com/terms-use')">使用條款</div>
                            <div @click="goLink('https://www.baincapital.com/regulatory-disclosures')">監理揭露</div>
                            <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning')">
                                詐欺和網路安全警告</div>
                            <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning-chinese')">
                                警告：網路詐騙及網路釣魚</div>
                            <div @click="goLink('https://www.baincapital.com/fraud-and-cybersecurity-warning-spanish')">
                                網路安全詐欺和廣告</div>
                        </div>
                    </div>
                    <div class="ftricon">
                        <div>
                            <i class="fa-brands fa-linkedin-in"></i>
                        </div>
                        <div><i class="fa-brands fa-twitter"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>

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
    width: 100%

.article-body
  .alti
    font-size: 18px
    color: #4e8dc4
    margin-top: 40px
    margin-bottom: 20px

  .content-text
    margin-bottom: 25px
    color: #1c2156
    @media (max-width: 768px)
        font-size: 16px
    .weight
        font-weight: 700
    p
      margin-bottom: 20px
      line-height: 30px
      text-align: justify // 兩端對齊
      @media (max-width: 768px)
        font-size: 16px
        line-height: 22px

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
        padding-top: 80px
        padding-bottom: 30px
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
            margin-top: 20px
        .left
            color: #8285a5
            width: 35%
            img
                border-radius: 5px
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
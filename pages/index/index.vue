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
        <div :class="bannerIndex == 0 ? 'banneractive' : ''" class="item bgimg1">
          <h2>獨具一格</h2>
          <p>
            作為率先在中國開展風險投資業務的投資機構，博裕
            投資
            已發展成為一家紮根中國市場、具備全球化視野的私募股權投資機構。
          </p>
        </div>
        <div :class="bannerIndex == 1 ? 'banneractive' : ''" class="item bgimg2">
          <h2>深度互信</h2>
          <p>
            博裕
            投資與包括主權基金/國家級出資平臺、養老基金、專業金融機構、產業資本以及家族辦公室等合作夥伴保持長期穩定的合作關係。
          </p>
        </div>
        <div :class="bannerIndex == 2 ? 'banneractive' : ''" class="item bgimg3">
          <h2>卓越業績</h2>
          <p>
            博裕投資已扶植逾600
            家企業透過在中國大陸、中國香港、美國、歐洲資本市場IPO或併購
            成功形式實現退出，支持了中國近一半的獨角獸企業。
          </p>
        </div>
        <div class="drop">
          <div :class="bannerIndex == 0 ? 'dropactive' : ''" class="dropitem" @click="bannerIndex = 0"></div>
          <div :class="bannerIndex == 1 ? 'dropactive' : ''" class="dropitem" @click="bannerIndex = 1"></div>
          <div :class="bannerIndex == 2 ? 'dropactive' : ''" class="dropitem" @click="bannerIndex = 2"></div>
        </div>
      </section>
      <section class="section2">
        <h2>我們的使命</h2>
        <div class="content">
          <div class="smitem">
            <img src="@/assets/images/indexb/icon-yj.svg" alt="" />
            <div>
              <h3>預見</h3>
              <p>正在發生的巨大變化</p>
            </div>
          </div>
          <div class="smitem">
            <img src="@/assets/images/indexb/icon-pb.svg" alt="" />
            <div>
              <h3>陪伴</h3>
              <p>有夢想有格局的未來開拓者</p>
            </div>
          </div>
          <div class="smitem">
            <img src="@/assets/images/indexb/icon-td.svg" alt="" />
            <div>
              <h3>推動</h3>
              <p>創造社會價值</p>
            </div>
          </div>
        </div>
      </section>
      <section class="section2">
        <h2>機構簡介</h2>
        <p style="color: #666; line-height: 180%">
          博裕投資創立於2011年，是一家深耕中國市場以及佈局全球的另一類資產管理公司。本公司建構了涵蓋私募股權投資、上市公司策略配置、物流樞紐與資料中心投資、創業投資、新能源產業平台的信心投資矩陣。博裕深度聚焦科技創新、消費零售醫療健康三大重點領域。依託一體化、和諧連結的投資管理平台，長期致力於為投資人創造卓越的價值與回報。
        </p>
      </section>
      <section class="section2">
        <h2>發展歷程</h2>
        <p style="color: #666; line-height: 180%">
          成立於2011年，始於私募股權投資，並於2016年拓展業務至二級市場投資領域，並於2020年啟動不動產與新基建投資及創投。如今，博裕已發展成為一個全面且良好的投資平台。
        </p>
        <div class="list1 list2">
          <div class="li-ite1">
            <div class="v-head">
              <h3>成立私募股權投資</h3>
            </div>
            <div class="v-body">
              <ul>
                <li>
                  <h4>2011</h4>
                  <p>
                    美元PE一期基金
                  </p>
                </li>
                <li>
                  <h4>2013</h4>
                  <p>
                    人民幣PE一期基金
                  </p>
                </li>
                <li>
                  <h4>2014</h4>
                  <p>
                    美元PE二期基金
                  </p>
                </li>
                <li>
                  <h4>2015</h4>
                  <p>
                    人民幣PE二期基金
                  </p>
                </li>
              </ul>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>成立二級市場投資</h3>
            </div>
            <div class="v-body">
              <ul>
                <li>
                  <h4>2016</h4>
                  <p>
                    二級市場基金
                  </p>
                </li>
                <li>
                  <h4>2017</h4>
                  <p>
                    美元PE三期基金
                  </p>
                  <p>
                    人民幣PE三期基金
                  </p>
                  <p>
                    與萬科共同發起設立物流地產基金
                  </p>
                </li>
                <li>
                  <h4>2019</h4>
                  <p>
                    美元PE四期基金
                  </p>
                </li>
              </ul>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>不動產與新基建</h3>
            </div>
            <div class="v-body">
              <ul>
                <li>
                  <h4>2020</h4>
                  <p>
                    美元VC一期資金
                  </p>
                </li>
                <li>
                  <h4>2021</h4>
                  <p>
                    美元PE五期基金
                  </p>
                  <p>美元成長一期基金
                  </p>
                  <p>人民幣PE四期基金
                  </p>
                  <p>人民幣VC一期基金
                  </p>
                </li>
                <li>
                  <h4>2022</h4>
                  <p>
                    美元VC二期資金
                  </p>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </section>
      <section class="section3">
        <h2>業務範圍</h2>
        <div class="content">
          <div class="left">
            <img src="@/assets/images/indexb/business.jpg" alt="" />
            <div class="list">
              <div>
                根入台灣市場、放眼全球的其他類資產管理公司
              </div>
              <!-- <div class="item3 itembg1"><span>种子期</span></div>
              <div class="item3 itembg2"><span>早期</span></div>
              <div class="item3 itembg3"><span>成长期</span></div>
              <div class="item3 itembg4"><span>并购期</span></div>
              <div class="item3 itembg5"><span>公开市场</span></div> -->
            </div>
          </div>
          <div class="right">
            <div class="ribox">
              <p>投資歷程</p>
              <h4><span>14+</span>年</h4>
            </div>
            <div class="ribox">
              <p>被投企業</p>
              <h4><span>200+</span></h4>
            </div>
            <div class="ribox">
              <p>團隊規模</p>
              <h4><span>170+</span></h4>
            </div>
          </div>
        </div>
      </section>
      <section class="section4">
        <h2> 投資者關係</h2>
        <p>
          博裕擁有穩定的、感恩的、募集卓著的投資者，涵蓋全球頂尖的國家主權基金、退休基金、捐贈基金、金融機構、家族基金、母基金等。有關基金募集集與投資人關係相關服務，由投資人關係團隊負責協調與推動。如需詢問投資者關係，請聯絡我們。
        </p>
      </section>
      <section class="section4">
        <h2> 環境、社會與管理</h2>
        <p>
          博裕深刻體認到環境、社會和管治（ESG）因素舉足輕重，並相信將ESG因素納入投資和風險管理流程是實現長期價值成長的關鍵。
        </p>
        <div class="list1">
          <div class="li-ite1">
            <div class="v-head">
              <h3>ESG歷程</h3>
            </div>
            <div class="v-body">
              <p>我們將環境、社會和管治（ESG）要素納入公司的管理架構。博裕採取漸進式的ESG風險管理方法，以關注氣候相關風險管理為起點，同時持續關注產業中應對其他ESG風險的新興方法和實踐。</p>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>風險治理框架</h3>
            </div>
            <div class="v-body">
              <p>• 由博裕的營運委員會明確監督權</p>
              <p>• 由 ESG 委員會制定政策和流程細則</p>
              <p>• 由 ESG 工作小組監控投資組合企業的 ESG 風險</p>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>投資管理</h3>
            </div>
            <div class="v-body">
              <p>• 博裕多措並舉，綜合運用多種途徑監控其投資組合中的氣候相關風險權</p>
              <p>• 博裕在投後管理過程中進行定性和定量分析，以評估氣候相關風險的相關性與重要性</p>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>管理與參與</h3>
            </div>
            <div class="v-body">
              <p>• 博裕謀求與投資者和同產業夥伴們參與合作，在決策投資的領域上共同促進產業實踐的發展</p>
              <p>• 博裕將持續與投資組合企業就 ESG 事項積極進行溝通</p>
            </div>
          </div>
        </div>
      </section>
      <section class="section4">
        <h2>公益事業</h2>
        <p>
          哥倫比亞阿諾德植物園，各方植物保護
        </p>
        <div class="list1 list3">
          <div class="li-ite1">
            <div class="v-head">
              <h3>哥倫比亞阿諾德植物園，
                植物保護
              </h3>
            </div>
            <div class="v-body">
              <p>博裕在哈佛大學阿諾德植物園設立了“中國植物保護專項基金”和“瀕危植物保護研究基金”，旨在支持全球，特別是中國本土的植物多樣性研究，以及瀕危植物種子的悉心收集與保護工作。 </P>
              <P>
                在本計畫的支持下，哈佛植物園參與北京植物園、中科院昆明植物研究所以及浙江大學等國內學術前沿，共同致力於植物材料的遷地保護與原地收集活動，加強中美研究機構間的植物保護知識交流和合作夥伴。
              </p>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>設立北大博物學者培養基金，扶持青年文化使者
              </h3>
            </div>
            <div class="v-body">
              <p>博裕向北京大學捐資設立“北京大學博物學者培養基金”，最初北大中文系與英文系強強聯手合作設立本科雙學位專案。</P>
              <P>
                我們希望推動計畫引領北京大學創新本科階段的跨學科人才培育模式，培養兼具中國心和國際視野，同時豐富中華文化積累和世界文明洞察的青年文化使者，使他們成為連結中西文化、講好中國故事的文化使者，推動中國文化走向世界。
              </p>
            </div>
          </div>

        </div>
      </section>
      <!-- <section class="section5">
        <h1>我們的業務</h1>
        <section class="section4">
          <h2>私募股权</h2>
          <p>
            我们坚持行之有效的核心投资策略，努力为投资者创造出色的长期回报。
          </p>
          <div class="list1 list3">
            <div class="li-ite1">
              <div class="v-head">
                <h3>坚持深耕三个重点行业
                </h3>
              </div>
              <div class="v-body">
                <p>• 专注于科技创新、消费零售，以及医疗健康行业高科技</P>
                <P>
                  • 熟悉重点投资领域的行业发展政策与地区性差异
                </p>
                <p>
                  • 深谙行业动态、商业模式，对行业的本土特征和发展趋势具有独到和前瞻性的认识
                </p>
              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>致力提供全面增值服务
                </h3>
              </div>
              <div class="v-body">
                <p>
                  • 借助创始人丰富的企业运营经验，协助企业制定战略规划
                </P>
                <P>
                  • 运用广泛的行业资源和投资经验，协助企业提升运营效率
                </p>
                <p>
                  • 通过派驻董事、引进人才等方式，督促企业完善治理结构
                </p>
                <p>
                  • 凭借专业的收购兼并和融资经验，引领企业借力资本市场
                </p>
              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>积极创造独有投资机会
                </h3>
              </div>
              <div class="v-body">
                <p>• 率先接触到企业核心管理层，建立独家合作关系</P>
                <P>
                  • 积极围绕各行业发展主题，系统性地挖掘投资机会
                </p>
              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>精心设计最优交易结构
                </h3>
              </div>
              <div class="v-body">
                <p>• 以少数股权、相对控股投资为主</P>
                <P>
                  • 为企业提供增长和转型资本（包括业务拓展、股东再融资等）
                </p>
              </div>
            </div>
          </div>
        </section>
        <section class="section2">
          <h2>二級市场</h2>
          <p style="color: #666; line-height: 180%">
            秉承博裕的核心优势以我们擅长的一二級联动策略，精准捕捉新兴行业的发展趋势与重要拐点，进而为投资者带来卓越且持续的收益表现。
          </p>
          <div class="list1 list4">
            <div class="li-ite1">
              <div class="v-head">
                <h3>投资理念 </h3>
              </div>
              <div class="v-body">
                <p>• 遵循长期价值投资理念，寻找行业内的优质核心资产</p>
                <p>• 结合一二級观点及国内外视野，重点发掘二級市场上具成长性的企业</p>
                <p>• 在市场错配时寻求逆向投资机会</p>
                <p>• 风格严谨，注重安全边际和内在价值 </p>
              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>投研优势</h3>
              </div>
              <div class="v-body">
                <p>• 运用博裕在多个资产类别的经验与视角，搭建完整独特的二級市场投研体系</p>

                <p>• 一二級市场全面覆盖，充分把握行业趋势中的关键业务动态及变化</p>

                <p>• 对重点行业领域进行深入研究，建立广泛的人脉网络和拓展资源</p>

                <p>• 高效稳定的调研和数据研究架构</p>

              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>组合与回报</h3>
              </div>
              <div class="v-body">
                <p>• 深入参与A股、H股、ADR及其他多元市场</p>

                <p>• 通过卓越的上行收益能力和有效的下行风险控制实现优秀的投资回报</p>

                <p>• 重视选股能力，构建具备独特优势的投资组合，追求持续收益</p>

                <p>• 基于稳定的资本基础，坚持长期投资愿景</p>

              </div>
            </div>
          </div>
        </section>
        <section class="section2">
          <h2>不动产与新基建</h2>
          <p style="color: #666; line-height: 180%">
            博裕不动产团队拥有在中国及亚洲的丰富投资经验。自2020年开始不动产投资，已经在物流和数据中心板块成功建立了高质量且有韧性的投资组合。
          </p>
          <div class="list1 list4">
            <div class="li-ite1">
              <div class="v-head">
                <h3>聚焦新经济产业 </h3>
              </div>
              <div class="v-body">
                <p>• 物流</p>
                <p>• 数据中心</p>
                <p>• 新基建和政策鼓励的其他产业板块</p>
              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>创造投资机会</h3>
              </div>
              <div class="v-body">
                <p>• 创造独有投资机会的能力</p>
                <p>• 发挥博裕生态系统优势，协同各行业头部企业，主动挖掘投资机会</p>
              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>审慎执行</h3>
              </div>
              <div class="v-body">
                <p>• 谨慎严格的尽职调查</p>
                <p>• 积极参与精品平台的发展，以获取运营优势和收益</p>
              </div>
            </div>
          </div>
        </section>
        <section class="section4">
          <h2>风险投资</h2>
          <p>
            • 为了顺应风险投资阶段投资的迅速增长，以及风险投资与私募股权投资领域之间不断提升的协同效能，博裕在国内与国际市场同步设立风险投资业务条线万物创投（Zoo Capital）。
          </p>
          <div class="list1 list3">
            <div class="li-ite1">
              <div class="v-head">
                <h3>万物创投（Zoo Capital）
                </h3>
              </div>
              <div class="v-body">
                <p>由博裕联合年轻创业者和经验丰富的投资人共同创立，致力于科技、生命科学和出海的早期投资。我们专注于找到能引领颠覆性创新的创业家，并陪伴他们成为新经济的中流砥柱。</P>
              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>万物投资策略
                </h3>
              </div>
              <div class="v-body">
                <p>• 深度挖掘顶尖科技人才走向 </p>
                <p>• 坚持深耕重点行业 </p>
                <p>• 积极创造独有投资机会 </p>
                <p>• 精心设计最优交易结构 </p>
                <p>• 致力提供全方位增值服务 </p>
                <p>• 连接博裕的资源和生态网络 </p>
              </div>
            </div>
          </div>
        </section>
      </section> -->
      <section class="section4">
        <h2>投資領域</h2>
        <p>我們的投資主要集中在以下最具活力與成長性的產業：</p>
        <div class="content">
          <div class="item4">
            <img src="@/assets/images/indexb/tmt.svg" alt="" />
            虛擬科技 AI系統
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/healthcare.svg" alt="" />
            半導體晶片
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/consumer.svg" alt="" />
            醫療設備
          </div>
        </div>
      </section>
      <section class="section4">
        <h2>我們的合作夥伴</h2>
        <p>
          除了為企業發展提供資金之外，我們還在企業管理、全球化佈局、退出策略、人力資源、法律與財務、品牌與市場等多方面為企業提供專業支援、經驗和資源，幫助被投資企業實現長足發展。
        </p>
        <div class="content">
          <div class="item4">
            <img src="@/assets/images/indexb/icon-qygl.svg" alt="" />
            企業管理
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/oversea.svg" alt="" />
            全球化佈局
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/marketing.svg" alt="" />
            退出策略
          </div>
        </div>
        <div class="content">
          <div class="item4">
            <img src="@/assets/images/indexb/human.svg" alt="" />
            人力資源
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/icon-flcw.svg" alt="" />
            法律與財務
          </div>
          <div class="item4">
            <img src="@/assets/images/indexb/branding.svg" alt="" />
            品牌與市場
          </div>
        </div>
      </section>
      <!-- <div class="statement">
        <img src="@/assets/images/indexb/image.png" alt="" />
      </div> -->
    </div>
    <FooterBottom></FooterBottom>
  </div>
</template>

<style scoped lang="sass">

.bodybox
  max-width: 1120px
  padding: 74px 0
  margin: 0 auto
  position: relative
  .statement
    position: fixed
    top: 74px
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
        @media (max-width: 768px)
          img
            height: 60px
    p
      margin-bottom: 15px
  .section3
    margin-top: 100px
    .content
      display: flex
    .left
      width: 69.6%
      .list
        display: flex
        background-color: #f4f6f7
        height: 120px
        overflow: hidden
        div
          width: 100%
          height: 100%
          padding: 20px
          display: flex
          align-items: center
          justify-content: center
          font-size: 35px
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
        padding: 28px 0
        span
          font-size: 55px
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

  .section5
    padding: 80px 0 40px
    h1
      font-size: 50px
      text-align: center

  .table
    margin-top: 50px
    width: 100%
    ul
      width: 100%
      text-align: center
      li
        margin-bottom: 20px
        .tb-item
          display: flex
          justify-content: center
          padding: 20px 10px
          gap: 20px
          h4
            font-weight: bold
          p
            color: #666
          @media (max-width: 768px)
            flex-direction: column
      h2
        font-size: 30px
        margin-bottom: 0
        padding: 0
        &::after
          background: none !important
          border: none !important
  .list2
    grid-template-columns: repeat(auto-fill, minmax(330px, 1fr)) !important
    .v-body
      padding: 0 !important
      ul
        li
          padding: 14px 25px
          margin-block: 1px
          h4
            font-weight: bold
  .list3
    grid-template-columns: repeat(auto-fill, minmax(440px, 1fr)) !important  
  .list4
    grid-template-columns: repeat(auto-fill, minmax(330px, 1fr)) !important
  .list1
    display: grid
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr))
    justify-content: space-between
    gap: 2px
    background-color: #fff
    .li-ite1
      background-color: #fafafa
      .v-head
        background-color: #eee9e0
        padding: 20px
        text-align: center
        color: #9f0d40
        font-weight: bold
      .v-body
        background-color: #fafafa
        padding: 25px 15px


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

@media (max-width: 768px)
  .banner
    .item
      padding: 50px 30px !important
      p
        width: 100% !important
        white-space: pre-wrap
  .bodybox .banner .drop
    left: 50%
    transform: translateX(-50%)
  .section2,.section3,.section4,.section5
    padding-inline: 20px
    
  .bodybox 
    .section2
      margin-top: 50px
      .content
        padding: 40px 0 !important
        flex-direction: column
        gap: 20px
    .section3
      .content
        flex-direction: column
        .left
          width: 100%
          .list
            height: auto
            div
              font-size: 20px
        .right
          margin: 0
          padding: 0
          width: 100%
    .section4
      margin-top: 50px
      .content
        flex-direction: column
        .item4
          border: none
    .list3
      grid-template-columns: repeat(auto-fill, minmax(330px, 1fr)) !important  
</style>

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
          <h2>独具一格</h2>
          <p>
            作为率先在中国开展风险投资业务的投资机构，博裕
            投資
            已发展成为一家扎根中国市场、具备全球化视野的私募股权投资机构。
          </p>
        </div>
        <div :class="bannerIndex == 1 ? 'banneractive' : ''" class="item bgimg2">
          <h2>深度互信</h2>
          <p>
            博裕
            投資与包括主权基金/国家级出资平台、养老基金、专业金融机构、产业资本以及家族办公室等合作伙伴保持长期稳定的合作关系。
          </p>
        </div>
        <div :class="bannerIndex == 2 ? 'banneractive' : ''" class="item bgimg3">
          <h2>卓越业绩</h2>
          <p>
            博裕 投資已扶植逾 600
            家企业通过在中国大陆、中国香港、美国、欧洲资本市场 IPO 或 M&A
            形式成功实现退出，支持了中国近一半的独角兽企业。
          </p>
        </div>
        <div class="drop">
          <div :class="bannerIndex == 0 ? 'dropactive' : ''" class="dropitem" @click="bannerIndex = 0"></div>
          <div :class="bannerIndex == 1 ? 'dropactive' : ''" class="dropitem" @click="bannerIndex = 1"></div>
          <div :class="bannerIndex == 2 ? 'dropactive' : ''" class="dropitem" @click="bannerIndex = 2"></div>
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
          博裕投资创立于2011年，是一家深耕中国市场、布局全球的另类资产管理公司。公司构建了涵盖私募股权投资、上市公司战略配置、物流仓储与数据中心投资、创业投资、新能源产业平台的多元化投资矩阵。博裕深度聚焦科技创新、消费零售以及医疗健康三大重点领域。依托一体化、协同联动的投资管理平台，致力于长期为投资者创造卓越的价值和回报。
        </p>
      </section>
      <section class="section2">
        <h2>發展歷程</h2>
        <p style="color: #666; line-height: 180%">
          成立于2011年，始于私募股权投资，随后于2016年拓展业务至二级市场投资领域，并在2020年启动不动产与新基建投资及风险投资。如今，博裕已发展成为一个综合协同的投资平台。
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
              <h3>成立二级市場投資</h3>
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
        <h2>业务范围</h2>
        <div class="content">
          <div class="left">
            <img src="@/assets/images/indexb/business.jpg" alt="" />
            <div class="list">
              <div>
                植根中国、放眼全球的另类资产管理公司
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
          博裕拥有稳定的、多元化的、声誉卓著的投资者，涵盖全球顶级的国家主权基金、养老基金、捐赠基金、金融机构、家族基金、母基金等。有关基金募集与投资者相关服务，由投资者关系团队负责协调和推动。如需垂询投资者关系事宜，请联系我们。
        </p>
      </section>
      <section class="section4">
        <h2> 环境、社会和管治</h2>
        <p>
          博裕深刻认识到环境、社会和管治（ESG）因素举足轻重，并相信将 ESG 因素纳入投资和风险管理流程是实现长期价值增长的关键。
        </p>
        <div class="list1">
          <div class="li-ite1">
            <div class="v-head">
              <h3>ESG歷程</h3>
            </div>
            <div class="v-body">
              <p>我们将环境、社会和管治（ESG）要素纳入公司的管理框架。博裕采取渐进式的 ESG 风险管理方法，以关注气候相关风险管理为起点，同时持续关注行业中应对其他 ESG 风险的新兴方法和实践。</p>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>風險治理框架</h3>
            </div>
            <div class="v-body">
              <p>• 由博裕的运营委员会行使最终监督权</p>
              <p>• 由 ESG 委员会制定政策和流程细则</p>
              <p>• 由 ESG 工作组监测投资组合企业的 ESG 风险</p>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>投資管理</h3>
            </div>
            <div class="v-body">
              <p>• 博裕多措并举，综合运用多种途径监控其投资组合中的气候相关风险权</p>
              <p>• 博裕在投后管理过程中进行定性和定量分析，以评估气候相关风险的相关性与重要性</p>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>管理與參與</h3>
            </div>
            <div class="v-body">
              <p>• 博裕谋求与投资者和同行业伙伴们携手合作，在负责任投资的领域上共同促进行业实践的发展</p>
              <p>• 博裕将持续与投资组合企业就 ESG 事项积极进行沟通</p>
            </div>
          </div>
        </div>
      </section>
      <section class="section4">
        <h2>公益事业</h2>
        <p>
          携手哈佛大学阿诺德植物园，倡导植物保护
        </p>
        <div class="list1 list3">
          <div class="li-ite1">
            <div class="v-head">
              <h3>携手哈佛大学阿诺德植物园，
                倡导植物保护
              </h3>
            </div>
            <div class="v-body">
              <p>博裕在哈佛大学阿诺德植物园设立“中国植物保护专项基金”和“濒危植物保护研究基金”，旨在支持全球，特别是中国本土的植物多样性研究，以及濒危植物种子的悉心收集与守护工作。 </P>
              <P>
                在该项目的支持下，哈佛植物园携手北京植物园、中科院昆明植物研究所以及浙江大学等国内学术翘楚，共同致力于植物材料的迁地保护与原地收集活动，加强中美研究机构间的植物保护知识交流和合作伙伴关系。
              </p>
            </div>
          </div>
          <div class="li-ite1">
            <div class="v-head">
              <h3>设立北京大学博物学者培养基金，助力培养青年文化使者
              </h3>
            </div>
            <div class="v-body">
              <p>博裕向北京大学捐资设立“北京大学博物学者培养基金”，促成北大中文系与英文系强强联手合作设立本科双学位项目。</P>
              <P>
                我们希望借此项目助力北京大学创新本科阶段的跨学科人才培养模式，培育兼具中国心和国际视野，又富有中华文化积淀和世界文明洞察的青年文化使者，使他们成为连接中西文化、讲好中国故事的文化使者，推动中国文化走向世界。
              </p>
            </div>
          </div>

        </div>
      </section>
      <section class="section5">
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
          <h2>二级市场</h2>
          <p style="color: #666; line-height: 180%">
            秉承博裕的核心优势以我们擅长的一二级联动策略，精准捕捉新兴行业的发展趋势与重要拐点，进而为投资者带来卓越且持续的收益表现。
          </p>
          <div class="list1 list4">
            <div class="li-ite1">
              <div class="v-head">
                <h3>投资理念 </h3>
              </div>
              <div class="v-body">
                <p>• 遵循长期价值投资理念，寻找行业内的优质核心资产</p>
                <p>• 结合一二级观点及国内外视野，重点发掘二级市场上具成长性的企业</p>
                <p>• 在市场错配时寻求逆向投资机会</p>
                <p>• 风格严谨，注重安全边际和内在价值 </p>
              </div>
            </div>
            <div class="li-ite1">
              <div class="v-head">
                <h3>投研优势</h3>
              </div>
              <div class="v-body">
                <p>• 运用博裕在多个资产类别的经验与视角，搭建完整独特的二级市场投研体系</p>

                <p>• 一二级市场全面覆盖，充分把握行业趋势中的关键业务动态及变化</p>

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

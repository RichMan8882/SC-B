<template>
  <div class="page-container">
    <div class="card">
      <h1 class="card-title">欢迎访问</h1>
      <p class="card-description">
        点击下方链接不仅可以打开网页，还会自动复制链接到您的剪贴板。
      </p>

      <div class="link-wrapper">
        <a :href="targetUrl" target="_blank" rel="noopener noreferrer" class="target-link" @click="handleLinkClick">
          {{ targetUrl }}
        </a>

        <button class="copy-btn" @click="copyToClipboard(targetUrl)">
          <span v-if="!isCopied">复制</span>
          <span v-else class="copied-text">已复制!</span>
        </button>
      </div>

      <transition name="fade">
        <div v-if="showToast" class="toast">
          链接已成功复制到剪贴板！
        </div>
      </transition>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const targetUrl = ref('https://example.com/your-target-link')
const isCopied = ref(false)
const showToast = ref(false)

const copyToClipboard = async (text) => {
  try {
    await navigator.clipboard.writeText(text)
    triggerCopySuccess()
  } catch (err) {
    const textArea = document.createElement('textarea')
    textArea.value = text
    document.body.appendChild(textArea)
    textArea.select()
    try {
      document.execCommand('copy')
      triggerCopySuccess()
    } catch (fallbackErr) {
      console.error('复制失败:', fallbackErr)
    }
    document.body.removeChild(textArea)
  }
}

const triggerCopySuccess = () => {
  isCopied.value = true
  showToast.value = true

  setTimeout(() => {
    isCopied.value = false
    showToast.value = false
  }, 2000)
}

const handleLinkClick = (event) => {
  copyToClipboard(targetUrl.value)
}
</script>

<style lang="sass" scoped>
// 定义 Sass 变量
$primary-color: #3498db
$success-color: #2ecc71
$bg-color: #f5f7fa
$text-color: #2c3e50
$border-radius: 8px
$transition-speed: 0.3s

.page-container
  display: flex
  justify-content: center
  align-items: center
  min-height: 100vh
  background-color: $bg-color
  font-family: 'Helvetica Neue', Arial, sans-serif

.card
  background: #ffffff
  padding: 2.5rem
  border-radius: $border-radius
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05)
  max-width: 500px
  width: 90%
  text-align: center

  &-title
    color: $text-color
    margin-bottom: 1rem
    font-size: 1.8rem

  &-description
    color: #7f8c8d
    font-size: 0.95rem
    margin-bottom: 2rem
    line-height: 1.5

.link-wrapper
  display: flex
  align-items: center
  border: 1px solid #e0e0e0
  border-radius: $border-radius
  padding: 0.5rem 0.5rem 0.5rem 1rem
  background: white
  transition: border-color $transition-speed

  &:hover
    border-color: $primary-color

.target-link
  color: $primary-color
  text-decoration: none
  font-weight: 500
  white-space: nowrap
  overflow: hidden
  text-overflow: ellipsis
  flex-grow: 1
  text-align: left
  margin-right: 1rem

  &:hover
    text-decoration: underline

.copy-btn
  background-color: $primary-color
  color: white
  border: none
  padding: 0.6rem 1.2rem
  border-radius: calc(#{$border-radius} - 2px)
  cursor: pointer
  font-weight: bold
  transition: background-color $transition-speed, transform 0.1s
  min-width: 80px

  &:hover
    background-color: darken($primary-color, 10%)

  &:active
    transform: scale(0.95)

  .copied-text
    color: #fff
    animation: pulse 0.3s ease-in-out

/* 提示弹窗样式 */
.toast
  position: fixed
  bottom: 30px
  left: 50%
  transform: translateX(-50%)
  background-color: rgba($text-color, 0.9)
  color: white
  padding: 0.8rem 1.5rem
  border-radius: 30px
  font-size: 0.9rem
  box-shadow: 0 4px 15px rgba(0,0,0,0.2)
  z-index: 1000

/* Vue 动画过渡效果 */
.fade-enter-active, .fade-leave-active
  transition: opacity 0.3s, transform 0.3s

.fade-enter-from, .fade-leave-to
  opacity: 0
  transform: translate(-50%, 20px)

@keyframes pulse
  0%
    transform: scale(1)
  50%
    transform: scale(1.1)
  100%
    transform: scale(1)
</style>

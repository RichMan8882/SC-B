<script lang="ts" setup></script>

<template>
  <div class="page">
    <div class="bgimgr">
      <div class="mask"></div>
    </div>
    <client-only><router-view></router-view></client-only>
  </div>
</template>
<style scoped lang="sass">
.page
  position: relative
  width: 100dvw
  // height: 100dvh
  font-family: 'Martinass'
  
  overflow-y: auto
  .bgimgr
    position: fixed
    width: 100%
    height: 100%
    background: url(@/assets/images/homebg.webp) !important
    background-size: cover !important
    background-position: center 80% !important
    .mask
      background: linear-gradient(to right, rgba(0,0,0,1) 0%,rgba(0,0,0,1) 30%, rgba(0,0,0,0) 100%)
      opacity: 0.6
      position: absolute
      width: 100%
      height: 100%
</style>
<style scoped lang="sass">
iframe
  width: 100dvw
  height: 100dvh
</style>

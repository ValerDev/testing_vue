<template>
<div class="imgBlockContent">
  <div  class="imgMainBlock" v-if="isImageOpen">
    <div class="layout"></div>
    <img src="https://via.placeholder.com/760x320/2200631" />
    <el-button type="primary" class="detail-button" @click="isImageOpen = !isImageOpen">
      <img src="../assets/img/icons/plus.svg" alt=""  class=""/>
      <span>Add Pricing</span>
    </el-button>
  </div>
  <div v-else class="imgMainBlockAfter">
      <div class="layoutAfter">
        <div class="layoutButtonBlock">
          <el-button type="primary" class="detail-button" @click="isImageOpen = !isImageOpen">
              <span>Idea</span>
          </el-button>
          <el-button type="primary" class="detail-button" @click="isImageOpen = !isImageOpen">
              <span>In development</span>
          </el-button>
        </div>
        <span>10+</span>
      </div>
      <img src="https://via.placeholder.com/760x320/2200631" />
    </div>
</div>
</template>
<script>
export default {
  data () {
    return {
      isImageOpen: true
    }
  }
}
</script>
<style lang='sass'>
@import '../assets/sass/background/background'
</style>

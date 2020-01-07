<template>
  <div class="m-menu">
    <div class="nav">
      <dt>全部分类</dt>
      <dd
        v-for="(item, index) in menu"
        :key="index"
      >
        <i :class="item.type" />{{item.name}}<span class="arrow" />
      </dd>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      menu: [{
        type: 'food',
        name: '美食'
      },
      {
        type: 'takeout',
        name: '外卖'
      }]
    }
  },
}
</script>

<style lang="scss">
 @import "@/assets/css/index/index.scss";
</style>
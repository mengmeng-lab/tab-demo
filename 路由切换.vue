<template>
  <div>
      <div class="tab">
        <router-link to="firstTab" class="router-link">firstTab</router-link>
        <router-link to="secondTab" class="router-link">secondTab</router-link>
        <router-link to="thirdTab" class="router-link">thirdTab</router-link>
    </div>
  </div>
</template>

<script>

export default {
    name: 'Home',
}
</script>
<style scoped>
.router-link{width: 220px; height: 84px; border: 1px solid #999; background: transparent; cursor: pointer; display: inline-block; margin-left: 24px; border-radius: 8px;
font: bold 24px/84px 'Microsoft Yahei'; text-align: center; text-decoration: none; color: #333; }
</style>


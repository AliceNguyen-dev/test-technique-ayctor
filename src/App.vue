<script setup lang="ts">

import userList from './views/userList.vue'
</script>

<template class="main-app">
  <userList />
      
  <div class="angle-bgk"></div>
  
</template>

<style scoped>
#app{
  display:flex;
}
.angle-bgk {
    width: 780px;
    height: 776px;
    background: #f3f3f3;
    clip-path: polygon(1% 53%, 101% 0%, 110% 99%);
}
</style>

<template>
  <div v-show="ifShow" class="main-head">
    <i class="el-icon-arrow-left" v-show="ifBack"></i>
    <span class="main-head-title">{{ mainHeadTitle }}</span>
  </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: 'MainHead',
  computed: {
    ...mapState(['mainHeadTitle', 'ifShow', 'ifBack'])
  }
}
</script>

<style lang="less">
@primaryColor: #2d303b;

.main-head {
  height: 60px;
  line-height: 60px;
  color: @primaryColor;

  > i {
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
  }

  .main-head-title {
    font-size: 16px;
    font-weight: 500;
    cursor: pointer;
  }
}
</style>

<template>
  <div>
    <layout-head />
    <div>
      <side-bar />
      <div :class="{spreadContainer: collapse}" class="main-container">
        <el-scrollbar wrap-class="main-scrollbar">
          <el-container direction="vertical">
            <el-main class="nuxt-main">
              <main-head />
              <nuxt class="nuxt-container"></nuxt>
            </el-main>
            <el-footer>
              <copyright></copyright>
            </el-footer>
          </el-container>
        </el-scrollbar>
      </div>
    </div>
  </div>
</template>

<script>
import Copyright from '../components/copyright.vue'
import LayoutHead from '../container/layout-head/layout-head.vue'
import {mapState, mapGetters} from 'vuex'
import auth from '@/mixins/auth'
import MainHead from '../container/main-head/index.vue'
import SideBar from '../container/side-bar/index.vue'

export default {
  mixins: [auth],
  components: {
    Copyright,
    LayoutHead,
    MainHead,
    SideBar
  },
  computed: {
    ...mapState(['collapse'])
  }
}
</script>
<style lang="less">
@import '../assets/variables.less';

#__nuxt {
  @title-bg: rgba(242, 244, 249, 1);
  @menu-height: 50px;
  @primary-color: #1890ff;
  @main-bg: #f7f8fb;

  // 主体区域 Main container

  .main-container {
    transition: margin-left 0.28s;
    margin-left: @sideBarMaxWidth;
    height: 100%;
    position: relative;
    background-color: @main-bg;

    &.spreadContainer {
      margin-left: @sideBarMinWidth;
    }

    .main-scrollbar {
      min-height: calc(100vh - 60px);
      overflow-x: hidden !important;
      margin-bottom: 0 !important;
    }

    .el-scrollbar__view {
      height: 100%;
    }

    .el-scrollbar__bar.is-vertical {
      right: 0;
    }

    .is-horizontal {
      display: none;
    }
  }

  .nuxt-main {
    position: relative;
    min-height: calc(100vh - 60px - 60px);

    /* margin: 24px 24px 0; */
    overflow-x: hidden;
    padding: 0 24px;
  }
}
</style>

<template>
    <div>
      <div :class="['search-head', layout, pageWidth]">
        <div class="search-input">
          <a-input-search class="search-ipt" style="width: 522px" placeholder="请输入..." size="large" enterButton="搜索" />
        </div>
        <div style="padding: 0 24px">
          <a-tabs :tabBarStyle="{margin: 0}" @change="navigate" :activeKey="activeKey">
            <a-tab-pane tab="文章" key="1"></a-tab-pane>
            <a-tab-pane tab="应用" key="2"></a-tab-pane>
            <a-tab-pane tab="项目" key="3"></a-tab-pane>
          </a-tabs>
        </div>
      </div>
      <div class="search-content">
        <router-view />
      </div>
    </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: 'SearchLayout',
  computed: {
    ...mapState('setting', ['layout', 'pageWidth']),
    activeKey () {
      switch (this.$route.path) {
        case '/list/search/article':
          return '1'
        case '/list/search/application':
          return '2'
        case '/list/search/project':
          return '3'
        default:
          return '1'
      }
    }
  },
  methods: {
    navigate (key) {
      switch (key) {
        case '1':
          this.$router.push('/list/search/article')
          break
        case '2':
          this.$router.push('/list/search/application')
          break
        case '3':
          this.$router.push('/list/search/project')
          break
        default:
          this.$router.push('/workplace')
      }
    }
  }
}
</script>

<style lang="less" >
  .search-head{
    background-color: @base-bg-color;
    margin: -24px;
    &.head.fixed{
      margin: -24px 0;
    }
    .search-input{
      text-align: center;
    }
  }
  .search-content{
    margin-top: 48px;
  }
</style>

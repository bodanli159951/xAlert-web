<template>
  <div class="container">
    <el-row>
      <el-col :span="3" class="left">
        <business title="业务"></business>
        <vulneCountStat></vulneCountStat>
        <vulneGradeStat></vulneGradeStat>
      </el-col>
      <el-col :span="21">
        <el-row>
          <el-col :xs="24" :sm="24" :lg="24">
            <vulneDistribution id="vulneDistribution" title="漏洞分布" :height="400" width="100%"></vulneDistribution>
          </el-col>
        </el-row>
        <el-row>
          <el-col :xs="24" :sm="24" :lg="24">
            <new-table-wrapper title="漏洞列表" tableHeight="350px">
              <vulne-list :dataList="vulneList"></vulne-list>
            </new-table-wrapper>
          </el-col>
        </el-row>
      </el-col>
    </el-row>
  </div>
</template>
<script type="text/ecmascript-6">
  import business from './components/business'
  import vulneCountStat from './components/vulneCountStat'
  import vulneGradeStat from './components/vulneGradeStat'
  import vulneDistribution from './components/vulneDistribution'
  import vulneList from './components/vulneList'
  import newTableWrapper from 'components/table/newTableWrapper'
  import axios from 'axios'
  export default {
    components: {
      business,
      vulneCountStat,
      vulneGradeStat,
      vulneDistribution,
      vulneList,
      newTableWrapper
    },
    data() {
      return {
        vulneList: []
      }
    },
    methods: {
      getVulneList() {
        axios.get('/api/analysis/table.json')
          .then(res => {
            res = res.data
            if (res.ret && res.data) {
              const data = res.data.vulne
              this.vulneList = data.vulneData
            }
          })
      }
    },
    created() {
      this.getVulneList()
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "~common/stylus/variable"
  @import "~common/stylus/mixin"
</style>
<style lang="stylus" rel="stylesheet/stylus" scoped>
  .container {
    background-color #fff
  }
  .left {
    background-color #f5f5f5
    height 1350px
  }
</style>
<style lang="stylus" rel="stylesheet/stylus">
  .container
    .el-tabs--card>.el-tabs__header {
      margin-bottom 0
    }
</style>

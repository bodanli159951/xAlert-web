<script type="text/ecmascript-6">
  import Chart from 'components/charts/chart'
  // import { getColor } from '@/utils/index'

  export default {
    extends: Chart,
    data() {
      return {
        chart: null,
        option: {
          tooltip: {
            trigger: 'item',
            formatter: '{a} <br/>{b} : {c} ({d}%)'
          },
          legend: {
            show: false,
            data: ['高危', '中危', '低危', '严重', '信息']
          },
          series: [
            {
              name: '漏洞等级分布',
              type: 'pie',
              radius: '75%',
              center: ['50%', '50%'],
              label: {
                fontSize: 15
              },
              data: [
                {value: 2, name: '高危'},
                {value: 5, name: '中危'},
                {value: 5, name: '低危'},
                {value: 1, name: '严重'},
                {value: 7, name: '信息'}
              ]
            }
          ]
        }
      }
    }
  }
</script>

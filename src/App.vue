<template>
  <div id="app">
    <div class="block">
      <span class="demonstration">默认</span>
      <date-picker
        v-model="value1"
        type="yearrange"
        range-separator="至"
        start-placeholder="开始年份"
        end-placeholder="结束年份">
      </date-picker>
    </div>
    <div class="block">
      <span class="demonstration">带快捷选项</span>
      <date-picker
        v-model="value2"
        type="yearrange"
        align="right"
        unlink-panels
        range-separator="至"
        start-placeholder="开始年份"
        end-placeholder="结束年份"
        :picker-options="pickerOptions">
      </date-picker>
    </div>
  </div>
</template>

<script>
import DatePicker from './components/date-picker'
import './components/date-picker.css'

export default {
  name: 'App',
  components: {
    DatePicker
  },
  data() {
    return {
      pickerOptions: {
        shortcuts: [{
          text: '今年',
          onClick(picker) {
            picker.$emit('pick', [new Date(), new Date()])
          }
        }, {
          text: '2000年至今',
          onClick(picker) {
            const end = new Date();
            const start = new Date(new Date('2000').getFullYear(), 0)
            picker.$emit('pick', [start, end])
          }
        }]
      },
      value1: '',
      value2: ''
    }
  }
}
</script>

<style>
</style>

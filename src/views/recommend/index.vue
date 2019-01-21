<template>
  <div class="app-container">
    <el-form ref="form" :model="form" label-width="85px">
      <el-form-item label="出发地选择">
        <el-cascader
          :options="options"
          v-model="form.sendAddrCode"
          size="large"
          @change="handleChangeSend"
        />
      </el-form-item>
      <el-form-item label="详细地址">
        <el-input v-model="form.sendAddrDetail" />
      </el-form-item>
      <el-form-item label="达到地选择">
        <el-cascader
          :options="options"
          v-model="form.destiAddrCode"
          size="large"
          @change="handleChangeDesti"
        />
      </el-form-item>
      <el-form-item label="详细地址">
        <el-input v-model="form.destiAddrDetail" />
      </el-form-item>
      <el-form-item label="货物重量">
        <el-select v-model="form.weight" placeholder="请选择">
          <el-option
            v-for="item in weightOptions"
            :key="item.value"
            :label="item.label"
            :value="item.value"/>
        </el-select>
      </el-form-item>
      <el-form-item label="货物品种">
        <el-select v-model="form.weight" placeholder="请选择">
          <el-option
            v-for="item in weightOptions"
            :key="item.value"
            :label="item.label"
            :value="item.value"/>
        </el-select>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">下一步</el-button>
        <!-- <el-button>取消</el-button> -->
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import { regionData, CodeToText } from 'element-china-area-data'
export default {
  data() {
    return {
      options: regionData,
      selectedOptions: [],
      weightOptions: [{
        value: '选项1',
        label: '<10kg'
      }, {
        value: '选项2',
        label: '>10kg'
      }],
      form: {
        sendAddrCode: [],
        sendAddrText: '',
        sendAddrDetail: '',
        destiAddrCode: [],
        destiAddrText: '',
        destiAddrDetail: '',
        weight: ''
      }
    }
  },

  methods: {
    handleChangeSend(value) {
      console.log(value)
      value.forEach((element, index) => {
        if (index === 0) {
          this.form.sendAddrText = ''
        }
        this.form.sendAddrText += CodeToText[element]
      })
      console.log(this.form.sendAddrText)
    }, handleChangeDesti(value) {
      console.log(value)
      value.forEach((element, index) => {
        if (index === 0) {
          this.form.destiAddrText = ''
        }
        this.form.destiAddrText += CodeToText[element]
      })
      console.log(this.form.destiAddrText)
    },
    onSubmit() {
      console.log(this.form)
      // 命名的路由
      // this.$router.push({ name: 'Demand' })
      this.$router.push({ name: 'Demand', params: { selectForm: this.form }})
    }
  }
}
</script>

<style lang="scss" scoped>
.el-form{
  max-width: 400px;
}
</style>


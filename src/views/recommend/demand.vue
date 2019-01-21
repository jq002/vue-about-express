<template>
  <div class="app-container demand-container">
    <el-form ref="form" :model="form" label-width="230px">
      <el-form-item label="货物是否需要严格按时间规定送达">
        <el-radio-group v-model="form.radio1">
          <el-radio :label="1">是</el-radio>
          <el-radio :label="2">一般</el-radio>
          <el-radio :label="3">否</el-radio>
        </el-radio-group>
      </el-form-item>
      <el-form-item label="运输过程货物质量是否有严格要求">
        <el-radio-group v-model="form.radio2">
          <el-radio :label="1">是</el-radio>
          <el-radio :label="2">一般</el-radio>
          <el-radio :label="3">否</el-radio>
        </el-radio-group>
      </el-form-item>
      <el-form-item label="是否需要实时的物流信息">
        <el-radio-group v-model="form.radio3">
          <el-radio :label="1">是</el-radio>
          <el-radio :label="2">一般</el-radio>
          <el-radio :label="3">否</el-radio>
        </el-radio-group>
      </el-form-item>
      <el-form-item label="交易流程便捷性">
        <el-radio-group v-model="form.radio4">
          <el-radio :label="1">是</el-radio>
          <el-radio :label="2">一般</el-radio>
          <el-radio :label="3">否</el-radio>
        </el-radio-group>
      </el-form-item>
      <el-form-item label="客服服务质量是否有要求">
        <el-radio-group v-model="form.radio5">
          <el-radio :label="1">是</el-radio>
          <el-radio :label="2">一般</el-radio>
          <el-radio :label="3">否</el-radio>
        </el-radio-group>
      </el-form-item>
      <el-form-item label="交易费用是否要求严格控制">
        <el-radio-group v-model="form.radio6">
          <el-radio :label="1">是</el-radio>
          <el-radio :label="2">一般</el-radio>
          <el-radio :label="3">否</el-radio>
        </el-radio-group>
      </el-form-item>
      <el-form-item label="其他特殊要求">
        <el-input v-model="form.desc" type="textarea"/>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onBack">上一步</el-button>
        <el-button type="primary" @click="onSubmit">提交</el-button>
        <!-- <el-button>取消</el-button> -->
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        radio1: '',
        radio2: '',
        radio3: '',
        radio4: '',
        radio5: '',
        radio6: '',
        desc: ''
      },
      selectForm: {}
    }
  },
  mounted() {
    this.selectForm = this.$route.params.selectForm
  },
  methods: {
    onSubmit() {
      console.log(this.form)
      // 命名的路由
      this.$router.push({ name: 'Result' })
    },
    onBack() {
      this.$router.push({ name: 'Recommend' })
    }
  }

}
</script>

<style lang="scss" >

.demand-container {
    .el-form{
    max-width: 450px;
  }
}
@media screen and (max-width: 500px) {
  .demand-container {
    .el-form-item__content{
      margin-left: 0!important;
      clear: both;
    }
    .el-form-item__label{
      text-align: left;
    }
  }
}
</style>

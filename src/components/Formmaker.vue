<template>
  <div class = 'Formmaker'>
  <el-form ref="func(form)" :model="func(form)" label-width="80px"> 
      <Itemmaker v-for="i in form.required" v-bind:key="i.id" :form = "i" :required="'true'"></Itemmaker>

      <Itemmaker v-for="i in form.optional" v-bind:key="i.id" :form = "i" :required="'false'"></Itemmaker>

      <el-form-item>
        <el-button type="primary" @click="submitForm('func(form)')">提交</el-button>
      </el-form-item>
  </el-form>
  </div>
</template>

<script>
import Itemmaker from './Itemmaker.vue'

export default {
  props:{
    'form':{
      type: Object,
      required: true
    }
  },
  components:{
    'Itemmaker': Itemmaker
  },
  methods: {
    func: function (item) {
      var values = {}
      for (var obj in item){
        for (var i = 0; i < item[obj].length; i ++){
          values[item[obj][i].id] = item[obj][i].default
        }
      }
      return values
    },
    submitForm(form) {
        this.$refs[form].validate((valid) => {
          if (valid) {
            this.$message({
              message: '表单提交成功！',
              type: 'success'
            })
          }else {
            this.$message.error('提交不成功！')
            return false;
          }
        })
      }
    }
  }
</script>

<style>
</style>
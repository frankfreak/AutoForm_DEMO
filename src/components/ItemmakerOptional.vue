<template>


  <el-form-item :label="form.label" :rules="Rules" :prop="form.id">
  	
    <el-input 
      v-if="form.type==='CharField'"
      type="text"
      placeholder='请输入'
      v-model="form.default"
      :maxlength = "form.max_length"
      :minlength = "form.min_length"
      show-word-limit
    ></el-input>

    <el-input-number
      v-else-if="form.type==='IntegerField'"
      v-model.number="form.default"
      :min="form.min_value"
      :max="form.max_value"
    ></el-input-number>

    <el-switch
      v-else-if="form.type==='BooleanField'"
      v-model="form.default"
    ></el-switch>

    <el-date-picker
      v-else-if="form.type==='DateField'"
      v-model="form.default"
      placeholder='选择日期'
      value-format="yyyy-MM-dd"
    ></el-date-picker>

    <el-time-picker
      v-else-if="form.type==='TimeField'"
      v-model="form.default"
      placeholder='选择时间'
      value-format="HH:mm:ss"
    ></el-time-picker>

    <el-date-picker
      v-else-if="form.type==='DateTimeField'"
      type="datetime"
      v-model="form.default"
      placeholder='选择时间日期'
      value-format="yyyy-MM-dd HH:mm:ss"
    ></el-date-picker>

    <el-input 
      v-else-if="form.type==='EmailField'"
      placeholder='请输入'
      v-model="form.default"
    ></el-input>

    <el-upload
      v-else-if="form.type==='FileField'"
      action="https://jsonplaceholder.typicode.com/posts/"
      multiple
      :limit="3">
      <el-button size="small" type="primary">点击上传</el-button>
      <div slot="tip" class="el-upload__tip">只能上传jpg/png文件，且不超过500kb</div>
    </el-upload>

    <el-input-number
      v-else-if="form.type==='FloatField'"
      v-model.number="form.default"
      :step="0.1"
    ></el-input-number>

    <el-select 
    v-else-if="form.type==='ChoiceField'"
    v-model="form.default" 
    placeholder="请选择">
      <el-option
        v-for="keys,values in form.choices"
        :key="values"
        :label="keys"
        :value="values">
      </el-option>
    </el-select>

    <el-input
      v-else-if="form.type===undefined"
      v-model="form.default"
      placeholder="请输入"
    ></el-input>

    <el-radio-group
      v-else-if="form.type==='SingleChoiceField'"
      v-model="form.default">
        <el-radio
          v-for="(keys,values) in form.choices"
          v-bind:key="values.id"
          :label="values">{{keys}} 
        </el-radio>
    </el-radio-group>

    <el-checkbox-group 
      v-else-if="form.type==='MultipleChoiceField'"
      v-model="form.default">
        <el-checkbox 
          v-for="(keys,values) in form.choices"
          v-bind:key="values.id"
          :label="values">{{keys}}
        </el-checkbox>
    </el-checkbox-group>


  </el-form-item>


</template>
<script>
export default {
  props:{
    'form':{
      type: Object,
      required: true
    }},
  computed:{
    Rules(){
      const R =[]
      const {form} = this
      if (form.type==='CharField'){
        R.push({required: false, message:'请输入', trigger: 'blur' },
          {
          validator(rule,value,callback){
            if(value.length <form.min_length){
              callback(new Error("输入长度过短，最短："+form.min_length+"字符"));            
            }else {
              callback()
            }
          },trigger: 'blur'
        })
      }
      if (form.type==='IntegerField'){
        R.push({required: false, message:'请输入', trigger: 'blur' },
        {
          validator(rule,value,callback){
            if(Number.isInteger(value)){
              callback();
            } else{
              callback(new Error("请输入整数"));               
            }
          },trigger: 'blur'
        })
      }
      if (form.type==='BooleanField'){
        R.push({required: false, message:'请选择', trigger: 'blur' })
      }
      if (form.type==='DateField'){
        R.push({required: false, message:'请选择', trigger: 'blur' })
      }
      if (form.type==='TimeField'){
        R.push({required: false, message:'请选择', trigger: 'blur' })
      }
      if (form.type==='DateTimeField'){
        R.push({required: false, message:'请选择', trigger: 'blur' })
      }
      if (form.type==='EmailField'){
        R.push({required: false, message:'请输入', trigger: 'blur' });
        R.push({type: 'email', message: '请输入正确的邮箱地址', trigger: ['blur', 'change'] })
      }
      if (form.type==='FileField'){
        R.push({required: false, message:'请上传', trigger: 'blur' })
      }
      if (form.type==='FloatField'){
        R.push({required: false, message:'请输入', trigger: 'blur' })
      }
      if (form.type==='ChoiceField'){
        R.push({required: false, message:'请选择', trigger: 'change' })
      }
      if (form.type===undefined){
        R.push({required: false, message:'请输入', trigger: 'blur' })
      }
      if (form.type==='SingleChoiceField'){
        R.push({required: false, message:'请选择', trigger: 'change' })
      }
      if (form.type==='MultipleChoiceField'){
        R.push({required: false, message:'请选择', trigger: 'change' })
      }
      if (form.type==='ArrayField'){
        R.push({required: false, message:'请输入', trigger: 'blur' })
      }

      return R
    }
  }
  
}
</script>
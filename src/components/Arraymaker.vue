<template>
	<el-form-item :label="'长度：' + comparray[index].length" label-width="90px">
		<el-row>
			<el-col :span=15>
				<el-input v-model="arrayinput"></el-input>
			</el-col>
			<el-col :span=1>
				<el-button type="danger" @click="delArray" icon="el-icon-close" plain>删除</el-button>
			</el-col>
		</el-row>
	</el-form-item>
</template>
<script>
export default{
	props:{
		'comparray':{
			'type':Array,
			'required':true
		},
		'index':{
			'type':Number,
			'required':true
		}
	},
	methods:{
		delArray(){
			this.comparray.splice(this.index,1)
		}
	},
	computed:{
		arrayinput:{
			get:function() {
				return JSON.parse(JSON.stringify(this.comparray[this.index])).join(',')
			},
      		set:function(val) {
        		this.comparray.splice(this.index,1,val ? val.split(/[,， ]/) : [])
      		}
    	}
	}
}
</script>
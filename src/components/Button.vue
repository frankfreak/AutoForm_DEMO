<template>
	<div>
		<el-button @click="startHacking">{{message.m}}</el-button>
	</div>
</template>
<script>
export default {
  props:{
    'message':{
      type: Object,
      required: true
    }},
  methods: {
    startHacking () {
      this.$notify({
        title: message.a,
        type: 'success',
        message: 'We\'ve laid the ground work for you. It\'s time for you to build something epic!',
        duration: 5000
      })
    }
  }
}
</script>
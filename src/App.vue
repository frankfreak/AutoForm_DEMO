<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>
      <Formmaker :form="form1" ></Formmaker>
    </div>
    <p>{{form1.optional[2].default}}</p>
  </div>
</template>

<script>
import Formmaker from './components/Formmaker.vue'

var data = {'form1':{
      "required":[
        {
          "id": "整型",
          "type": "IntegerField",
          "label": "年龄",
          "help_text": "请输入年龄",
          "default": "",
          "max_value": 150,
          "min_value": 0,
          "max_string_length": 8
        },
        {
          "id": "布尔",
          "type": "BooleanField",
          "label": "已婚",
          "help_text": "请选择",
          "default": ""
        },
        {
          "id": "单选",
          "type": "SingleChoiceField",
          "label": "国籍",
          "help_text": "请选择",
          "default": "",
          "choices":{
            "选择1": "中国",
            "选择2": "日本",
            "选择3": "韩国"
          }
        },
        {
          "id": "多选",
          "type": "MultipleChoiceField",
          "label": "兴趣爱好",
          "help_text": "请选择",
          "default": [],
          "choices":{
            "选择1": "唱歌",
            "选择2": "篮球",
            "选择3": "睡觉"
          }
        },
        {
          "id": "字符",
          "type": "CharField",
          "label": "姓名",
          "help_text": "请输入姓名",
          "default": '',
          "max_length": 8,
          "min_length": 2
        },
        {
          "id": "日期",
          "type": "DateField",
          "label": "出生年月",
          "help_text": "请选择日期",
          "default": ''
        },
        {
          "id": "时间",
          "type": "TimeField",
          "label": "时间",
          "help_text": "请选择时间",
          "default": ''
        },

        {
          "id": "日期时间",
          "type": "DateTimeField",
          "label": "日期时间",
          "help_text": "请选择时间和日期",
          "default": ''
        },
        {
          "id": "邮件",
          "type": "EmailField",
          "label": "邮箱地址",
          "help_text": "请输入邮箱地址",
          "default": ''
        },
        {
          "id": "文件",
          "type": "FileField",
          "label": "简历",
          "help_text": "帮助信息",
          "default": ''
        },
        {
          "id": "浮点",
          "type": "FloatField",
          "label": "工资",
          "help_text": "请输入正确的数字",
          "default": ''
        },
        {
          "id": "选择",
          "type": "ChoiceField",
          "label": "职业",
          "help_text": "请选择",
          "default":'',
          "choices": {
              "选择1": "教师",
              "选择2": "工人",
              "选择3": "军人"
            }
        },
        {
          "id":"id1",
          "label":"label1",
          "default":"",
          "help_text":"id1的信息"
        },
        {
          "id":"id2",
          "label":"label2",
          "default":"",
          "help_text":"id2的信息",
          "type":"ChoiceField",
          "choices":{
            "选择1": "444",
            "选择2": "666"
          }
        }],
        "optional":[
        {
          "id": "整型1",
          "type": "IntegerField",
          "label": "年龄",
          "help_text": "请输入年龄",
          "default": "",
          "max_value": 150,
          "min_value": 0,
          "max_string_length": 8
        },
        {
          "id": "文本1",
          "type": "TextField",
          "label": "意见",
          "default": "",
          "help_text":"请留下您宝贵的意见..",
          "max_length":50

        },
        {
          "id":"数组1",
          "type":"ArrayField",
          "label":"数组",
          "default":[[1,2,3],[3,4,5]],
          "help_text":"请输入"
        }]
      }}
export default {
  name: 'App',
  data(){
    return data
  },
  components:{
    'Formmaker': Formmaker
  }
}

</script>

<style>
#app {
  padding: 10px 10px;
  width: 80%;
  margin: auto;
  margin-top: 20px;
  font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",'Arial','sans-serif';
        }
</style>
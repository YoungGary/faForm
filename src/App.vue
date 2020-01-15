<template>
  <div id="app">
    <i-form :model="formModel" :rules="ruleValidate" ref="form">
      <i-form-item label="用户名" prop="username">
        <i-input v-model="formModel.username"></i-input>
      </i-form-item>
      <i-form-item label="密码" prop="password">
        <i-input type="password" v-model="formModel.password"></i-input>
      </i-form-item>
    </i-form>
     <button @click="handleSubmit">提交</button>
        <button @click="handleReset">重置</button>
  </div>
</template>

<script>
  import iForm from './components/form.vue';
   import iFormItem from './components/formItem.vue';
  import iInput from './components/input.vue';

export default {
  name: 'app',
  components: {
      iInput,iFormItem,iForm
  },
  data(){
    return{
        formModel:{
           username: '',
           password: ''
        },
        ruleValidate: {
          username: [
            { required: true, message: '用户名不能为空', trigger: 'blur' }
          ],
          password: [
            { required: true, message: '密码不能为空', trigger: 'blur' }
          ],
        }
    }
  },
  mounted(){
  },
  methods:{
       handleSubmit () {
            this.$refs.form.validate((valid) => {
                if (valid) {
                    window.alert('提交成功');
                } else {
                    window.alert('表单校验失败');
                }
            })
        },
        handleReset () {
            this.$refs.form.resetFields();
        }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

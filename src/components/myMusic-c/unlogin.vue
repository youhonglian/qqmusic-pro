<!--<template>
  <div class="dialog-login">    
      <el-dialog title="立即登录" :visible.sync="dialogFormVisible">
         <el-form :model="ruleForm2" status-icon :rules="rules2" ref="ruleForm2" label-width="100px" class="demo-ruleForm">
            <el-form-item label="用户名" prop="username" >
                <el-input v-model.number="ruleForm2.username" placeholder="请输入账号"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input type="password" v-model="ruleForm2.password" auto-complete="off"  placeholder="请输入密码" @keyup.enter.native="submitForm('ruleForm2')"></el-input>
            </el-form-item>                           
            <el-form-item class="el-form-item-buttom">
                <el-button type="primary" @click="submitForm('ruleForm2')" style="backgroundColor:#31c27c">登录</el-button>
                <el-button @click="resetForm('ruleForm2')">重置</el-button>
            </el-form-item>
        </el-form>
      </el-dialog>
  </div>
</template>

<script>
export default {
    data() {
      var checkName = (rule, value, callback) => {
        if (!value) {
          return callback(new Error('用户名不能为空'));
        }
        callback();
     
      };
      var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请输入密码'));
        } 
       callback();
       
      };
      return {
        dialogFormVisible: this.$store.state.dialogFormVisible,
        ruleForm2: {
          username: '',
          password: ''
        },
        rules2: {
          username: [
            { validator: checkName, trigger: 'blur' }
          ],
          password: [
            { validator: validatePass, trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      signIn() {
        alert("dsfsdf")
      },
      open() {
        const h = this.$createElement;
         this.$notify.info({
          message: '用户名或密码错误',
          showClose: false
        });
      },
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {                 
        if (valid) {
          let that = this        
          this.axios.get(`http://127.0.0.1:3000/login/cellphone?phone=${this.ruleForm2.username}&password=${this.ruleForm2.password}`).then((response) => {
              console.log(response)
              if(response.data.code == 200 && response.data.loginType == 1) {
                sessionStorage.username = this.ruleForm2.username
                alert("登录成功")
                this.$store.state.isLogin = true
                } else {
                  that.open()
                }
             }).catch((error) => {
                that.open()                
             })   
        } else {
            that.open()
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();   
      }
    }
    
}
</script>

<style lang="scss" scoped>
@import "./unlogin.scss";
</style>-->

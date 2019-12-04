<template>
    <div class="login_container">
        <div class="login_box">
            <div class="avatar_box">
                <img src="../assets/logo.png">
            </div>
            <el-form ref="loginFormRef" class="login_form" v-bind:model="loginForm" :rules="rules">
                <el-form-item prop="username">
                    <el-input prefix-icon="el-icon-user" v-model="loginForm.username"></el-input>
                </el-form-item>
                <el-form-item prop="password">
                    <el-input prefix-icon="el-icon-lock" v-model="loginForm.password" type="password"></el-input>
                </el-form-item>
                <el-form-item class="btns">
                    <el-button type="success" plain @click="submit">提交</el-button>
                    <el-button type="info" plain @click="reset('loginForm')">重置</el-button>
                </el-form-item>
            </el-form>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            loginForm: {
                username: '',
                password: ''
            },
            rules: {
                username: [
                    { required: true, message: '请输入用户名', trigger: 'blur' },
                    { min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur' }
                ],
                password: [
                     { required: true, message: '请输入密码', trigger: 'blur' },
                     { min: 6, max: 12, message: '密码长度在 6 到 12 个字符', trigger: 'blur' }
                ]
            }
        }
    },
    methods: {
        submit() {
            this.$refs.loginFormRef.validate(
                isValid => {
                    if(!isValid) {
                        console.log("校验失败");
                        return false;
                    } else {
                        
                    }
                }
            )
        },
        reset(form) {
            this.$refs.loginFormRef.resetFields();
        }
    }
}
</script>

<style lang="less" scoped>
    .login_container{
        background-color: #2b4b6b;
        height: 100%;
    }
    .login_box{
        height: 500px;
        width: 750px;
        background-color:slategray;
        border-radius: 5px;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }
    .avatar_box{
    height: 160px;
    width: 160px;
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
    border: 1px solid white;
    border-radius: 50%;
    background-color: slategray;
    box-shadow: 0 0 10px green;
    padding: 10px;
    }
    img {
        height: 100%;
        width: 100%;
        padding: 0;
        margin: 0;
        border-radius: 50%;
        background-color:wheat;
    }
    .login_form{
        position: absolute;
        bottom: 15%;
        padding: 0 15%;
        box-sizing: border-box;
        width: 100%;
        height: 50%;
    }
    .btns{
        position:absolute;
        bottom: 0%;
        right: 15%;
    }
</style>
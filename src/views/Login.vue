<template>
    <div class="login_container">
        <div class="login_box">
            <div class="avatar_box">
                <img src="../assets/logo.png" alt />
            </div>
            <el-form :model="loginForm" :rules="rules" ref="loginFormRef">
                <el-form-item prop="user">
                    <el-input
                        prefix-icon="el-icon-user"
                        v-model="loginForm.user"
                        autocomplete="off"
                    ></el-input>
                </el-form-item>
                <el-form-item prop="pass">
                    <el-input
                        type="password"
                        prefix-icon="el-icon-lock"
                        v-model="loginForm.pass"
                        autocomplete="off"
                    ></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="login('loginFormRef')">提交</el-button>
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
                user: 'admin',
                pass: '123456'
            },
            rules: {
                user: [
                    {
                        required: true,
                        message: '请输入登录名称',
                        trigger: 'blur'
                    }
                ],
                pass: [
                    {
                        required: true,
                        message: '请输入登录密码',
                        trigger: 'blur'
                    }
                ]
            }
        }
    },
    methods: {
        login(formName) {
            this.$refs[formName].validate(valid => {
                if (!valid) return
                if (
                    this.loginForm.user != 'admin' &&
                    this.loginForm.pass != '123456'
                )
                    return this.$message.error('登录失败!')
                this.$message.success('登录成功')
                // token 只应在当前网站打开期间生效，所以最好保存在 sessionStorage 中
                window.sessionStorage.setItem('token', 'tongwudi')
                this.$router.push('/home')
            })
        }
    }
}
</script>

<style lang="less" scoped>
.login_container {
    background-color: #2b4b6b;
    height: 100%;
    position: relative;
}

.login_box {
    width: 450px;
    height: 300px;
    background-color: #fff;
    border-radius: 5px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    .avatar_box {
        width: 120px;
        height: 120px;
        padding: 10px;
        border: 1px solid #eee;
        border-radius: 50%;
        box-shadow: 0 0 10px #ddd;
        background-color: #fff;
        position: absolute;
        left: 50%;
        transform: translate(-50%, -50%);
        img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background-color: #eee;
        }
    }
}

.el-form {
    padding: 0 50px;
    padding-top: 100px;
}

.el-button {
    width: 100%;
}
</style>
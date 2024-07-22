<template>
    <el-row justify="center" align="middle" class="login">
        <el-col :xs="22" :sm="14" :md="10" :lg="8" :xl="6">
            <el-card style="padding: 32px;">
                <h2 style="text-align: center;">注册页面</h2>
                <el-form label-position="top">
                    <el-form-item label="账号">
                        <el-input v-model="form.username"></el-input>
                    </el-form-item>
                    <el-form-item label="昵称">
                        <el-input v-model="form.nickname"></el-input>
                    </el-form-item>
                    <el-form-item label="密码">
                        <el-input v-model="form.password" type="password" show-password></el-input>
                    </el-form-item>
                    <el-form-item label="确认密码">
                        <el-input v-model="form.repassword" type="password" show-password></el-input>
                    </el-form-item>
                    <el-form-item label="手机号">
                        <el-input v-model="form.tel"></el-input>
                    </el-form-item>
                    <el-form-item>
                        <el-button type="success" style="width: 100%;" @click="register">注&nbsp;册</el-button>
                    </el-form-item>
                    <el-link type="primary" style="float: right;" @click="$router.back()">已有账号？立即登录</el-link>
                </el-form>
            </el-card>
        </el-col>
    </el-row>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'
import { useRouter } from 'vue-router';
const router = useRouter()

const form = ref({
    username: '',
    nickname: '',
    password: '',
    repassword: '',
    tel: ''
})

async function register() {
    const res = await axios.post('http://localhost:8000/register', {
        data: {
            username: form.value.username,
            nickname: form.value.nickname,
            password: form.value.password,
            repassword: form.value.repassword,
            tel: form.value.tel,
        }
    })
    const data = res.data
    if (data.code == 0) {
        if (data.msg != '') {
            ElMessage({
                message: data.msg,
                type: 'success',
            })
        }
        router.push({ name: 'login' })
    }
    if (data.code != 0) {
        ElMessage({
            message: data.msg,
            type: 'error',
        })
    }
}
</script>

<style scoped>
.login {
    height: 100vh;
    background-image: url('http://localhost:8000/static/assets/bg.jpg');
}
</style>
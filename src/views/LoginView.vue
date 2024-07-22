<template>
    <el-row justify="center" align="middle" class="login">
        <el-col :xs="22" :sm="14" :md="10" :lg="8" :xl="6">
            <el-card style="padding: 32px;">
                <h2 style="text-align: center;">登录页面</h2>
                <el-form label-position="top">
                    <el-form-item label="账号">
                        <el-input v-model="form.username"></el-input>
                    </el-form-item>
                    <el-form-item label="密码">
                        <el-input v-model="form.password" type="password" show-password></el-input>
                    </el-form-item>
                    <el-form-item>
                        <el-button type="success" style="width: 100%;" @click="login">登&nbsp;录</el-button>
                    </el-form-item>
                    <el-link type="primary" style="float: right;"
                        @click="$router.push({ name: 'register' })">还没有账号？立即注册</el-link>
                </el-form>
            </el-card>
        </el-col>
    </el-row>
</template>

<script setup>
import axios from 'axios';
import { ElMessage } from 'element-plus';
import { ref } from 'vue'
import { useRouter } from 'vue-router';

const form = ref({
    username: '',
    password: ''
})

const router = useRouter()

async function login() {
    const res = await axios.post("http://localhost:8000/login", {
        data: {
            username: form.value.username,
            password: form.value.password
        }
    })
    const data = res.data
    if (data.code == 0) {
        if (data.msg != '') {
            ElMessage({
                message: data.msg,
                type: 'success'
            })
        }
        router.push({ name: 'home' })
    } else {
        ElMessage({
            message: data.msg,
            type: 'error'
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
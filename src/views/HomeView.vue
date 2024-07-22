<template>
    <el-container>
        <el-header>
            <el-row align="middle" justify="center">
                <el-space :size=10>
                    <img style="height: 80px;width: 80px;" :src='logo' />
                    <el-input v-model="input" style="width: 450px;height: 40px;" placeholder="Please input" />
                
                <el-button style="width: 50px;height: 40px;" :icon="Search" />
                
                <router-link to="/register"><el-button plain>注册</el-button></router-link>
               
                <router-link to="/login"><el-button plain>登录</el-button></router-link>
            </el-space>
            </el-row>
        </el-header>

        <el-main>
            <br><br><br>
            <el-row justify="center">
                <el-space :size=15>
                    <el-card :body-style="{ padding: '5px' }" v-for="i in 4" style="width: 300px;text-align: center;">
                        <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png"
                            style="width: 100%" />
                        <el-text style="font-size: 30px;">456</el-text>
                    </el-card>
                </el-space>
            </el-row>
            <br> <br>
            <el-row justify="center">
                <el-button style="height: 45px;width:90px;font-size: 20px;" plain>更多</el-button>
            </el-row>
        </el-main>
        <el-footer>
            <el-divider />
            <el-row justify="center">
                <el-text>社区二手交易平台</el-text>        
            </el-row>
            <el-row justify="center">            
                <el-text>社区服务|联系电话|权益保障</el-text>
            </el-row>
        </el-footer>
    </el-container>
</template>

<script setup>
import logo from '../assets/logo.jpg'
import { ref } from 'vue'
import { Search } from '@element-plus/icons-vue'
const input = ref('')


</script>








  
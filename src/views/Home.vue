<template>
    <el-container class="home-container">
        <!-- 左侧菜单 -->
        <el-aside :width="isCollapse ? '64px' : '200px'">
            <div class="logo"></div>
            <el-menu
                class="menu"
                :default-active="activePath"
                background-color="#313743"
                text-color="#fff"
                active-text-color="#ffd04b"
                unique-opened
                router
                :collapse-transition="false"
                :collapse="isCollapse"
            >
                <menu-tree :menus="menuList" />
            </el-menu>
        </el-aside>
        <!-- 右侧主体 -->
        <el-container>
            <!-- 头部 -->
            <el-header>
                <i
                    :class="[isCollapse ? 'el-icon-s-unfold' : 'el-icon-s-fold' , 'trigger']"
                    @click="isCollapse = !isCollapse"
                ></i>
            </el-header>
            <!-- 内容 -->
            <el-main>
                <!-- 路由占位符 -->
                <router-view></router-view>
            </el-main>
        </el-container>
    </el-container>
</template>

<script>
import menuTree from '../components/menuTree'
export default {
    data() {
        return {
            activePath: '',
            isCollapse: false,
            menuList: [
                { id: 1, name: '首页', path: '/welcome' },
                {
                    id: 2,
                    name: '用户管理',
                    path: '',
                    children: [{ id: 3, name: '用户列表', path: '/users' }]
                },
                {
                    id: 4,
                    name: '权限管理',
                    path: '',
                    children: [
                        { id: 5, name: '权限配置', path: '/power' },
                        {
                            id: 6,
                            name: '权限配置',
                            path: '',
                            children: [{ id: 7, name: '111', path: '/222' }]
                        }
                    ]
                }
            ],
            breadArr: []
        }
    },
    mounted() {
        this.activePath = this.$route.path
    },
    beforeUpdate() {
        this.activePath = this.$route.path
    },
    components: {
        menuTree
    }
}
</script>

<style lang="less" scoped>
.home-container {
    height: 100%;
}

.el-header {
    padding-left: 0;
    background-color: #363d40;
    color: #fff;
    .trigger {
        font-size: 20px;
        padding: 0 20px;
        line-height: 60px;
        cursor: pointer;
        &:hover {
            color: #1890ff;
        }
    }
}

.el-aside {
    background-color: #313743;
    color: #fff;
    .logo {
        height: 60px;
        background-image: url('../assets/logo.png');
        background-size: cover;
    }
}

.el-menu {
    border-right-color: #313743;
}

.el-main {
    background-color: #e9edf1;
}
</style>
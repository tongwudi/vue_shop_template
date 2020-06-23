<template>
    <el-container class="home-container">
        <!-- 左侧菜单 -->
        <el-aside :width="isCollapse ? '64px' : '200px'">
            <div class="logo"></div>
            <el-menu
                default-active="1"
                background-color="#313743"
                text-color="#fff"
                active-text-color="#ffd04b"
                :unique-opened="true"
                :collapse-transition="false"
                :collapse="isCollapse"
            >
                <el-menu-item index="1">
                    <i class="el-icon-s-home"></i>
                    <span slot="title">首页</span>
                </el-menu-item>
                <el-submenu index="2">
                    <template slot="title">
                        <i class="el-icon-location"></i>
                        <span>导航一</span>
                    </template>
                    <el-menu-item-group>
                        <template slot="title">分组一</template>
                        <el-menu-item index="2-1">选项1</el-menu-item>
                        <el-menu-item index="2-2">选项2</el-menu-item>
                    </el-menu-item-group>
                    <el-menu-item-group title="分组2">
                        <el-menu-item index="2-3">选项3</el-menu-item>
                    </el-menu-item-group>
                    <el-submenu index="2-4">
                        <template slot="title">选项4</template>
                        <el-menu-item index="2-4-1">选项1</el-menu-item>
                    </el-submenu>
                </el-submenu>
                <el-submenu index="3">
                    <template slot="title">
                        <i class="el-icon-location"></i>
                        <span>导航二</span>
                    </template>
                    <el-menu-item-group>
                        <template slot="title">分组一</template>
                        <el-menu-item index="3-1">选项1</el-menu-item>
                        <el-menu-item index="3-2">选项2</el-menu-item>
                    </el-menu-item-group>
                    <el-menu-item-group title="分组2">
                        <el-menu-item index="3-3">选项3</el-menu-item>
                    </el-menu-item-group>
                    <el-submenu index="3-4">
                        <template slot="title">选项4</template>
                        <el-menu-item index="3-4-1">选项1</el-menu-item>
                    </el-submenu>
                    <el-submenu index="3-5">
                        <template slot="title">选项5</template>
                        <el-menu-item index="3-5-1">选项1</el-menu-item>
                    </el-submenu>
                </el-submenu>
                <el-menu-item index="4">
                    <i class="el-icon-location"></i>
                    <span slot="title">导航三</span>
                </el-menu-item>
                <el-menu-item index="5">
                    <i class="el-icon-setting"></i>
                    <span slot="title">导航四</span>
                </el-menu-item>
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
            <el-main>Main</el-main>
        </el-container>
    </el-container>
</template>

<script>
export default {
    data() {
        return {
            isCollapse: false
        }
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

.el-main {
    background-color: #e9edf1;
}


.el-menu {
    border-right-color: #313743;
}
</style>
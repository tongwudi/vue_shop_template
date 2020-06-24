<template>
    <div>
        <template v-for="menu in menus">
            <el-submenu v-if="menu.children" :index="menu.id + ''" :key="menu.id">
                <template slot="title">
                    <i class="el-icon-location" v-if="menu.path == ''"></i>
                    <span>{{ menu.name }}</span>
                </template>
                <menu-tree :menus="menu.children" />
            </el-submenu>
            <el-menu-item v-else :index="menu.path" :key="menu.id">
                <i class="el-icon-location"></i>
                <span slot="title">{{ menu.name }}</span>
            </el-menu-item>
        </template>
    </div>
</template>

<script>
export default {
    name: 'menuTree',
    props: {
        menus: Array
    }
}
</script>

<style lang="less" scoped>
.el-menu--collapse .el-submenu__title span {
    display: none;
}
.el-menu--collapse .el-submenu__title .el-submenu__icon-arrow {
    display: none;
}
</style>
<template>
  <div>
    <el-button @click="logOut">退出</el-button>
  </div>
</template>

<script>
export default {
    methods: {
        logOut() {
            window.sessionStorage.clear('token')
            this.$router.push('/login')
            this.$message.success('退出成功')
        }
    }
}
</script>

<style lang="less" scoped>
</style>
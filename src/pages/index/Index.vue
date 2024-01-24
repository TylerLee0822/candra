<template>
    <a-layout style="min-height: 100vh">
        <a-layout-sider :style="siderStyle" style="background: #fff">Sider</a-layout-sider>
        <a-layout-content :style="contentStyle">Content</a-layout-content>
        <a-layout-sider :style="siderStyle" style="background: #fff">Sider</a-layout-sider>
    </a-layout>
</template>
  
<script>
export default {
    name: 'Index'
}
</script>
  
<style ></style>
  
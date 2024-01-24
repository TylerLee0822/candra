<template>
    <a-layout style="min-height: 100vh">
        <a-layout-sider :style="siderStyle" style="background: #fff">Sider</a-layout-sider>
        <a-layout-content :style="contentStyle">
            <canvas id="canvas"></canvas>
        </a-layout-content>
        <a-layout-sider :style="siderStyle" style="background: #fff">Sider</a-layout-sider>
    </a-layout>
</template>
  
<script>
// import { fabric } from 'fabric';
// import Editor from '.core';
// const canvas = {};

export default {
    name: 'Index',
}




</script>
  
<style>
#canvas {
    width: 100%;
    height: 100%;
}
</style>
  
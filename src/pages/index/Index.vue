<template>
    <a-layout style="min-height: 100vh">
        <a-layout-sider style="background: #fff">
            <tools></tools>
        </a-layout-sider>
        <a-layout-content style="overflow: hidden;">
            <div id="workspace" style="width: 100%; position: relative; background: #f1f1f1">
                <canvas id="canvas"></canvas>
                <zoom></zoom>
                <mouseMenu></mouseMenu>
            </div>

        </a-layout-content>
        <a-layout-sider style="background: #fff">
            <setSize></setSize>
        </a-layout-sider>
    </a-layout>
</template>
  
<script>

// 左侧组件
import tools from './components/tools.vue';
import setSize from './components/setSize.vue';

import zoom from './components/zoom.vue';
import EditorWorkspace from './core/EditorWorkspace';
// 右键菜单
import mouseMenu from './components/contextMenu/index.vue';

// 功能组件
import EventHandle from './utils/eventHandler';

import { fabric } from 'fabric';
import Editor from './core';

const event = new EventHandle();
const canvas = {};

export default {
    name: 'Index',
    provide: {
        canvas,
        fabric,
        event,
    },
    data() {
        return {
        };
    },
    components: {
        setSize,
        tools,
        zoom,
        mouseMenu,
    },
    mounted() {
        this.canvas = new fabric.Canvas('canvas', {
            //containerClass: "canvasClass",
            fireRightClick: true, // 启用右键，button的数字为3
            stopContextMenu: true, // 禁止默认右键菜单
            controlsAboveOverlay: true, // 超出clipPath后仍然展示控制条
        });

        canvas.c = this.canvas;


        event.init(canvas.c);
        canvas.editor = new Editor(canvas.c);
        canvas.editor.editorWorkspace = new EditorWorkspace(this.canvas, {
            width: 512,
            height: 512,
        });

        canvas.c.renderAll();
    },
}




</script>
  
<style>
.canvasClass {
    border: 10px dashed green;
    background-color: white;
    margin: auto;
}
</style>
  
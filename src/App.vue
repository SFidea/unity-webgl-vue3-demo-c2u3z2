<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import UnityWebgl from 'unity-webgl';

const canvasRef = ref(null);
let unityComponent = null;

onMounted(() => {
  if (!unityComponent) {
    unityComponent = new UnityWebgl(canvasRef.value, {
      loaderUrl:
        'https://static-huariot-com.oss-cn-hangzhou.aliyuncs.com/unity/test1/Build/OUT_BIM.loader.js',
      dataUrl:
        'https://static-huariot-com.oss-cn-hangzhou.aliyuncs.com/unity/test1/Build/OUT_BIM.data',
      frameworkUrl:
        'https://static-huariot-com.oss-cn-hangzhou.aliyuncs.com/unity/test1/Build/OUT_BIM.framework.js',
      codeUrl:
        'https://static-huariot-com.oss-cn-hangzhou.aliyuncs.com/unity/test1/Build/OUT_BIM.wasm',
    });
  }
});
onBeforeUnmount(() => {
  if (unityComponent) {
    unityComponent.destroy();
    unityComponent = null;
  }
});
</script>

<template>
  <div style="width: 800px; height: 600px; border: 1px solid #f00">
    <canvas id="canvas" ref="canvasRef" style="width: 100%; height: 100%" />
  </div>
</template>

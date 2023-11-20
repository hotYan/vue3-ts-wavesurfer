<template>
  <zyAudio
    ref="audioRef"
    :wavesurfer-options="wavesurferOptions"
    :show-hover="hasHover"
    :hover-options="hoverOptions"
    :show-timeline="hasTimeLine"
    :timeline-options="timeLineOptions"
    :show-minimap="hasMiniMap"
    :minimap-options="miniMapOptions"
    :show-regions="hasRegions"
    :show-spectrogram="hasSpectrogram"
    :showAudio="hasAudio"
  ></zyAudio>
  <el-switch
    v-model="hasHover"
    inline-prompt
    style="--el-switch-on-color: #13ce66; --el-switch-off-color: #ff4949"
    active-text="引入 Hover 插件"
    inactive-text="不引入 Hover 插件"
  ></el-switch>
  <el-switch
    v-model="hasTimeLine"
    inline-prompt
    style="--el-switch-on-color: #13ce66; --el-switch-off-color: #ff4949"
    active-text="引入 TimeLine 插件"
    inactive-text="不引入 TimeLine 插件"
  ></el-switch>
  <el-switch
    v-model="hasMiniMap"
    inline-prompt
    style="--el-switch-on-color: #13ce66; --el-switch-off-color: #ff4949"
    active-text="引入 MiniMap 插件"
    inactive-text="不引入 MiniMap 插件"
  ></el-switch>
  <el-switch
    v-model="hasRegions"
    inline-prompt
    style="--el-switch-on-color: #13ce66; --el-switch-off-color: #ff4949"
    active-text="引入 Regions 插件"
    inactive-text="不引入 Regions 插件"
  ></el-switch>
  <el-switch
    v-model="hasSpectrogram"
    inline-prompt
    style="--el-switch-on-color: #13ce66; --el-switch-off-color: #ff4949"
    active-text="引入 Spectrogram 插件"
    inactive-text="不引入 Spectrogram 插件"
  ></el-switch>
  <el-switch
    v-model="hasAudio"
    inline-prompt
    style="--el-switch-on-color: #13ce66; --el-switch-off-color: #ff4949"
    active-text="引入 Audio 控制条"
    inactive-text="不引入 Audio 控制条"
  ></el-switch>
</template>

<script setup lang="ts">
import zyAudio from './Audio.vue'
import { ref, watch } from 'vue'
const audioRef = ref()
let hasHover = ref(true)
const hasTimeLine = ref(false)
const hasMiniMap = ref(false)
const hasRegions = ref(false)
const hasSpectrogram = ref(false)
const hasAudio = ref(true)
const wavesurferOptions = ref({
  progressColor: 'paleturquoise',
  cursorColor: '#57BAB6',
  cursorWidth: 4,
  autoplay: false,
  autoCenter: true,
  minPxPerSec: 100,
})
const hoverOptions = ref()
const timeLineOptions = ref()
const miniMapOptions = ref()
watch([hasHover, hasTimeLine, hasMiniMap, hasRegions, hasSpectrogram], () => {
  audioRef.value.initWaveSurfer()
})
</script>

<style lang="scss" scoped></style>

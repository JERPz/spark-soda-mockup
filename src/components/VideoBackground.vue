<script setup>
import { ref, watch, onMounted, onUnmounted } from 'vue'
const props = defineProps(['src', 'offset', 'sectionId', 'startTime', 'endTime'])

const videoEl = ref(null)
const opacity = ref(0)
const isReady = ref(false)

let targetTime = 0
let currentTime = 0
let rafId = null

const prefersReduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches

const updateFrame = () => {
  if (isReady.value && videoEl.value) {
    const lerpFactor = prefersReduced ? 1 : 0.02;
    currentTime += (targetTime - currentTime) * lerpFactor;

    if (currentTime < 0) currentTime = 0;
    if (currentTime > videoEl.value.duration) currentTime = videoEl.value.duration;

    videoEl.value.currentTime = currentTime;
  }
  rafId = requestAnimationFrame(updateFrame);
}

watch(() => props.offset, (newVal) => {
  const section = document.getElementById(props.sectionId)
  if (section && videoEl.value && isReady.value) {
    const progress = Math.min(Math.max((newVal - section.offsetTop) / section.clientHeight, 0), 1)
    const start = props.startTime || 0
    const duration = videoEl.value.duration
    const end = (props.endTime > 0 && props.endTime <= duration) ? props.endTime : duration
    targetTime = start + (progress * (end - start))
  }
})

watch(() => props.src, (n) => {
  if (videoEl.value) {
    if (n) {
      isReady.value = false
      currentTime = targetTime = props.startTime || 0
      videoEl.value.src = n
      videoEl.value.load()
    } else {
      videoEl.value.removeAttribute('src')
      videoEl.value.load()
      isReady.value = false
    }
  }
})

const onVideoLoaded = () => {
  if (videoEl.value) {
    videoEl.value.pause()
    isReady.value = true
    opacity.value = 1
    currentTime = targetTime = props.startTime || 0
    videoEl.value.currentTime = currentTime
  }
}

onMounted(() => updateFrame())
onUnmounted(() => cancelAnimationFrame(rafId))
</script>

<template>
  <div class="absolute inset-0 w-full h-full -z-10 bg-black overflow-hidden">
    <video v-if="src" ref="videoEl" :src="src" muted playsinline preload="auto" @loadedmetadata="onVideoLoaded"
      class="absolute inset-0 w-full h-full object-cover brightness-[0.4] transition-opacity duration-1000"
      :style="{ opacity }" />
    <div class="absolute inset-0 bg-gradient-to-b from-black/20 via-transparent to-black/80"></div>
  </div>
</template>
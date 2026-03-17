<script setup>
import { ref, computed, onMounted, onUnmounted } from "vue"
import LoadingScreen from "./components/LoadingScreen.vue"
import Navigation from "./components/Navigation.vue"
import HeroSection from "./components/HeroSection.vue"
import VideoBackground from "./components/VideoBackground.vue"
import FlavorSection from "./components/FlavorSection.vue"
import BenefitsSection from "./components/BenefitsSection.vue"
import TestimonialsSection from "./components/TestimonialsSection.vue"
import ContactSection from "./components/ContactSection.vue"

import orange from "./assets/orange.png"; import berry from "./assets/berry.png"; import lime from "./assets/lime.png"
import orangeBg from "./assets/orange-bg.mp4"; import berryBg from "./assets/berry-bg.mp4"; import limeBg from "./assets/lime-bg.mp4"

const scenes = [
  { id: "s1", title: "Orange Blast", tagline: "The Spark That Ignites", desc: "A citrus shockwave crafted with natural flavors.", image: orange, bg: orangeBg, color: "var(--color-spark-orange)", stats: { sugar: "0g", energy: "∞" }, startTime: 0.3, endTime: 4 },
  { id: "s2", title: "Berry Spark", tagline: "Electric Energy", desc: "Wild berry rush with electric fizz.", image: berry, bg: berryBg, color: "var(--color-spark-berry)", stats: { sugar: "0g", energy: "High" }, startTime: 0.3, endTime: 4 },
  { id: "s3", title: "Lime Charge", tagline: "Pure Vitality", desc: "Hyper fresh lime power surge.", image: lime, bg: limeBg, color: "var(--color-spark-green)", stats: { sugar: "0g", energy: "Extreme" }, startTime: 0.3, endTime: 4 }
]

const currentIndex = ref(0)
const bgOffset = ref(0)

const activeBg = computed(() => scenes[currentIndex.value].bg)

const stickyOpacity = computed(() => {
  const section = document.getElementById('anchor-' + currentIndex.value)
  if (!section) return 1
  const val = bgOffset.value
  const start = section.offsetTop
  const end = start + section.clientHeight
  const fadeRange = window.innerHeight * 0.3
  const fadePoint = end - fadeRange
  if (val < fadePoint) return 1
  return Math.max(0, 1 - (val - fadePoint) / fadeRange)
})

let ticking = false
const handleScroll = () => {
  if (!ticking) {
    ticking = true
    requestAnimationFrame(() => {
      bgOffset.value = window.scrollY
      ticking = false
    })
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {

      if (entry.isIntersecting) {
        currentIndex.value = parseInt(entry.target.dataset.index)
      }
    })
  }, {
    threshold: 0.1, 
    rootMargin: "-10% 0px -10% 0px"
  })

  document.querySelectorAll('.scroll-anchor').forEach(el => observer.observe(el))

  scenes.forEach(s => {
    const videoLink = document.createElement('link')
    videoLink.rel = 'preload'
    videoLink.as = 'video'
    videoLink.href = s.bg
    document.head.appendChild(videoLink)

    const imgLink = document.createElement('link')
    imgLink.rel = 'preload'
    imgLink.as = 'image'
    imgLink.href = s.image
    document.head.appendChild(imgLink)

    const img = new Image()
    img.src = s.image
  })
})

onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<template>
  <LoadingScreen />
  <Navigation />

  <div class="relative bg-black/30">
    <div id="hero">
      <HeroSection />
    </div>

    <div id="flavor" class="relative">
      <div class="sticky top-0 h-screen overflow-hidden" :style="{ opacity: stickyOpacity }">
        <VideoBackground :src="activeBg" :offset="bgOffset" :section-id="'anchor-' + currentIndex"
          :startTime="scenes[currentIndex].startTime" :endTime="scenes[currentIndex].endTime" />
        <div class="absolute inset-0 z-10 pointer-events-none flex items-center justify-center px-[8%]">
          <FlavorSection :data="scenes[currentIndex]" class="pointer-events-auto" />
        </div>
      </div>

      <div v-for="(scene, index) in scenes" :key="scene.id" :id="'anchor-' + index" :data-index="index"
        class="scroll-anchor h-[120vh] w-full relative pt-[15vh]">
      </div>
    </div>

    <div class="relative z-30 bg-black">
      <div id="features">
        <BenefitsSection />
      </div>
      <TestimonialsSection />
      <div id="contact">
        <ContactSection />
      </div>
    </div>
  </div>
</template>

<style>

html {
  scroll-behavior: smooth;
}
</style>
<template>
  <div class="wrapper">
    <section
      v-for="(panel, index) in visiblePanels"
      :key="index"
      class="panel"
      :style="getStyle(index)"
    >
      <component :is="panel" />
    </section>
  </div>
</template>

<script setup>
import { shallowRef, onMounted, ref } from 'vue'
import { animate } from 'animejs'

import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Works from './components/Works.vue'
import Contact from './components/Contact.vue'

const panels = [Hero, About, Works, Contact]

const currentIndex = ref(0)
const scale = ref(1)
const visiblePanels = shallowRef([panels[0], panels[1]])

const scrollAmount = 0.0005

function handleWheel(e) {
  const adjustedDelta = e.deltaY * multiplier
  if (adjustedDelta > 0) {
    scale.value -= scrollAmount * Math.abs(adjustedDelta)
  } else {
    scale.value += scrollAmount * Math.abs(adjustedDelta)
  }

  if (scale.value <= 0.5) {
    nextPanel()
    scale.value = 1
  }

  if (scale.value >= 1.05) {
    prevPanel()
    scale.value = 0.5
  }

  if (scale.value > 1.5) scale.value = 1.5
}

const isTouchDevice =
  'ontouchstart' in window || navigator.maxTouchPoints > 0
const multiplier = isTouchDevice ? 2 : 1
let startY = 0

function handleTouchStart(e) {
  startY = e.touches[0].clientY
}

function handleTouchMove(e) {
  const currentY = e.touches[0].clientY
  const deltaY = startY - currentY

  handleWheel({ deltaY }) // ← 疑似的にwheelイベント化

  startY = currentY
}

function nextPanel() {
  currentIndex.value =
    (currentIndex.value + 1) % panels.length

  const next =
    panels[(currentIndex.value + 1) % panels.length]

  visiblePanels.value = [
    panels[currentIndex.value],
    next
  ]
}

function prevPanel() {

  currentIndex.value =
    (currentIndex.value - 1 + panels.length) % panels.length

  const next =
    panels[(currentIndex.value + 1) % panels.length]

  visiblePanels.value = [
    panels[currentIndex.value],
    next
  ]
}

function getStyle(index) {
  if (index === 0) {
    return {
      transform: `scale(${scale.value})`,
      zIndex: 2
    }
  }

  return {
    transform: 'scale(1)',
    zIndex: 1
  }
}

onMounted(() => {
  window.addEventListener('wheel', handleWheel, {
    passive: true
  })

  window.addEventListener('touchstart', handleTouchStart, {
    passive: true
  })

  window.addEventListener('touchmove', handleTouchMove, {
    passive: true
  })
})
</script>

<style scoped>
.wrapper {
  position: relative;
  min-height: 100vh;
  width: 100vw;
  
  touch-action: pan-y;
}

.panel {
  position: absolute;
  height: 100vh;
  width: 80vw;
  left: 50%;
  top: 50%;
  transform-origin: center;
  translate: -50% -50%;
  overflow: hidden;

  padding: 80px 10vw;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #F5F5F5;
  background-size: contain;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.2);
}
</style>
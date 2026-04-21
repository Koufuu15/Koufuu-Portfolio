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
  if (e.deltaY > 0) {
    scale.value -= scrollAmount * Math.abs(e.deltaY)
  } else {
    scale.value += scrollAmount * Math.abs(e.deltaY)
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

  /*
  animate({
    targets: scale,
    value: newScale,
    duration: 300,
    easing: 'easeOutQuad'
  })
  */

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

  window.addEventListener('touchmove', handleWheel, {
    passive: true
  })
})
</script>

<style scoped>
.wrapper {
  position: relative;
  min-height: 100vh;
  width: 100vw;
  overflow: hidden;
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

  padding: 80px 10vw;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #F5F5F5;
  background-size: contain;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.2);
}
</style>
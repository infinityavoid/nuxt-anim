<script setup lang="ts">
const firstScreen = ref(null)

const scrollHeaderHandler = () => {
  let scrolled = window.scrollY
  if(scrolled > 80) {
    firstScreen.value?.classList?.add('out')
  }
  else {
    firstScreen.value?.classList?.remove('out')
  }
}

onMounted(() => {
  window.addEventListener('scroll', scrollHeaderHandler)
  window.addEventListener('resize', scrollHeaderHandler)
})
onUnmounted(() => {
  window.removeEventListener('scroll', scrollHeaderHandler)
  window.removeEventListener('resize', scrollHeaderHandler)
})
</script>

<template>
  <div ref="firstScreen" class="first-screen">
    <h2 class="first-screen__text">Hello world</h2>
  </div>
</template>

<style lang="sass">
.first-screen
  height: 600px
  transition: 2s
.first-screen.out
  height: 0
  .first-screen__text
    opacity: 0
    transform: translateY(-100px)

.first-screen__text
  padding-left: 150px
  padding-top: 100px
  opacity: 1
  transition: 1.5s
</style>
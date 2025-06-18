<template>
  <headerApp/>
  <div class="container pos-relative">
    <firstScreen/>
    <scrollSection/>
  </div>
</template>

<style lang="sass">
*,
*::after,
*::before
  padding: 0
  margin: 0
  box-sizing: border-box

//::-webkit-scrollbar
//  display: none
hr
  border: 0
body
  font-family: sans-serif
  background-color: rgb(14, 14, 14)
  color: white


.container
  max-width: 1440px
  margin-left: auto
  margin-right: auto
  padding-bottom: 50px

.pos-relative
  position: relative


</style>

<script setup>

onMounted(()=>{
  initSmoothScroll()
})
</script>

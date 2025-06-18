<script setup lang="ts">
const { title, desc } = defineProps<{ title: string, desc: string }>()
</script>

<template>
  <li class="sticky-scroll__item">
    <h2 class="sticky-scroll__item-title">{{title}}</h2>
    <p class="sticky-scroll__item-desc">{{desc}}</p>
  </li>
</template>

<style lang="sass">
.sticky-scroll__item
  list-style-type: none
  height: 100%
  position: absolute
  left: 0
  top: 0
  width: 100%
  display: grid
  grid-template-rows: repeat(2, 50%)
  grid-template-columns: repeat(2, 50%)

.sticky-scroll__item-title
  text-align: right
  padding-right: 30px
  padding-bottom: 30px
  align-content: flex-end
  font-size: 40px
  opacity: 0
  transition: 0.5s
  transition-delay: 0.5s

.sticky-scroll__item-desc
  padding-left: 30px
  padding-top: 30px
  grid-row: 2
  grid-column: 2
  font-size: 24px
  opacity: 0
  transition: 0.5s
  transition-delay: 0.5s

.sticky-scroll__item.active
  .sticky-scroll__item-title, .sticky-scroll__item-desc
    opacity: 1
</style>
<script setup lang="ts">

</script>

<template>
  <header ref="headerElement">
    <div class="header-main">
      <h3>Так называемая шапка</h3>
    </div>
  </header>
</template>

<style lang="sass">
header
  position: sticky
  height: auto
  display: flex
  flex-direction: column
  top: 0
  z-index: 1
  background-color: rgb(14, 14, 14)
.header-main
  height: 80px
  border-bottom: 1px solid #ffffff26
  padding: 0 40px
  align-items: center
  display: flex
  z-index: 1
</style>
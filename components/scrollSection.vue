<script setup lang="ts">
const scrollSection = ref(null)
const stickyScroll = ref(null)
const data = [
  {
    title:'Welcome',
    desc:'To animprac'
  },
  {
    title:'Scroll',
    desc:'Example'
  },
  {
    title:'he-he',
    desc:'ha-ha'
  },
  {
    title:'choo-choo',
    desc:'ho-ho'
  }
]

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  window.addEventListener('resize', handleScroll)
})
onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  window.removeEventListener('resize', handleScroll)
})

const activeIndex = ref(null); // null - значит, ни один элемент не активен

const handleScroll = () => {
  if (!scrollSection.value) return;

  const numItems = data.length;
  const sectionHeight = scrollSection.value.offsetHeight / numItems;
  const scrollTop = window.scrollY || document.documentElement.scrollTop || document.body.scrollTop || 0;

  const scrollSectionOffsetTop = scrollSection.value.offsetTop;
  const scrollSectionHeight = scrollSection.value.offsetHeight;

  const isInView = (scrollTop >= scrollSectionOffsetTop) && (scrollTop <= (scrollSectionOffsetTop + scrollSectionHeight));

  if (isInView) {
    const relativeScrollTop = scrollTop - scrollSectionOffsetTop;
    const activeIndexValue = Math.floor(relativeScrollTop / sectionHeight);
    activeIndex.value = Math.max(0, Math.min(activeIndexValue, numItems - 1));
  } else {
    activeIndex.value = null;
  }
};
</script>

<template>
  <div class="scroll-section pos-relative" ref="scrollSection" :style="`--items: ${data.length};`">
    <div class="sticky-scroll" ref="stickyScroll">
      <ul class="sticky-scroll__list pos-relative">
        <hr :class="{'active' : activeIndex !== null}" class="line-vertical">
        <hr :class="{'active' : activeIndex !== null}" class="line-horizontal">
        <scrollSectionItem
            v-for="(item, index) in data"
            :title="item.title"
            :desc="item.desc"
            :class="{ 'active' : index === activeIndex }"/>
      </ul>
    </div>
  </div>
</template>

<style lang="sass">
.scroll-section
  height: calc(var(--items) * 200vh)
.sticky-scroll
  position: sticky
  top: 80px
  display: flex
  height: 100vh
.sticky-scroll__list
  width: 100%
  height: calc(100% - 80px)
  border-bottom: 1px solid #ffffff26
.line-vertical
  position: absolute
  top: 0
  left: 50%
  width: 1px
  height: 100%
  background: #ffffff26
  transform: scale(1, 0)
  display: block
  transition: all 2s
.line-horizontal
  position: absolute
  top: 50%
  left: 0
  margin: 0
  height: 1px
  background: #ffffff26
  transform: scale(0, 1)
  display: block
  transition: all 2s
  width: 100%
.line-horizontal.active
  transform: scale(1, 1)
.line-vertical.active
  transform: scale(1, 1)
</style>
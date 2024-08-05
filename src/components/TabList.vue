<script setup>
import { ref, watch } from 'vue';

defineProps({
  tabList: Array,
});

const currentIndex = ref(0);
const tabListRef = ref();
watch(currentIndex, (newVal) => {
  const tabList = tabListRef;
  const tab = tabList.value.children[newVal];
  const tabRect = tab.getBoundingClientRect();
  const scrollLeft = tab.offsetLeft + tabRect.width / 2 - window.innerWidth / 2;
  tabList.value.scrollLeft = scrollLeft;
});

const onTabClick = (index) => {
  currentIndex.value = index;
};
</script>

<template>
  <div class="tab-list" ref="tabListRef">
    <div
      v-for="(item, index) in tabList"
      :key="item"
      :class="index === currentIndex ? 'active-item' : 'tab-item'"
      @click="onTabClick(index)"
    >
      {{ item }}
    </div>
  </div>
</template>

<style scoped>
.tab-list {
  display: flex;
  width: 100%;
  flex-wrap: nowrap;
  overflow-x: scroll;
  .tab-item,
  .active-item {
    flex: 1;
    flex-shrink: 0;
    flex-basis: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 200px;
    height: 40px;
    border-right: 1px solid #000;
    font-size: 16px;
    background-color: #8ce397;
  }
  .active-item {
    background-color: #f93c7d;
  }
}
</style>

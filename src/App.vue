<script setup>
import { ref, nextTick, onMounted } from 'vue';
import TabList from './components/TabList.vue';

const tabList = ref([
  'Tab1',
  'Tab2',
  'Tab3',
  'Tab4',
  'Tab5',
  'Tab6',
  'Tab7',
  'Tab8',
  'Tab9',
]);
const childTabList = ref();

onMounted(async () => {
  await nextTick();
  childTabList.value.onTabClick(4);
});
</script>

<template>
  <div id="app">
    <TabList :tabList="tabList" ref="childTabList" />
  </div>
</template>

<style scoped></style>

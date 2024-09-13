<script lang="ts" setup>
import { ref } from 'vue';
import { zhTW } from 'date-fns/locale';
import VueDatePicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css';

const date = ref(new Date());

const format = (date: Date) => {
  const day = date.getDate();
  const month = date.getMonth() + 1;
  const year = date.getFullYear() - 1911;

  return `民國 ${year} 年 ${month} 月 ${day} 日`;
};

console.log('Date:', date.value);
</script>

<template>
  <div class="p-4 mx-auto prose md:px-6 prose-indigo sm:rounded-md">
    <h2>Datepicker Demo Page</h2>

    <p>
      <router-link to="/"> Back to home </router-link>
    </p>
    <VueDatePicker v-model="date" :format="format" :format-locale="zhTW" year-first >
      <template #year="{ value }">
        <span>民國 {{ value - 1911 }} 年</span>
      </template>
      <template #year-overlay-value="{ text }">
        <span>{{ Number(text) - 1911 }}</span>
      </template>
    </VueDatePicker>
  </div>
</template>

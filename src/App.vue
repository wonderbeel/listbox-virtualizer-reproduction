<script setup>
import { ref } from 'vue';
import Listbox from './components/Listbox.vue';

const withHeightItems = ref(0);
const withoutHeightItems = ref(0);

setTimeout(() => {
  const virtualWithHeight = document.querySelector(
    '#with-height [data-radix-vue-virtualizer]'
  );
  const virtualWithoutHeight = document.querySelector(
    '#without-height [data-radix-vue-virtualizer]'
  );
  withHeightItems.value = virtualWithHeight.childElementCount;
  withoutHeightItems.value = virtualWithoutHeight.childElementCount;
}, 1000);
</script>

<template>
  <div style="display: flex; gap: 2rem">
    <div style="width: 500px" id="with-height">
      <p>With Height</p>
      <Listbox :with-height="true" />
    </div>

    <div style="width: 500px" id="without-height">
      <p>Without Height</p>
      <Listbox :with-height="false" />
    </div>

    <div style="width: 500px">
      <p>With height items: {{ withHeightItems }}</p>
      <p>Without height items: {{ withoutHeightItems }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import {
  ListboxContent,
  ListboxFilter,
  ListboxItem,
  ListboxRoot,
  ListboxVirtualizer,
} from 'radix-vue';
import { faker } from '@faker-js/faker';

const props = defineProps<{ withHeight: boolean }>();

const people = faker.helpers.multiple(
  () => ({
    name: faker.person.fullName(),
  }),
  { count: 1000 }
);
</script>

<template>
  <ListboxRoot>
    <ListboxContent
      :style="props.withHeight ? 'height: 500px; overflow: scroll' : ''"
    >
      <ListboxVirtualizer
        v-slot="{ option }"
        :options="people"
        :text-content="(opt) => opt.name"
      >
        <ListboxItem :value="option">
          {{ option.name }}
        </ListboxItem>
      </ListboxVirtualizer>
    </ListboxContent>
  </ListboxRoot>
</template>

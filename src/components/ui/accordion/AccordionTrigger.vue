<script setup lang="ts">
import { cn } from "@/lib/utils";
import { ChevronDown } from "lucide-vue-next";
import {
  AccordionHeader,
  AccordionTrigger,
  type AccordionTriggerProps,
} from "reka-ui";
import { computed, type HTMLAttributes } from "vue";

const props = defineProps<
  AccordionTriggerProps & { class?: HTMLAttributes["class"] }
>();

const delegatedProps = computed(() => {
  const { class: _, ...delegated } = props;

  return delegated;
});
</script>

<template>
  <AccordionHeader class="flex">
    <AccordionTrigger
      v-bind="delegatedProps"
      :class="
        cn(
          'flex flex-1 items-center justify-between py-4 text-sm font-medium transition-all [&[data-state=open]>svg]:rotate-180 focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-zinc-950 dark:focus-visible:ring-zinc-300 rounded-md',
          props.class
        )
      "
    >
      <slot />
      <slot name="icon">
        <ChevronDown
          class="h-4 w-4 shrink-0 text-zinc-500 transition-transform duration-200 dark:text-zinc-400"
        />
      </slot>
    </AccordionTrigger>
  </AccordionHeader>
</template>

<script setup>
const props = defineProps({
  class: String,
  onClick: Function,
});
</script>

<template>
  <button :class="`${props.class}`" @click="props.onClick">
    <slot>{{ "Button" }}</slot>
  </button>
</template>

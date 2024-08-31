<template>
  <div ref="reactRoot"></div>
</template>

<script setup>
import { createRoot } from 'react-dom/client';
import { onBeforeUnmount, onMounted, ref } from 'vue';

const props = defineProps({
  component: Object,
  componentProps: Object
});

const reactRoot = ref(null);
let root = null;

onMounted(() => {
  root = createRoot(reactRoot.value);
  root.render(<props.component {...props.componentProps} />);
});

onBeforeUnmount(() => {
  if (root) {
    root.unmount();
  }
});
</script>

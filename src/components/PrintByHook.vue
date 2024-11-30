<script setup lang="ts">
// #region script
import { useVueToPrint } from 'vue-to-print';
import { reactive, ref } from 'vue';
import ComponentToPrint from './ComponentToPrint.vue';

const componentRef = ref();
const state = reactive({ text: 'old boring text' });

const { handlePrint } = useVueToPrint({
  content: componentRef,
  documentTitle: 'AwesomeFileName',
  removeAfterPrint: true,
  print: (target) => console.log(target),
});
// #endregion script
</script>

// #region template
<template>
  <button @click="handlePrint">Print</button>
  <div ref="componentRef">
    <component-to-print :text="state.text" />
  </div>
</template>

<style scoped></style>
// #endregion template

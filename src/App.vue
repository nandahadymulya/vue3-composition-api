<script>
import { ref, reactive, toRefs, computed } from "vue";

export default {
  setup() {
    const counter = reactive({
      value: 0,
    });

    const addNum = ref(1);

    const increment = () => {
      result.value = 5;
      counter.value++;
    };

    const result = computed({
      get: () => counter.value + addNum.value,
      set: (val) => (addNum.value = val),
    });

    return {
      ...toRefs(counter),
      increment,
      result,
    };
  },
};
</script>

<template>
  <div>
    <!-- <p>Name: {{ user.name }}</p>
    <p>Age: {{ user.age }}</p> -->
    <p>Count: {{ value }}</p>
    <button @click="increment">Increment</button>
    <p>Result: {{ result }}</p>
  </div>
</template>

<script>
import { ref, reactive, toRefs, watch } from "vue";

export default {
  setup() {
    const counter = reactive({
      value: 0,
      foo: "bar",
    });

    const num1 = ref(2);
    const num2 = ref(3);

    const increment = () => {
      counter.value++;
      num1.value++;
      num2.value++;
    };

    // gabisa karena object lebih baik refs
    // watch(counter, (current, before) => {
    //   console.log(counter.value);
    //   console.log(current);
    //   console.log(before);
    // });

    // ref
    // watch(num1, (current, before) => {
    //   console.log(num1.value);
    //   console.log(current);
    //   console.log(before);
    // });

    // ref 2 ref
    watch([num1, num2], (current, before) => {
      console.log(num1.value);
      console.log(num2.value);
      console.log(current);
      console.log(before);
    });

    // for object reactive
    // watch(
    //   () => counter.value,
    //   (current, before) => {
    //     console.log(counter.value);
    //     console.log(current);
    //     console.log(before);
    //   }
    // );

    return {
      ...toRefs(counter),
      num1,
      increment,
    };
  },
};
</script>

<template>
  <div>
    <!-- <p>Name: {{ user.name }}</p>
    <p>Age: {{ user.age }}</p> -->
    <p>Count: {{ value }}</p>
    <p>Count Num1: {{ num1 }}</p>
    <button @click="increment">Increment</button>
    <!-- <p>Result: {{ result }}</p> -->
  </div>
</template>

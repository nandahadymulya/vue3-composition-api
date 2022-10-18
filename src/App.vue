<script>
// import { ref } from "vue";
import { reactive, toRefs } from "vue";

export default {
  setup() {
    const counter = reactive({
      value: 0,
    });

    const increment = () => {
      counter.value++;
    };

    return {
      ...toRefs(counter),
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
    <button @click="increment">Increment</button>
    <!-- <p>Age: {{ age }}</p> -->
  </div>
</template>

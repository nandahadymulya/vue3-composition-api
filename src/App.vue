<script>
import { ref, reactive, toRefs, watchEffect } from "vue";

export default {
  setup() {
    const counter = reactive({
      value: 0,
      foo: "bar",
    });

    const increment = () => {
      counter.value++;
    };

    watchEffect(
      () => {
        console.log(counter.value);
        // jalan ketika setup jalan atau component di render
        // memantau counter.value
      },
      {
        // flush: "post",
        // pre: sebelum component di render maka print console.log
        // post: sesudah

        // for debugging
        onTrack(e) {
          console.log(e);
        },
      }
    );

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
    <!-- <p>Result: {{ result }}</p> -->
  </div>
</template>

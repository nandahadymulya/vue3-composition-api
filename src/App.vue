<script>
import { ref } from "vue";

export default {
  setup() {
    const message = ref("Hello Nanda");

    setTimeout(() => {
      console.log(message);
      message.value = "Apakah kamu bisa mengubahnya?";
    }, 2000);

    return {
      message,
    };
  },
};
</script>

<template>
  <h1>{{ message }}</h1>
</template>

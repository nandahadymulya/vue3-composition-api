<script>
// import { ref } from "vue";
import { reactive, toRefs } from "vue";

export default {
  setup() {
    const user = reactive({
      name: "Nanda",
      age: 25,
    });

    setTimeout(() => {
      console.log(user);
      user.name = "Hady";
      user.age = "26";
    }, 2000);

    // return {
    //   user,
    // };
    return {
      ...toRefs(user),
    };
  },
};
</script>

<template>
  <div>
    <!-- <p>Name: {{ user.name }}</p>
    <p>Age: {{ user.age }}</p> -->
    <p>Name: {{ name }}</p>
    <p>Age: {{ age }}</p>
  </div>
</template>

<script>
import { ref, reactive, toRef } from "vue";
import UserComponent from "./components/UserComponent.vue";

export default {
  components: {
    UserComponent,
  },
  setup() {
    const label = ref("Biodata");
    const user = reactive({
      name: "Nanda",
      age: 25,
    });

    const changeName = () => {
      user.name = "Nanda Hady Mulya";
    };

    const onSubmit = (val) => {
      console.log(val);
    };

    return {
      label,
      user,
      changeName,
      onSubmit,
    };
  },
};
</script>

<template>
  <h1>Parent</h1>
  <hr />
  <UserComponent :label="label" :user="user" class="active" address="padang" @submit="onSubmit">
    <div>Ini slot</div>
  </UserComponent>
  <button @click="changeName">Change Name</button>
</template>

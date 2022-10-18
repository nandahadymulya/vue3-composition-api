<script>
import { ref, toRefs, computed, onMounted } from "vue";
export default {
  inheritAttrs: false,
  props: {
    label: {
      type: String,
      default: "",
    },
    user: {
      type: Object,
      default: () => ({}),
    },
  },

  // setup(props, context) {
  setup(props, { attrs, slots, emit }) {
    // console.log(props);
    const { label, user } = toRefs(props);
    const description = computed(() => {
      return `${user.value.name} is ${user.value.age} years old`;
    });
    // console.log(label);
    // console.log(label.value);

    onMounted(() => {
      console.log(attrs);
      console.log(slots);
    });

    const submit = () => {
      emit("submit", "This emit from user component");
    };

    return {
      description,
      submit,
    };
  },
};
</script>

<template>
  <h1>User Component</h1>
  <p>{{ label }}</p>
  <ul>
    <li>{{ user.name }}</li>
    <li>{{ description }}</li>
  </ul>
  <button @click="submit">Submit from child</button>
  <hr />
  <slot />
</template>

<template>
  <div class="hello"></div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";

interface Person {
  name: string;
  class: string;
  age: number;
}

export default defineComponent({
  props: {
    success: { type: String },
    callback: {
      type: Function as PropType<() => void>
    },
    student: {
      type: Object as PropType<Student>,
      required: true
    }
  },
  setup() {},
  data() {
    return {
      message: "Vue3 code style"
    };
  },
  computed: {
    reversedMessage(): string {
      return this.message
        .split(" ")
        .reverse()
        .join("");
    }
  }
});
</script>

<style scoped lang="scss"></style>

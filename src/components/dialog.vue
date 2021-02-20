<template>
  <div class="hello">
    {{ greeting }}
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, toRefs, computed, unref } from "vue";

interface Person {
  name: string;
  age: number;
}

export default defineComponent({
  name: "newDialog",
  props: {
    person: {
      type: Object as PropType<Person>,
      required: true
    }
  },
  setup(props, ctx) {
    const { person } = toRefs(props);
    //unref 处理reactive对象为不需要取value
    const newPerson = unref(person);
    const greeting = computed(() => {
      return `${newPerson.name}今年${newPerson.age}岁`;
    });
    return {
      greeting
    };
  }
});
</script>

<style scoped lang="scss"></style>

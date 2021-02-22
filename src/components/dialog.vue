<template>
  <div class="hello">
    <teleport to="#app">
      <div v-if="showDialog" class="dialog">
        {{ greeting }}
      </div>
    </teleport>
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
    const showDialog = true;
    //unref 处理reactive对象为不需要取value
    const newPerson = unref(person);
    const greeting = computed(() => {
      return `${newPerson.name}今年${newPerson.age}岁`;
    });
    return {
      greeting,
      showDialog
    };
  }
});
</script>
<style lang="scss" scoped>
.dialog {
  display: flex;
  width: 800px;
  height: 500px;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  box-shadow: 1px 2px 10px 1px rgba(35, 52, 85, 0.11);
}
</style>

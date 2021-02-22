<template>
  <div class="hello">
    <teleport to="#app">
      <div v-if="showDialog" class="dialog">
        <div>{{ greeting }}</div>
        <button @click="addAge">年龄增长</button>
        <button @click="closeDialog">关闭弹窗</button>
      </div>
    </teleport>
  </div>
</template>

<script lang="ts">
import {
  watch,
  defineComponent,
  PropType,
  toRefs,
  computed,
  unref,
  ref
} from "vue";

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
  emit: ["update:isShow", "change-message"],
  setup(props, ctx) {
    console.log(ctx);
    const { person } = toRefs(props);
    const showDialog = ref(true);
    //unref 处理reactive对象为不需要取value
    const newPerson = unref(person);

    const greeting = computed(() => {
      return `${newPerson.name}今年${newPerson.age}岁`;
    });

    // watch(isShow, val => {});

    const closeDialog = () => {
      ctx.emit("update:isShow", false);
    };
    const addAge = () => {
      ctx.emit("change-message", person.value.age++);
    };
    return {
      greeting,
      showDialog,
      closeDialog,
      addAge
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

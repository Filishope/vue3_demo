<template>
  <div class="home">
    <button @click="handleClick">点击我</button>
    <new-dialog
      :person="person"
      v-model:isShow="isShow"
      @change-message="changeMessage"
    ></new-dialog>
  </div>
</template>

<script lang="ts">
import { reactive, ref } from "vue";
import NewDialog from "../components/dialog.vue";
interface Person {
  name: string;
  age: number;
}
export default {
  name: "home",
  components: {
    NewDialog
  },
  setup() {
    const isShow = ref(false);
    const person = reactive<Person>({ name: "小红", age: 18 });
    const handleClick = () => {
      isShow.value = true;
    };
    const changeMessage = (age: number) => {
      console.log(age);
    };
    return {
      isShow,
      person,
      handleClick,
      changeMessage
    };
  }
};
</script>

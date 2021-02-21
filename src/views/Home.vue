<template>
  <div class="home">
    <new-dialog :person="person"></new-dialog>
  </div>
</template>

<script lang="ts">
import { reactive } from "vue";
import NewDialog from "../components/dialog.vue";
interface Person {
  name: string;
  age: number;
}
export default {
  components: {
    NewDialog
  },
  setup() {
    const person = reactive<Person>({ name: "小红", age: 18 });
    return {
      person
    };
  }
};
</script>

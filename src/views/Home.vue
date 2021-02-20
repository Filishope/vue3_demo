<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <Dialog msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Dialog from "@/components/dialog.vue"; // @ is an alias to /src

@Options({
  components: {
    Dialog
  }
})
</script>

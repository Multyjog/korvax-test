<template>
  <form @submit.prevent="onSubmit" class="inputs">
    <textarea
      class="border-light"
      id="vue-code"
      placeholder="Vue.js code"
      rows="10"
      cols="50"
      v-model="formData.vueCode"
    ></textarea>
    <textarea
      class="border-light"
      id="css-code"
      placeholder="CSS code"
      rows="10"
      cols="50"
      v-model="formData.cssCode"
    ></textarea>
    <button type="submit">Save</button>
  </form>
</template>

<script setup lang="ts">
import { ref } from "vue";
const emit = defineEmits<{
  (e: "submit", value: { vueCode: string; cssCode: string }): void;
}>();

const formData = ref({
  vueCode: "",
  cssCode: "",
});
const onSubmit = () => {
  emit("submit", formData.value);
};
</script>

<style scoped>
.inputs {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>

<template>
  <h1>My Vuelidate Test </h1>
  <FormComponent />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormComponent from '@/components/FormComponent.vue';

export default defineComponent({
  name: 'App',
  components: {
    FormComponent,
  }
});
</script>

<style>
body, html {
  background-color: rgb(72, 85, 112);
  margin: 0;
  padding: 0;
}
h1 {
  color: bisque;
  margin: 50px 0;
}
#app {
 display: flex;
 flex-direction: column;
 justify-content: center;
 align-items: center;
}
</style>

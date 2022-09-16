<template>
  <p>YO</p>

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
#app {
 
}
</style>

<template>
  <form class="form">
    <div class="fieldset">
      <input type="text" placeholder="Email" v-model="state.email">
      <span class="error" v-if="v$.email.$error">{{v$.email.$errors[0].$message}} </span>
    </div>
    <div class="fieldset">
      <input type="password" placeholder="Password" v-model="state.password.password">
    </div>
    <div class="fieldset">
      <input type="password" placeholder="Confirm password" v-model="state.password.confirm">
    </div>
    <button type="button" @click="submitForm()">Envoyer</button>
  </form>
</template>
<script lang="ts">
import {useVuelidate} from '@vuelidate/core'
import { required, email, minLength, sameAs } from '@vuelidate/validators'

import { defineComponent, reactive, computed } from 'vue'

export default defineComponent({
  setup() {
    const state = reactive({
      email: '',
      password: {
        password: '',
        confirm: ''
    }
    });

    const rules = computed(() => {
      return {
        email: { required, email },
        password: {
          password:  { required, minLength: minLength(6) },
          confirm:  { required, sameAs: sameAs(state.password.password) }
        }
      }
    });

    const v$ = useVuelidate(rules, state);

    return {
      state,
      v$,
    }
  },
  methods: {
    submitForm() {
      this.v$.$validate();
      if(!this.v$.$error) {
        console.log('Success');
        console.log(this.v$);
      } else {
        console.log(this.v$.$errors);
      }
    }
  }
})
</script>
<style scoped>
.form {
  margin: 50px 0;
  min-width: 400px;
  background-color: rgb(190, 168, 168);
  padding: 20px;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
}

.fieldset {
  margin: 25px 0;
}

.fieldset input {
  padding: 5px 10px;
  border-radius: 5px;
  border: none;
  width: 100%;
  box-sizing: border-box;
}

button {
  /* width: 150px; */
  border: none;
  border-radius: 3px;
  padding: 5px 10px;
  background-color: rgb(78, 219, 172);
  align-self: flex-end;
  min-width: 100px;
  cursor: pointer;
}

button:hover {
  background-color: rgb(48, 139, 109);;
}

</style>

# Vue Valid Forms

> Simple forms validation for Vue 3.0

## Installation

```bash
npm install vue-valid-forms
```

## Usage with Composition API

```vue
<Form :on-validated="submit">
   <div class="col-12">
      <InputField v-model="user.email" type="email" name="email" placeholder="Email" rules="required|email" />
   </div>

   <div class="col-12">
      <InputField v-model="user.password" type="password" name="password" placeholder="Password" rules="required|min:8" />
   </div>

   <template #submit="slotProps">
      <div class="col-12">
      <button class="btn btn-primary w-100" :disabled="slotProps.submitting">
         <span v-if="slotProps.submitting" class="spinner-border spinner-border-sm" role="status" aria-hidden="true"></span>
         Login
      </button>
      </div>
      <div v-if="success" class="valid-feedback d-block">{{ success }}</div>
      <div v-if="error" class="invalid-feedback d-block">{{ error }}</div>
   </template>
</Form>
```

```ts
import { reactive, ref } from 'vue'
import Form from '../lib/Form.vue'
import InputField from '../lib/InputField.vue'

const user = reactive({
  email: '',
  password: ''
})
const error = ref('')
const success = ref('')

function submit() {
  success.value = 'Success!'
}
```

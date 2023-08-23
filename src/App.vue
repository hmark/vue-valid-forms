<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-xl-6 col-lg-12 col-md-9">
        <div class="card o-hidden border-0 shadow-lg my-5">
          <div class="card-body p-0">
            <div class="row">
              <div class="col-lg-2 d-none d-lg-block bg-login-image"></div>
              <div class="col-lg-8">
                <div class="p-5">
                  <div class="text-center">
                    <h1 class="h4 text-gray-900 mb-4">Login</h1>
                  </div>
                  <Form :on-validated="submit" class="row g-3">
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
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'
import Form from '../lib/Form.vue'
import InputField from '../lib/InputField.vue'

const user = reactive({
  email: '',
  password: ''
})
const error = ref('')
const success = ref('')

async function submit() {
  error.value = ''
  success.value = "Success!"
}
</script>
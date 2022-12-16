<template>
  <div>
    <div class="pt-5 space-y-6">
      <UIInput label="Username"
               placeholder="@username"
               v-model="data.username"/>
      <UIInput type="password"
               label="Password"
               placeholder="********"
               v-model="data.password"/>
      <div>
        <button @click="handleLogin">
          Submit
        </button>
      </div>
    </div>
  </div>
</template>
<script setup>
import useAuth from "~/composables/useAuth";

const data = reactive({
  username: '',
  password: ''
})

async function handleLogin() {
  const { login } = useAuth()
  data.loading = true
  try {
    await login({
      username: data.username,
      password: data.password
    })
  } catch (error) {
    console.log(error)
  } finally {
    data.loading = false
  }
}

</script>

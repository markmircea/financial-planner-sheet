<template>
  <div class="min-h-screen flex items-center justify-center bg-gradient-to-r from-blue-500 to-green-500 py-12 px-4 sm:px-6 lg:px-8">
    <div class="max-w-md w-full space-y-8 glass rounded-lg p-8 shadow-xl animate-fadeIn">
      <div>
        <h2 class="mt-6 text-center text-3xl font-extrabold gradient-text">
          Sign in to your account
        </h2>
      </div>
      <form class="mt-8 space-y-6" @submit.prevent="login">
        <div class="rounded-md shadow-sm -space-y-px">
          <div class="mb-4">
            <label for="email-address" class="sr-only">Email address</label>
            <input id="email-address" name="email" type="email" autocomplete="email" required
                   class="appearance-none rounded-t-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm transition duration-300 ease-in-out"
                   placeholder="Email address" v-model="form.email">
          </div>
          <div>
            <label for="password" class="sr-only">Password</label>
            <input id="password" name="password" type="password" autocomplete="current-password" required
                   class="appearance-none rounded-b-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm transition duration-300 ease-in-out"
                   placeholder="Password" v-model="form.password">
          </div>
        </div>

        <div>
          <button type="submit"
                  class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 transition duration-300 ease-in-out transform hover:scale-105">
            <span class="absolute left-0 inset-y-0 flex items-center pl-3">
              <svg class="h-5 w-5 text-indigo-500 group-hover:text-indigo-400 transition ease-in-out duration-300" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                <path fill-rule="evenodd" d="M5 9V7a5 5 0 0110 0v2a2 2 0 012 2v5a2 2 0 01-2 2H5a2 2 0 01-2-2v-5a2 2 0 012-2zm8-2v2H7V7a3 3 0 016 0z" clip-rule="evenodd" />
              </svg>
            </span>
            Sign in
          </button>
        </div>
      </form>
      <div class="text-center">
        <a href="/register" class="font-medium text-indigo-600 hover:text-indigo-500 transition duration-300 ease-in-out">
          Don't have an account? Sign up
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'
import { useForm } from '@inertiajs/vue3';

export default defineComponent({
  setup() {
    const form = useForm({
      email: '',
      password: '',
    })

    const login = () => {
      form.post('/login', {
        preserveState: true,
        preserveScroll: true,
      })
    }

    return { form, login }
  },
})
</script>

<style scoped>
.glass {
  @apply bg-white bg-opacity-20 backdrop-filter backdrop-blur-lg;
}

.gradient-text {
  @apply text-transparent bg-clip-text bg-gradient-to-r from-indigo-600 to-green-700;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.animate-fadeIn {
  animation: fadeIn 0.5s ease-out;
}
</style>

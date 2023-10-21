<script lang="ts" setup>
definePageMeta({
  middleware: "guest",
});

const form = ref({
  username: "",
  password: "",
});

const { signIn } = useAuth();

async function handleLogin() {
  try {
    await signIn("credentials", form.value);
    useRouter().push({
      name: "index",
    });
  } catch (e) {}
}
</script>
<template>
  <div>
    <h1 class="mb-4 text-xl font-bold">Login</h1>
    <form @submit.prevent="handleLogin">
      <input
        v-model="form.username"
        class="w-full border p-2 rounded-lg mb-4"
        type="text"
        placeholder="Username"
      />
      <input
        v-model="form.password"
        class="w-full border p-2 rounded-lg mb-4"
        type="password"
        placeholder="Password"
      />
      <button
        type="submit"
        class="bg-blue-500 hover:bg-blue-600 transition-all duration-200 w-full text-blue-50 rounded-lg p-2"
      >
        Login
      </button>
    </form>
  </div>
</template>

<style></style>

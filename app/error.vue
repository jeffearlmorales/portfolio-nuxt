<script setup lang="ts">
import { AlertTriangle, Home } from "lucide-vue-next";

const error = useError();

const is404 = computed(() => error.value?.statusCode === 404);

useHead({
  title: is404.value
    ? "404 - Page Not Found | Jeff Earl Morales"
    : "Error | Jeff Earl Morales",
});

const handleBackHome = () => {
  clearError({ redirect: "/" });
};
</script>

<template>
  <div
    class="flex min-h-screen flex-col items-center justify-center bg-base-100 px-6 text-center text-base-content"
  >
    <div
      class="card max-w-md border-2 border-primary/50 bg-base-200 p-8 orange-glow"
    >
      <div
        class="mx-auto mb-4 flex h-16 w-16 items-center justify-center rounded-full bg-primary/15 text-primary"
      >
        <AlertTriangle class="h-8 w-8" />
      </div>

      <template v-if="error?.statusCode === 404">
        <h1
          class="font-serif-display brand-gradient-text text-6xl font-extrabold"
        >
          404
        </h1>
        <h2 class="font-serif-display mt-2 text-2xl font-bold">
          Page Not Found
        </h2>
        <p class="mt-2 text-sm text-base-content/75">
          The page you're looking for doesn't exist in this portfolio.
        </p>
      </template>

      <template v-else>
        <h1
          class="font-serif-display brand-gradient-text text-6xl font-extrabold"
        >
          {{ error?.statusCode || 500 }}
        </h1>
        <h2 class="font-serif-display mt-2 text-2xl font-bold">
          Something Went Wrong
        </h2>
        <p class="mt-2 text-sm text-base-content/75">
          {{ error?.message || "An unexpected error occurred." }}
        </p>
      </template>

      <button
        @click="handleBackHome"
        class="btn btn-primary mt-6 rounded-full px-6 font-bold"
      >
        <Home class="h-4 w-4" /> Return Home
      </button>
    </div>
  </div>
</template>

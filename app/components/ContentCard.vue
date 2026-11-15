<script setup lang="ts">
import type { Component } from "vue";
import { ExternalLink, Eye } from "lucide-vue-next";

defineProps<{
  title: string;
  description?: string;
  image?: string;
  badge?: string;
  icon?: Component;
  link?: string;
  linkLabel?: string;
  clickableImage?: boolean;
}>();

defineEmits<{
  (e: "preview", image: string, title: string): void;
}>();
</script>

<template>
  <article
    class="card border-2 border-primary/50 bg-base-100 transition-all duration-300 hover:-translate-y-1 hover:border-primary orange-glow"
  >
    <figure
      v-if="image"
      class="relative cursor-pointer overflow-hidden px-5 pt-5"
      @click="clickableImage && $emit('preview', image, title)"
    >
      <img
        :src="image"
        :alt="title"
        class="h-48 w-full rounded-xl border border-primary/40 object-cover transition-transform duration-300 hover:scale-105"
      />
      <span
        v-if="clickableImage"
        class="badge badge-neutral/90 absolute right-7 bottom-2 gap-1 text-xs"
      >
        <Eye class="h-3 w-3 text-primary" /> Click to enlarge
      </span>
    </figure>

    <div class="card-body items-center text-center">
      <div
        v-if="icon"
        class="mb-2 flex h-14 w-14 items-center justify-center rounded-2xl bg-primary/15 text-primary"
      >
        <component :is="icon" class="h-7 w-7" />
      </div>

      <span v-if="badge" class="badge badge-primary badge-outline badge-sm">
        {{ badge }}
      </span>

      <h3 class="font-serif-display card-title text-xl font-bold">
        {{ title }}
      </h3>

      <p
        v-if="description"
        class="text-sm leading-relaxed text-base-content/75"
      >
        {{ description }}
      </p>

      <div v-if="link" class="card-actions mt-3">
        <a
          :href="link"
          target="_blank"
          rel="noopener noreferrer"
          class="btn btn-primary btn-sm rounded-full px-5 font-semibold"
        >
          <span>{{ linkLabel || "View Credentials" }}</span>
          <ExternalLink class="h-3.5 w-3.5" />
        </a>
      </div>
    </div>
  </article>
</template>

<script setup lang="ts">
import { Github, Linkedin, Instagram, Twitter, ArrowUp } from "lucide-vue-next";

const socials = [
  { label: "GitHub", href: "https://github.com/jeffearlmorales", icon: Github },
  {
    label: "LinkedIn",
    href: "https://www.linkedin.com/in/jeff-earl-morales-17520a40b/",
    icon: Linkedin,
  },
  {
    label: "Instagram",
    href: "https://www.instagram.com/jaden.mrls?igsh=MTVvMzlkd2w5dG1sZQ%3D%3D&utm_source=qr",
    icon: Instagram,
  },
  {
    label: "X / Twitter",
    href: "https://x.com/jeff_buttowskii?s=21",
    icon: Twitter,
  },
];

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>

<template>
  <footer
    class="footer footer-center gap-4 border-t border-primary/25 bg-base-200 px-6 py-8 text-base-content"
  >
    <nav class="flex flex-wrap justify-center gap-3">
      <a
        v-for="social in socials"
        :key="social.label"
        :href="social.href"
        target="_blank"
        rel="noopener noreferrer"
        :aria-label="social.label"
        class="btn btn-circle btn-outline btn-primary transition-transform hover:-translate-y-1 hover:scale-110"
      >
        <component :is="social.icon" class="h-5 w-5" />
      </a>
    </nav>

    <div class="flex flex-col items-center gap-2 sm:flex-row sm:gap-4">
      <p class="font-serif-display text-sm text-base-content/85">
        @ Jeff Earl Morales | Portfolio
      </p>
      <button
        @click="scrollToTop"
        class="btn btn-ghost btn-xs gap-1 text-primary"
      >
        <ArrowUp class="h-3.5 w-3.5" /> Back to top
      </button>
    </div>
  </footer>
</template>

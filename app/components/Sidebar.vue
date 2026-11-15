<script setup lang="ts">
import {
  Home,
  User,
  Layers,
  Award,
  Mail,
  Github,
  Linkedin,
  Instagram,
  Twitter,
  Sparkles,
} from "lucide-vue-next";

const navItems = [
  { label: "Home", to: "/", icon: Home },
  { label: "About Me", to: "/about", icon: User },
  { label: "Tech Stack", to: "/techstack", icon: Layers },
  { label: "Certifications", to: "/certificate", icon: Award },
  { label: "Contact", to: "/contact", icon: Mail },
];

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
</script>

<template>
  <aside
    class="hidden w-72 shrink-0 border-r border-primary/20 bg-base-200/70 p-6 lg:flex lg:flex-col lg:justify-between"
  >
    <div class="space-y-6">
      <!-- Profile Card -->
      <div
        class="card border border-primary/40 bg-base-100 p-5 text-center orange-glow"
      >
        <div
          class="mx-auto mb-3 h-24 w-24 overflow-hidden rounded-full border-2 border-primary"
        >
          <img
            src="/Images/MyPicture/myimage.png"
            alt="Jeff Earl Morales"
            class="h-full w-full object-cover"
          />
        </div>
        <h2 class="font-serif-display text-lg font-bold">
          Jeff Earl <span class="brand-gradient-text">Morales</span>
        </h2>
        <p class="mt-1 text-xs text-base-content/75">
          UI/UX • Frontend • Backend
        </p>
        <div
          class="badge badge-primary badge-outline mx-auto mt-3 gap-1 text-xs"
        >
          <Sparkles class="h-3 w-3" /> Keep Moving Forward
        </div>
      </div>

      <!-- Desktop Sidebar Navigation -->
      <ul
        class="menu w-full rounded-box border border-base-300 bg-base-100 p-2"
      >
        <li class="menu-title text-xs uppercase tracking-wider text-primary">
          Navigation
        </li>
        <li v-for="item in navItems" :key="item.to">
          <NuxtLink
            :to="item.to"
            active-class="bg-primary text-primary-content font-semibold"
          >
            <component :is="item.icon" class="h-4 w-4" />
            {{ item.label }}
          </NuxtLink>
        </li>
      </ul>
    </div>

    <!-- Social Icon Row -->
    <div class="pt-6">
      <p
        class="mb-2 text-center text-xs uppercase tracking-wider text-base-content/60"
      >
        Connect
      </p>
      <div class="flex justify-center gap-2">
        <a
          v-for="social in socials"
          :key="social.label"
          :href="social.href"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="social.label"
          class="btn btn-circle btn-outline btn-primary btn-sm transition-transform hover:-translate-y-1"
        >
          <component :is="social.icon" class="h-4 w-4" />
        </a>
      </div>
    </div>
  </aside>
</template>

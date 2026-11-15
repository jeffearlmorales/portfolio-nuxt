<script setup lang="ts">
import { Home, User, Layers, Award, Mail, Menu, Code2 } from "lucide-vue-next";

const navItems = [
  { label: "Home", to: "/", icon: Home },
  { label: "About", to: "/about", icon: User },
  { label: "Tech Stack", to: "/techstack", icon: Layers },
  { label: "Certifications", to: "/certificate", icon: Award },
  { label: "Contact", to: "/contact", icon: Mail },
];
</script>

<template>
  <header
    class="navbar sticky top-0 z-40 border-b border-primary/25 bg-base-100/85 px-4 py-3 backdrop-blur-md lg:px-10"
  >
    <div class="navbar-start">
      <!-- Mobile Dropdown -->
      <div class="dropdown lg:hidden">
        <div
          tabindex="0"
          role="button"
          class="btn btn-ghost btn-square text-primary"
          aria-label="Open menu"
        >
          <Menu class="h-6 w-6" />
        </div>
        <ul
          tabindex="0"
          class="menu dropdown-content menu-sm z-50 mt-3 w-56 rounded-box border border-primary/40 bg-base-200 p-2 shadow-xl"
        >
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

      <NuxtLink
        to="/"
        class="font-serif-display flex items-center gap-2 text-2xl font-extrabold tracking-tight transition-transform hover:scale-105"
      >
        <Code2 class="h-6 w-6 text-primary" />
        <span>Jeff Earl <span class="brand-gradient-text">Morales</span></span>
      </NuxtLink>
    </div>

    <div class="navbar-end hidden lg:flex">
      <ul class="menu menu-horizontal gap-2 px-1 text-sm font-medium">
        <li v-for="item in navItems" :key="item.to">
          <NuxtLink
            :to="item.to"
            class="border-b-2 border-transparent transition-all hover:border-primary hover:text-primary"
            active-class="!border-primary text-primary font-semibold"
          >
            <component :is="item.icon" class="h-4 w-4" />
            {{ item.label }}
          </NuxtLink>
        </li>
      </ul>
    </div>
  </header>
</template>

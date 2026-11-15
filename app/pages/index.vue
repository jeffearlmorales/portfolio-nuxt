<script setup lang="ts">
import {
  Briefcase,
  Award,
  Github,
  Linkedin,
  Instagram,
  Twitter,
  Code2,
  Database,
  Palette,
} from "lucide-vue-next";

useHead({
  title: "Jeff Earl Morales | Portfolio",
});

useSeoMeta({
  description:
    "Web Developer portfolio of Jeff Earl Morales specializing in UI/UX Design, Frontend Development, and Backend Development.",
  ogTitle: "Jeff Earl Morales | Web Developer Portfolio",
  ogDescription:
    "Explore UI/UX design, frontend, and backend web development work and certifications by Jeff Earl Morales.",
});

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
  <div class="space-y-14">
    <!-- Hero Section -->
    <section
      class="flex flex-col-reverse items-center justify-between gap-10 rounded-3xl border border-primary/30 bg-base-200/60 p-8 lg:flex-row lg:p-12"
    >
      <div
        class="flex flex-col items-center text-center lg:items-start lg:text-left"
      >
        <h1
          class="font-serif-display text-4xl font-extrabold tracking-tight sm:text-6xl"
        >
          Hi, it's <span class="brand-gradient-text">Jeff</span>
        </h1>
        <h2 class="font-serif-display mt-3 text-2xl font-bold sm:text-4xl">
          I'm a <span class="brand-gradient-text">Web Developer</span>
        </h2>
        <p
          class="mt-3 text-sm font-semibold tracking-wide text-base-content/80 sm:text-base"
        >
          UI/UX Design <span class="text-primary">|</span> Frontend Development
          <span class="text-primary">|</span> Backend Development
        </p>

        <!-- Social Icons -->
        <div class="mt-6 flex flex-wrap justify-center gap-3 lg:justify-start">
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
        </div>

        <!-- Primary Action Buttons -->
        <div class="mt-7 flex flex-wrap justify-center gap-4 lg:justify-start">
          <NuxtLink
            to="/contact"
            class="btn btn-primary rounded-full px-7 text-base font-bold orange-glow"
          >
            <Briefcase class="h-4 w-4" /> Hire
          </NuxtLink>
          <NuxtLink
            to="/certificate"
            class="btn btn-outline btn-primary rounded-full px-7 text-base font-bold"
          >
            <Award class="h-4 w-4" /> View Certs
          </NuxtLink>
        </div>
      </div>

      <!-- Circular Glowing Portrait -->
      <div class="shrink-0">
        <div
          class="h-60 w-60 overflow-hidden rounded-full border-4 border-primary sm:h-80 sm:w-80 orange-glow"
        >
          <img
            src="/Images/MyPicture/myimage.png"
            alt="Jeff Earl Morales Profile"
            class="h-full w-full object-cover"
          />
        </div>
      </div>
    </section>

    <!-- Core Disciplines Summary -->
    <section class="grid gap-6 md:grid-cols-3">
      <ContentCard
        title="UI/UX Design"
        badge="Design"
        description="Crafting user-friendly, responsive layouts with modern visual hierarchy and intuitive navigation."
        :icon="Palette"
      />
      <ContentCard
        title="Frontend Development"
        badge="Client-Side"
        description="Building modular interfaces with Nuxt, Vue, HTML5, CSS3, JavaScript, Tailwind CSS, and DaisyUI."
        :icon="Code2"
      />
      <ContentCard
        title="Backend Development"
        badge="Server & Data"
        description="Structuring reliable server-side logic, relational PostgreSQL databases, and Git version workflows."
        :icon="Database"
      />
    </section>
  </div>
</template>

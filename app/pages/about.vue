<script setup lang="ts">
import { Compass, Target, Award, Layers } from "lucide-vue-next";

useHead({
  title: "About Me | Jeff Earl Morales",
});

useSeoMeta({
  description:
    "Learn about Jeff Earl Morales, an IT student and web developer committed to the Keep Moving Forward philosophy.",
  ogTitle: "About Me | Jeff Earl Morales",
  ogDescription:
    "Full-stack web development journey, philosophy, and goals of Jeff Earl Morales.",
});
</script>

<template>
  <div class="space-y-10">
    <section
      class="flex flex-col items-center gap-10 rounded-3xl border border-primary/30 bg-base-200 p-8 lg:flex-row lg:p-12"
    >
      <div class="shrink-0">
        <div
          class="h-60 w-60 overflow-hidden rounded-full border-4 border-primary sm:h-72 sm:w-72 orange-glow"
        >
          <img
            src="/Images/MyPicture/myimage.png"
            alt="Jeff Morales"
            class="h-full w-full object-cover"
          />
        </div>
      </div>

      <div class="space-y-5 text-center lg:text-left">
        <div
          class="badge badge-primary badge-outline gap-1.5 px-3 py-3 font-medium"
        >
          <Compass class="h-3.5 w-3.5" /> Personal Philosophy
        </div>
        <h1 class="font-serif-display text-4xl font-extrabold sm:text-5xl">
          Keep Moving <span class="brand-gradient-text">Forward</span>
        </h1>
        <p class="leading-relaxed text-base-content/85 sm:text-lg">
          I am a dedicated IT student with a passion for building creative
          solutions through technology. Outside of my studies, I enjoy exploring
          modern design trends and finding ways to make digital experiences more
          user-friendly. I believe that learning is a lifelong journey, which is
          why I constantly seek out new certifications to sharpen my technical
          skills. My current focus is on mastering frontend and backend
          development to create seamless, functional websites.
        </p>
        <p class="leading-relaxed text-base-content/85 sm:text-lg">
          My ultimate goal is to become a professional web developer where I can
          contribute to impactful projects on a global scale. I aspire to
          specialize in full-stack development, bridging the gap between
          beautiful user interfaces and robust server-side logic. By staying
          committed to the "Keep Moving Forward" philosophy, I aim to eventually
          lead development teams and mentor others in the tech community.
        </p>

        <div class="flex flex-wrap justify-center gap-3 pt-2 lg:justify-start">
          <NuxtLink to="/techstack" class="btn btn-primary rounded-full">
            <Layers class="h-4 w-4" /> Explore Tech Stack
          </NuxtLink>
          <NuxtLink
            to="/certificate"
            class="btn btn-outline btn-primary rounded-full"
          >
            <Award class="h-4 w-4" /> View Certifications
          </NuxtLink>
        </div>
      </div>
    </section>

    <!-- Focus Pillars -->
    <section class="grid gap-6 md:grid-cols-2">
      <ContentCard
        title="Continuous Learning"
        badge="Mindset"
        description="Earned verified credentials across software engineering, Python, networking, and productivity tools to build a strong technical foundation."
        :icon="Award"
      />
      <ContentCard
        title="Full-Stack Vision"
        badge="Career Goal"
        description="Combining clean, responsive frontend craftsmanship with structured databases and maintainable backend architecture."
        :icon="Target"
      />
    </section>
  </div>
</template>

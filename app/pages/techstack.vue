<script setup lang="ts">
import {
  Coffee,
  FileCode2,
  Palette,
  Braces,
  GitBranch,
  Github,
  Database,
  TerminalSquare,
  BarChart3,
} from "lucide-vue-next";

useHead({
  title: "Tech Stack | Jeff Earl Morales",
});

useSeoMeta({
  description:
    "Programming languages, databases, and developer tools used by Jeff Earl Morales including Java, HTML, CSS, JavaScript, Git, GitHub, PostgreSQL, and VS Code.",
  ogTitle: "Tech Stack | Jeff Earl Morales",
  ogDescription:
    "Technical skills and interactive Apache ECharts stack breakdown for Jeff Earl Morales.",
});

const stackItems = [
  {
    title: "Java",
    badge: "Backend / OOP",
    description:
      "Java is a versatile and widely-used object-oriented programming language.",
    icon: Coffee,
  },
  {
    title: "HTML",
    badge: "Frontend",
    description:
      "HyperText Markup Language for semantic, accessible web structure.",
    icon: FileCode2,
  },
  {
    title: "CSS",
    badge: "Styling",
    description:
      "Cascading Style Sheets, Tailwind CSS, and DaisyUI for responsive layouts.",
    icon: Palette,
  },
  {
    title: "JavaScript",
    badge: "Full-Stack",
    description:
      "JavaScript and Vue/Nuxt for dynamic, interactive web applications.",
    icon: Braces,
  },
  {
    title: "Git",
    badge: "Version Control",
    description:
      "Distributed version control system for tracking code changes safely.",
    icon: GitBranch,
  },
  {
    title: "GitHub",
    badge: "Collaboration & CI",
    description:
      "Git repository hosting service powering collaboration and cloud deployments.",
    icon: Github,
  },
  {
    title: "PostgreSQL",
    badge: "Database",
    description:
      "Relational database management system using Structured Query Language.",
    icon: Database,
  },
  {
    title: "VS Code",
    badge: "IDE",
    description:
      "Visual Studio Code development environment for web and software builds.",
    icon: TerminalSquare,
  },
];

const barChartOption = ref({
  tooltip: { trigger: "axis" },
  grid: { left: "3%", right: "5%", bottom: "3%", containLabel: true },
  xAxis: {
    type: "value",
    max: 100,
    axisLabel: { color: "#a3a3a3" },
    splitLine: { lineStyle: { color: "rgba(234, 88, 12, 0.15)" } },
  },
  yAxis: {
    type: "category",
    data: [
      "PostgreSQL",
      "Java",
      "Git & GitHub",
      "JavaScript / Nuxt",
      "HTML & CSS",
    ],
    axisLabel: { color: "#e5e5e5" },
  },
  series: [
    {
      name: "Proficiency (%)",
      type: "bar",
      data: [80, 82, 85, 88, 92],
      itemStyle: {
        color: "#ea580c",
        borderRadius: [0, 8, 8, 0],
      },
    },
  ],
});

const pieChartOption = ref({
  tooltip: { trigger: "item", formatter: "{b}: {c}% ({d}%)" },
  legend: { bottom: 0, textStyle: { color: "#e5e5e5" } },
  series: [
    {
      name: "Stack Distribution",
      type: "pie",
      radius: ["45%", "70%"],
      itemStyle: { borderRadius: 6 },
      label: { show: false },
      color: ["#ea580c", "#df8908", "#ff1d15", "#fb923c"],
      data: [
        { value: 40, name: "Frontend (HTML/CSS/JS/Nuxt)" },
        { value: 25, name: "Backend (Java)" },
        { value: 20, name: "Database (PostgreSQL)" },
        { value: 15, name: "Dev Tools (Git/GitHub/VS Code)" },
      ],
    },
  ],
});
</script>

<template>
  <div class="space-y-10">
    <div class="text-center">
      <h1 class="font-serif-display text-4xl font-extrabold sm:text-5xl">
        Tech <span class="brand-gradient-text">Stack</span>
      </h1>
      <p class="mt-2 text-base-content/75">
        Core languages, databases, and tools I use to build modern applications.
      </p>
    </div>

    <!-- 8 Tech Stack Cards with Lucide Icons -->
    <section class="grid gap-6 sm:grid-cols-2 lg:grid-cols-4">
      <ContentCard
        v-for="tech in stackItems"
        :key="tech.title"
        :title="tech.title"
        :badge="tech.badge"
        :description="tech.description"
        :icon="tech.icon"
      />
    </section>

    <!-- Apache ECharts Bonus Integration -->
    <section class="space-y-4 pt-4">
      <div class="flex items-center gap-2 text-primary">
        <BarChart3 class="h-5 w-5" />
        <h2 class="font-serif-display text-2xl font-bold text-base-content">
          Stack Proficiency & Distribution
        </h2>
      </div>

      <div class="grid gap-6 lg:grid-cols-2">
        <div class="card border border-primary/35 bg-base-200 p-5">
          <h3
            class="mb-2 text-sm font-semibold uppercase tracking-wider text-base-content/75"
          >
            Core Skill Proficiency (%)
          </h3>
          <div class="h-72 w-full">
            <ClientOnly>
              <VChart :option="barChartOption" autoresize />
            </ClientOnly>
          </div>
        </div>

        <div class="card border border-primary/35 bg-base-200 p-5">
          <h3
            class="mb-2 text-sm font-semibold uppercase tracking-wider text-base-content/75"
          >
            Development Focus Breakdown
          </h3>
          <div class="h-72 w-full">
            <ClientOnly>
              <VChart :option="pieChartOption" autoresize />
            </ClientOnly>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

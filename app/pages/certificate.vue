<script setup lang="ts">
import { Award, X } from "lucide-vue-next";

useHead({
  title: "Certifications | Jeff Earl Morales",
});

useSeoMeta({
  description:
    "Verified industry certifications earned by Jeff Earl Morales in Software Engineering, Python Essentials, Networking Basics, Microsoft Word, and PowerPoint.",
  ogTitle: "Certifications | Jeff Earl Morales",
  ogDescription:
    "View verified Credly and Saylor Academy credentials earned by Jeff Earl Morales.",
});

const certificates = [
  {
    title: "Microsoft PowerPoint",
    badge: "Microsoft Office Specialist",
    image: "/Images/Certifications/powerpointcertificate.png",
    link: "https://www.credly.com/badges/9b490918-fa35-4f49-823e-f3500287c71e/public_url",
  },
  {
    title: "Microsoft Word",
    badge: "Microsoft Office Specialist",
    image: "/Images/Certifications/wordcertificate.png",
    link: "https://www.credly.com/badges/cca1c29d-0a29-4587-8876-6c6964441e8c/public_url",
  },
  {
    title: "Software Engineering",
    badge: "Saylor Academy",
    image: "/Images/Certifications/sailorCERTIFICATE.png",
    link: "https://learn.saylor.org/admin/tool/certificate/index.php?code=9708058266JM",
  },
  {
    title: "Python Essentials 1",
    badge: "Cisco Networking Academy",
    image: "/Images/Certifications/phyton.png",
    link: "https://www.credly.com/badges/d532fce2-123a-4b2f-875d-05f6aeeaebff/public_url",
  },
  {
    title: "Networking Basics",
    badge: "Cisco Networking Academy",
    image: "/Images/Certifications/networking.png",
    link: "https://www.credly.com/badges/ea128e0c-c138-45bc-b084-08f75f828b61/public_url",
  },
];

const selectedCert = ref<{ image: string; title: string } | null>(null);

const openPreview = (image: string, title: string) => {
  selectedCert.value = { image, title };
};

const closePreview = () => {
  selectedCert.value = null;
};
</script>

<template>
  <div class="space-y-8">
    <div class="text-center">
      <div class="badge badge-primary badge-outline mb-2 gap-1.5 px-3 py-3">
        <Award class="h-3.5 w-3.5" /> Verified Credentials
      </div>
      <h1 class="font-serif-display text-4xl font-extrabold sm:text-5xl">
        My <span class="brand-gradient-text">Certifications</span>
      </h1>
      <p class="mt-2 text-sm text-base-content/75">
        Click any certificate image to enlarge it, or select View Credentials to
        verify online.
      </p>
    </div>

    <section class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
      <ContentCard
        v-for="cert in certificates"
        :key="cert.title"
        :title="cert.title"
        :badge="cert.badge"
        :image="cert.image"
        :link="cert.link"
        link-label="View Credentials"
        :clickable-image="true"
        @preview="openPreview"
      />
    </section>

    <!-- DaisyUI Certificate Preview Modal (migrated from your script.js modal) -->
    <dialog :class="['modal', { 'modal-open': selectedCert }]">
      <div
        v-if="selectedCert"
        class="modal-box max-w-2xl border-2 border-primary bg-base-200 text-center"
      >
        <button
          @click="closePreview"
          class="btn btn-sm btn-circle btn-ghost absolute top-3 right-3 text-primary"
          aria-label="Close modal"
        >
          <X class="h-5 w-5" />
        </button>
        <img
          :src="selectedCert.image"
          :alt="selectedCert.title"
          class="mx-auto mt-4 w-full rounded-xl border border-primary/40"
        />
        <h3 class="font-serif-display mt-4 text-xl font-bold">
          {{ selectedCert.title }} — Certificate Preview
        </h3>
      </div>
      <form method="dialog" class="modal-backdrop" @click="closePreview">
        <button>close</button>
      </form>
    </dialog>
  </div>
</template>

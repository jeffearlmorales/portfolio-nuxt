<script setup lang="ts">
import {
  User,
  Mail,
  Phone,
  FileText,
  Send,
  CheckCircle2,
} from "lucide-vue-next";

useHead({
  title: "Contact Me | Jeff Earl Morales",
});

useSeoMeta({
  description:
    "Get in touch with Jeff Earl Morales for web development projects, collaborations, or inquiries.",
  ogTitle: "Contact Me | Jeff Earl Morales",
  ogDescription: "Send a direct message to web developer Jeff Earl Morales.",
});

const form = reactive({
  fullName: "",
  email: "",
  phone: "",
  subject: "",
  message: "",
});

const submitted = ref(false);

const handleSubmit = () => {
  submitted.value = true;
  setTimeout(() => {
    form.fullName = "";
    form.email = "";
    form.phone = "";
    form.subject = "";
    form.message = "";
  }, 400);
};
</script>

<template>
  <div class="mx-auto max-w-4xl space-y-8">
    <div class="text-center">
      <h1 class="font-serif-display text-4xl font-extrabold sm:text-5xl">
        Contact <span class="brand-gradient-text">Me</span>
      </h1>
      <p class="mt-2 text-base-content/75">
        Have a project in mind or want to connect? Send me a message below.
      </p>
    </div>

    <div
      v-if="submitted"
      role="alert"
      class="alert alert-success border border-success/40"
    >
      <CheckCircle2 class="h-5 w-5" />
      <span
        >Thank you! Your message has been recorded. You can also reach me
        anytime via LinkedIn or GitHub.</span
      >
    </div>

    <form
      @submit.prevent="handleSubmit"
      class="card border-2 border-primary/40 bg-base-200 p-6 sm:p-8 orange-glow"
    >
      <div class="grid gap-6 md:grid-cols-2">
        <!-- Left Input Group -->
        <div class="space-y-4">
          <label
            class="input input-bordered flex w-full items-center gap-2 border-primary/60 bg-base-100 focus-within:border-primary"
          >
            <User class="h-4 w-4 text-primary" />
            <input
              v-model="form.fullName"
              type="text"
              placeholder="Full Name"
              required
              class="grow"
            />
          </label>

          <label
            class="input input-bordered flex w-full items-center gap-2 border-primary/60 bg-base-100 focus-within:border-primary"
          >
            <Mail class="h-4 w-4 text-primary" />
            <input
              v-model="form.email"
              type="email"
              placeholder="Email"
              required
              class="grow"
            />
          </label>

          <label
            class="input input-bordered flex w-full items-center gap-2 border-primary/60 bg-base-100 focus-within:border-primary"
          >
            <Phone class="h-4 w-4 text-primary" />
            <input
              v-model="form.phone"
              type="tel"
              placeholder="Phone Number"
              class="grow"
            />
          </label>

          <label
            class="input input-bordered flex w-full items-center gap-2 border-primary/60 bg-base-100 focus-within:border-primary"
          >
            <FileText class="h-4 w-4 text-primary" />
            <input
              v-model="form.subject"
              type="text"
              placeholder="Subject"
              required
              class="grow"
            />
          </label>
        </div>

        <!-- Right Message Group -->
        <div class="flex flex-col justify-between gap-4">
          <textarea
            v-model="form.message"
            placeholder="Your Message"
            required
            class="textarea textarea-bordered h-48 w-full resize-none border-primary/60 bg-base-100 text-base focus:border-primary"
          ></textarea>

          <button
            type="submit"
            class="btn btn-primary w-full rounded-full text-base font-bold orange-glow"
          >
            <Send class="h-4 w-4" /> Send Message
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

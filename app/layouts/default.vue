<template>
  <div class="flex min-h-screen flex-col bg-base-100 text-base-content">
    <Navbar />
    <div class="flex flex-1">
      <Sidebar />
      <main class="mx-auto w-full max-w-6xl flex-1 px-5 py-10 md:px-10">
        <slot />
      </main>
    </div>
    <Footer />
  </div>
</template>

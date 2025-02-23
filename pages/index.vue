<script setup lang="ts">
const contacts = [
  {
    href: "https://x.com/SEED_dao",
    label: "{twit} @SEED_dao",
  },
  {
    href: "https://www.instagram.com/seed.computer/",
    label: "{inst} @seed.computer",
  },
  {
    href: null,
    label: "{mail} s.e.e.d_dao@protonmail.com",
  },
  {
    href: "https://warpcast.com/~/channel/seedcomputer",
    label: "{warp} seed channel",
  },
];
</script>

<template>
  <div class="h-full w-full flex flex-col items-center justify-center">
    <img class="px-10 pb-32" src="@/public/images/seed_logo.png" />
    <div class="absolute bottom-0 left-0 w-full flex flex-col px-4">
      <div
        class="w-full flex flex-col lg:flex-row lg:justify-between gap-2 pb-2"
      >
        <div class="flex flex-col gap-1">
          <div class="font-header text-sm">Contact us</div>

          <div class="flex flex-col gap-0.5">
            <div
              v-for="contact in contacts"
              class="font-header text-xs text-gray-400"
            >
              <a
                v-if="contact.href !== null"
                :href="contact.href"
                target="_blank"
                rel="noopener noreferrer"
                >{{ contact.label }}</a
              >
              <div v-else>{{ contact.label }}</div>
            </div>
          </div>
        </div>
        <div class="font-header text-sm text-gray-400 flex lg:items-end gap-1">
          by
          <a class="text-white" target="_blank" rel="noopener noreferrer">
            nas</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

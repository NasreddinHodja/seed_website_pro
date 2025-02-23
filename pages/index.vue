<template>
  <div
    class="h-full w-full flex flex-col items-center justify-center bg-blue-500"
  >
    <div v-for="(item, index) in Array(500).fill(0)">
      <div class="w-24">oie {{ index }}</div>
    </div>
  </div>
</template>

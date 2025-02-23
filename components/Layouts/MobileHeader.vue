<script setup lang="ts">
const route = useRoute();

const choices = HEADER_CHOICES;
const choicesOpen = ref(false);

const selectedItem = computed(() => {
  const to = `${route.path.split("/")[1]}`;
  const filteredChoices = choices.filter((choice) => {
    const choiceTo = choice.to.split("/")[1];
    return choiceTo === to;
  });
  return filteredChoices.length == 1 ? filteredChoices[0] : null;
});
</script>

<template>
  <div
    class="w-full font-header flex flex-col justify-center items-center gap-4 pb-2 pt-6 px-6"
  >
    <div class="w-full flex items-end justify-between">
      <NuxtLink to="/"><div class="text text-3xl flex">S.E.E.D.</div></NuxtLink>
      <div class="pb-1 flex justify-end">
        <NuxtLink to="/"
          ><img src="@/public/images/e_logo.jpg" class="w-24 min-w-24 ml-3"
        /></NuxtLink>
      </div>
    </div>

    <div
      class="w-full flex"
      v-click-outside="
        () => {
          choicesOpen = false;
        }
      "
    >
      <div class="w-full text-xl" @click="choicesOpen = !choicesOpen">
        <div class="flex grow justify-between gap-4">
          <div v-if="selectedItem">{{ selectedItem.label }}</div>
          <div v-else>HOME</div>
          <div v-if="choicesOpen">
            <Icon name="meteor-icons:chevron-up" />
          </div>
          <div v-else>
            <Icon name="meteor-icons:chevron-down" />
          </div>
        </div>
      </div>

      <div
        v-if="choicesOpen"
        class="absolute left-0 top-[125px] w-full flex flex-col transition px-6 py-6 z-50 bg-black"
      >
        <div class="w-full flex flex-col transition border-2 border-white p-4">
          <div
            v-for="(item, index) in choices"
            :key="index"
            :class="{
              'text-gray-500': item.to !== selectedItem?.to,
            }"
          >
            <NuxtLink :to="item.to">>{{ item.label }}</NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

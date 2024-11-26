<template>
  <UApp>
    <NuxtLayout>
      <ThemePicker />
      <NuxtPage />
    </NuxtLayout>
  </UApp>
</template>
<script setup lang="ts">
import colors from "tailwindcss/colors";

const appConfig = useAppConfig();
const colorMode = useColorMode();

const color = computed(() =>
  colorMode.value === "dark"
    ? (colors as any)[appConfig.ui.colors.neutral][900]
    : "white"
);

const radius = computed(
  () => `:root { --ui-radius: ${appConfig.theme.radius}rem; }`
);

useHead({
  meta: [
    { name: "viewport", content: "width=device-width, initial-scale=1" },
    { key: "theme-color", name: "theme-color", content: color },
  ],
  style: [{ innerHTML: radius, id: "nuxt-ui-radius", tagPriority: -2 }],
});
</script>

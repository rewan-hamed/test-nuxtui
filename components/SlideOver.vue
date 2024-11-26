<template>
  <USlideover side="left" prevent-close title="التصفية">
    <UButton label="Open" color="neutral" variant="subtle" />

    <template #body>
      <div>hello</div>
    </template>
    <template #footer>
      <UButton
        label="اعاده البحث"
        color="neutral"
        variant="outline"
        @click="open = false"
      />
      <UButton label="عرض النتائج" color="neutral" />
    </template>
  </USlideover>
</template>

<template>
  <div class="max-w-screen-sm mx-auto">
    <div class="prose dark:prose-invert">
      <ContentRenderer :value="data" />
    </div>
  </div>
</template>

<script setup lang="ts">
useHead({
  title: 'Privacy Policy' + ' – manjaro.org',
})

const route = useRoute()
const { data } = await useAsyncData(`${route.path}`, () => queryContent(route.path).findOne())

if (!data.value) {
  throw createError({ statusCode: 404, statusMessage: 'Page Not Found', fatal: true })
}
</script>

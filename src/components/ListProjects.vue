<script lang="ts" setup>
defineProps<{
  list: {
    text: string
    description?: string
    icon?: string
    image?: string
    href: string
  }[]
}>()
</script>

<template>
  <ul grid="~ cols-1 sm:cols-2 gap-4">
    <template v-if="!list || list.length === 0">
      <div py10 opacity-50 text-lg>
        nothing here yet.
      </div>
    </template>
    <li v-for="project in list" :key="project.text" container-link w-full flex items-center rd-2>
      <a flex items-center target="_blank" :href="project.href" :aria-label="project.text">
        <div ml-2 mr-4 pt-2>
          <i v-if="!project.image" text-4xl inline-block :class="project.icon || 'i-carbon-unknown'" />
          <img v-if="project.image && project.alt" :src="project.image" :alt="project.alt" style="width:198px" text-4xl>
        </div>
        <div font-normal lh-tight>
          <div text-lg hover:text-main>{{ project.text }}</div>
          <div opacity-90 text-sm>{{ project.description }}</div>
        </div>
      </a>
    </li>
  </ul>
</template>

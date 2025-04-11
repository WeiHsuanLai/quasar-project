<template>
  <q-item
    clickable
    v-bind="itemAttrs"                           
    :class="{ 'text-primary': isActive }"
  >
    <q-item-section avatar>
      <q-icon
        v-if="props.icon"
        :name="props.icon"
        :color="isActive ? 'primary' : 'grey-7'"
      />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{ props.title }}</q-item-label>
      <q-item-label caption>{{ props.caption }}</q-item-label>
    </q-item-section>
  </q-item>
</template>

<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router' 
const props = defineProps({
  title: String,
  caption: { type: String, default: '' },
  icon: { type: String, default: '' },
  to: { type: String, default: '' },
  link: { type: String, default: '' }
})

const route = useRoute()

const isActive = computed(() => {
  if (!props.to) return false
  // if (props.to === '/home') return route.path === '/home'
  return route.path.startsWith(props.to)
})

const itemAttrs = computed(() => {
  if (props.to) {
    return { to: props.to }
  }

  if (props.link) {
    return {
      tag: 'a',
      href: props.link,
      target: '_blank',
      rel: 'noopener'
    }
  }

  return {}
})
</script>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

defineOptions({
  name: 'SvgIcon'
})

const props = defineProps({
  url: {
    type: String,
    default: 'https://raw.gitmirror.com/xlovet/svgs/main/'
  },
  name: {
    type: String,
    default: 'regular/bahai'
  },
  size: {
    type: String,
    default: '1em'
  },
  color: {
    type: [Object, String],
    default: () => ({
      primary: 'currentColor',
      secondary: 'currentColor'
    })
  },
  opacity: {
    type: [Object, Number],
    default: () => ({
      primary: 1,
      secondary: 0.4
    })
  }
})

const iconRaw = ref('')

if (/^https?:/.test(props.url)) {
  axios
    .get(`${props.url}${props.name}.svg`)
    .then(res => (iconRaw.value = res.data))
} else {
  import(/* @vite-ignore */ `${props.url}${props.name}.svg`).then(
    res => (iconRaw.value = res.default)
  )
}
</script>

<template>
  <i v-html="iconRaw"></i>
</template>

<style scoped>
:deep(svg) {
  width: v-bind('props.size');
  height: v-bind('props.size');
  fill: v-bind('props.color');
  opacity: v-bind('props.opacity');

  --fa-primary-color: v-bind('props.color.primary');
  --fa-primary-opacity: v-bind('props.opacity.primary');
  --fa-secondary-color: v-bind('props.color.secondary');
  --fa-secondary-opacity: v-bind('props.opacity.secondary');
}
</style>

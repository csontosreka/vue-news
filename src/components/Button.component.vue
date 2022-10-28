<template>
  <button @click="toggleContent()">{{ title }}</button>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Button",
  props: {
    title: String
  },
  methods: {
    toggleContent() {
      this.$emit('toggle-content')
    }
  }
}
</script>
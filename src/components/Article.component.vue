<template>
  <div class="my-5 max-w-md rounded overflow-hidden shadow-lg" :article="article">
    <img class="w-full" :src=article.urlToImage alt="idk">
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2">{{article.title}}</div>
      <div class="text-lg mb-2 text-slate-400">{{article.author}}</div>
      <p class="text-gray-700 text-base">{{article.description}}</p>
      <p class="text-slate-400 text-base">{{article.publishedAt}}</p>
      <button class="font-semibold py-2 px-4 border border-blue rounded"
              @click="toggleContent">Read more...</button>
      <div v-if="isVisible" class="block text-gray-700">{{article.content}}</div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Article",
  props: {
    article: Object
  },
  data() {
    return {
      isVisible: false
    }
  },
  methods: {
    toggleContent() {
      this.isVisible = !this.isVisible
    }
  }
}
</script>
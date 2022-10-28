<template>
  <div class="grid place-items-center"
       v-for="(article, index) in articles" :key="index">
    <Article :article="article"/>
  </div>
</template>

<script>
import Article from "@/components/Article.component";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Articles",
  props: {
    articles: Array
  },
  components: {
    Article
  }
}
</script>
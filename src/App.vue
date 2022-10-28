<template>
  <SearchBar @nav-to-home="fetchCurrentNews()" @handle-submit="handleSubmit"/>
  <Articles v-if="isCurrentNewsLoaded === false" :articles="fetchCurrentNews()"/>
  <Articles :articles="news"/>

</template>

<script>
import SearchBar from "@/components/Searchbar.component";
import Articles from "@/components/Articles.component";

export default {
  name: 'App',
  components: {
    Articles,
    SearchBar
  },
  data() {
    return {
      apiKey: "60073e5abb1446cb80c7edd6858bf828",
      news: [],
      isCurrentNewsLoaded: false
    }
  },
  methods: {
    handleSubmit(query) {
      console.log('fetching query...')
      const url = `https://newsapi.org/v2/everything?q=${query}&sortBy=popularity&apiKey=${this.apiKey}`
      const req = new Request(url)

      fetch(req).then((res) => {
        return res.json()
      }).then(this.setResults)
    },
    setResults(results) {
      [...results.articles].map((article) => {
        article.publishedAt = article.publishedAt.slice(0, 10)
      })
      this.news = results.articles
    },
    fetchCurrentNews() {
      const url = `https://newsapi.org/v2/top-headlines?country=us&apiKey=${this.apiKey}`
      const req = new Request(url)

      fetch(req).then((res) => {
        console.log('fetching current...')
        this.isCurrentNewsLoaded = true
        return res.json()
      }).then(this.setResults)
    }
  }
}

</script>

<style>

</style>

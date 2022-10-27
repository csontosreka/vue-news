<template>
  <div class="flex bg-slate-600">
    <h1 class="pl-5 my-5 text-3xl text-white bold font-semibold">NewsSite</h1>
    <form class="flex mr-5 items-center max-w-md mx-auto shadow rounded border-0 p-3"
          @submit.prevent="handleSubmit">
      <input class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg block w-full pl-10 p-2.5"
          type="text" placeholder="Search for news..." v-model="query">
      <button class="p-2.5 ml-2 text-sm font-medium text-white bg-blue-500 rounded-lg border border-blue-500"><i class="fa fa-search"></i></button>
    </form>
  </div>
</template>

<script>
  export default {
    name: "SearchBar",
    data() {
      return {
        query: '',
      }
    },
    methods: {
      handleSubmit() {
        this.$emit('handle-submit', this.query)
      }
    }
  }
</script>
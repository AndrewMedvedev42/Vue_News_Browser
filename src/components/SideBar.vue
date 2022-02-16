<template>
  <section class="side_bar">
    <a v-bind:href="article.url" class="slot" v-for="article in articles" :key="article.publishedAt" target="_blank">
      <img class="image" v-bind:src="article.urlToImage" alt="image">
      <article class="news_details">
        <h1 class="article_title">{{article.title}}</h1>
        <p class="paragraph">{{article.description}}</p>
      </article>
    </a>
  </section>
</template>

<script>
export default {
  data(){
    return {
      articles:Array
    }
  },
  mounted(){
    fetch(`https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=${process.env.VUE_APP_NEWS_KEY}`)
      .then(res => res.json())
      .then(data=> this.articles = data.articles)
  }
}
</script>
<style scoped>
  .side_bar{
    padding: 1rem;
    width: 25%;
    display: flex;
    flex-direction:column;
  }
</style>
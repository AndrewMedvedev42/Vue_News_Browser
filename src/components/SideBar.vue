<template>
  <section class="side_bar">
    <a v-bind:href="article.url" class="slot" v-for="article in articles" :key="article.publishedAt" target="_blank">
      <img v-if="article.image_url" class="image" v-bind:src="article.image_url" alt="image">
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
    fetch(`https://newsdata.io/api/1/news?apikey=${process.env.VUE_APP_NEWS_KEY}&q=business`)
      .then(res => res.json())
      .then((data)=> {this.articles = data.results, console.log(data)})
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
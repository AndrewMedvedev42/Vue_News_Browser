<template>
  <section class="main_section">
    <nav class="search_section">
        <input type="text" @input="checkExist($event)" class="input_field" placeholder="search news">
    </nav>
    <section class="news_list">
        <a v-bind:href="article.url" class="slot" v-for="article in articles" :key="article.publishedAt" target="_blank">
        <img class="image" v-bind:src="article.urlToImage" alt="image">
        <article class="news_details">
            <h1 class="article_title article_big_title">{{article.title}}</h1>
            <p class="paragraph">{{article.description}}</p>
        </article>
        </a>
    </section>
  </section>
</template>

<script>
export default {
  data(){
    return {
      articles:Array,
      searchKeyword:""
    }
  },
  mounted(){
    fetch(`https://newsapi.org/v2/everything?q=everything&apiKey=${process.env.VUE_APP_NEWS_KEY}`)
      .then(res => res.json())
      .then(data=> this.articles = data.articles)
  },
  methods: {
       checkExist(event){
        fetch(`https://newsapi.org/v2/everything?q=${event.target.value ? (event.target.value):"everything"}&apiKey=${process.env.VUE_APP_NEWS_KEY}`)
        .then(res => res.json())
        .then(data=> this.articles = data.articles)
       } 
    
}
}
</script>
<style scoped>
    .main_section{
        padding: 1rem 1rem 1rem 0rem;
        width: 75%;
    }
    .news_list{
                display: flex;
        flex-direction:column;
    }
    .search_section{
        display: flex;
        justify-content: center;
        margin-bottom: 1rem;
    }
    .input_field{
        border-radius: 15px;
        border:none;
        padding: 0.5rem 1rem;
        font-size: 1.5rem;
        box-shadow: rgba(0, 0, 0, 0.25) 2.5px 2.5px 5px;
    }
</style>
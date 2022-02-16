<template>
  <section class="main_section">
    <nav class="search_section">
        <input type="text" @input="checkExist($event)" class="input_field" placeholder="search news">
    </nav>
    <section class="news_list">
        <a v-bind:href="article.url" class="slot main_slot" v-for="article in articles" :key="article.publishedAt" target="_blank">
        <img v-if="article.image_url"  class="image" v-bind:src="article.image_url" alt="image">
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
    fetch(`https://newsdata.io/api/1/news?apikey=${process.env.VUE_APP_NEWS_KEY}&q=apple`)
      .then(res => res.json())
      .then(data=> this.articles = data.results)
  },
  methods: {
       checkExist(event){
        fetch(`https://newsdata.io/api/1/news?apikey=${process.env.VUE_APP_NEWS_KEY}&q=${event.target.value ? (event.target.value):"everything"}`)
        .then(res => res.json())
        .then(data=> this.articles = data.results)
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
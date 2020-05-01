<template>
  <article>
    <div class="article" v-for="i in articleToShow" :key="i">
      <div class="article-header">
        <div class="img-holder">
          <img src="@/assets/images/author.png" alt="">
        </div>
        <div class="content">
          <h3>{{ articleCatcher(i,'title') }}</h3>
          <span>Friday December 16, 2019</span>
          <p>Fred the Slasher Designer</p>
        </div>
      </div>
      <div class="article-body">
        {{ articleCatcher(i,'body') }}
      </div>
    </div>
  </article>
</template>
<script>

export default {
  props: {
    articles: {
      type: Array
    },
    articleToShow: {
      type: Number,
    }
  },
  methods: {
    articleCatcher (a,b) {
      let _s = this
      // if the data not yet loaded don't call it so we can't get error 
      if (!_s.articles.length) return 
      
      if (b === 'title') {
        return _s.articles[a].title
      }
      if (b === 'body') {
        return _s.articles[a].body
      } 
    },
  },
}
</script>

<style scoped>
.article {
  background-color: #F4FAFF;
  border: 2px dashed #D4D8DB;
  padding: 15px;
  margin-bottom: 15px;
  border-top-right-radius: 2em;
  border-bottom-right-radius: 5px;
  border-top-left-radius: 2px;
  border-bottom-left-radius: 2em;
}

.article .article-header {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
  min-height: 80px;
}

.article .article-header .content {
  margin-left: 10px;
}

.article .article-header .content h3,
.article .article-header .content p {
  margin: 0;
}

.article .article-header .content span {
  display: block;
  font-size: 14px;
  color: #AAAAB0;
  margin-top: -5px;
}

.article .article-header .content p {
  margin-top: -2px;
  font-size: 16px;
  color: #9e5bc8
}

.article .article-header .img-holder {
  width: 80px;
  height: 80px;
  flex: 0 0 80px;
  overflow: hidden;
  border-radius: 70px;
  border: 1px solid #D4D8DB;
}
</style>
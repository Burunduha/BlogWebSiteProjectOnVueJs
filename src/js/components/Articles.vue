<template>
<div class="Articles text-dark">
            <div class="row">
                <main class="col-8">
                    <div class="row">
                        <div class="col-1">
                            <h1>Новости</h1>
                        </div>
                    </div>
                    <div class="row">
                        <div class="article-item mt-5 col-5 me-5 p-0 bg-white" v-for="article in displayedArticles" :key="article.id">
                            <img class="articleimg" :src="article.foto" alt="Article Image" />
                            <div class="article p-3">
                                <h1>{{ article.title }}</h1>
                                <p>{{ article.intro }}</p>
                                <button class="btn btn-warning">Читать далее</button>
                            </div>
                        </div>
                        
                        <button class="btn  mt-5 btn-load-more btn-warning mx-auto" v-if="showLoadMoreButton" @click="loadMore">Подгрузить еще</button>
                    </div>

                    <div class="row" v-if="moreArticles">
                        <div class="article-item mt-5 col-5 me-5 p-0 bg-white" v-for="el in articles" :key="el.id">
                            <img class="articleimg" :src="el.foto" alt="articleimg">
                            <div class="article p-3">
                                <h1>{{ el.title }}</h1>
                                <p>{{ el.intro }}</p>
                            </div>
                        </div>
                    </div>
                </main>
                <aside class="col-4">
                    <h1>Анонсы</h1>
                    <div class="bg-white p-3">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Magnam unde pariatur tempora nesciunt quibusdam alias fugit aperiam veniam commodi aliquid! Qui, sunt quia est eveniet maiores necessitatibus. Exercitationem, quis unde.</div>
                    <div class="mt-3 p-4 bg-info">
                        <img class="articleimg border border-5 mb-4" src="https://i.ytimg.com/vi/Hr5IOEQI7eg/maxresdefault.jpg" alt="">
                        <p class="text-white">Lorem ipsum dolor sit amet consectetur adipisicing elit. Ducimus ipsa nam porro, laudantium magni facilis asperiores iure, eligendi fugit dolorum illo nulla aspernatur commodi totam vero sed mollitia eaque blanditiis.</p>
                        <button class="btn btn-light">Читать далее</button>
                    </div>
                </aside>
             </div>
        </div>
</template>

<script>
export default {
    props: ['data'],
    created(){
        this.articles = this.data
    },
    data(){
        return {
            articles: [],
            displayedArticles: [], // Отображаемые статьи
            articlesPerPage: 4, // Количество статей на странице
            visibleArticles: 4 // Количество видимых статей
    };
  },
  computed: {
    showLoadMoreButton() {
        return this.visibleArticles < this.articles.length;
    }
  },
  mounted() {
    this.loadArticles();
  },
  methods: {
    loadArticles() {
      // Загрузка статей для текущей страницы
      this.displayedArticles = this.articles.slice(0, this.visibleArticles);
    },
    loadMore() {
      // Подгрузка следующей порции статей
      this.visibleArticles += this.articlesPerPage;
      this.loadArticles();
    }
  }

}

</script>

<style lang="scss" scoped>
    .articleimg {
        height: 150px;
        width: 366.66px;
    }
    .btn-load-more{
        width: 300px;
    }
</style>
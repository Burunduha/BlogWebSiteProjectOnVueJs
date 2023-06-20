<template>
    <header >
            <div class="container mt-3 p-3  bg-white border-bottom border-3 rounded-3">
                <div class="text-dark fs-5 ">
                    <div class="row">
                        <div class="logo col-2">
                            <div class="row">
                                <div class="col-6">
                                <img class="logoimg" src="IMG/Vector.svg" alt="">
                                </div>
                                <div class="col-1 mt-3">
                                    <span class="fs-4 fw-bolder">Burunduha</span> <br>
                                    <span class="fs-5 text-info fw-bold">Blog</span>
                                </div>
                            </div>
                        </div>
                        <div class="col-5 mt-4 text-end">
                            <div class="fullscreen-search" v-show="showSearch">
                                <h1 class="search-form text-info">Форма поиска</h1> 
                                <input ref="searchInput" type="text" class="form-control" placeholder="Поиск" @blur="closeSearch">
                                <span @click="toggleSearch" class="close-btn">&times;</span>
                            </div>
                             <input @click="openSearch" v-show="!showSearch" placeholder="Поиск" >
                        </div>
                            <div class="col-2 mt-4 text-end"> 
                                <button class="btn border btn-dark border-1">Главная</button>
                            </div>
                            <div class="col-1 mt-4"> 
                                <button class="btn border btn-dark border-1">Статьи</button>
                            </div>
                            <div class="col-1 mt-4"> 
                                <button class="btn border btn-dark border-1">Контакты</button>
                            </div>
                    </div>
                </div>
            </div> 
    </header>
</template>

<script>
export default{
    data() {
    return {
      showSearch: false
    };
  },
  methods: {
    openSearch() {
      this.showSearch = true;
      document.body.classList.add('no-scroll'); // Добавить класс для запрета прокрутки страницы
    },
    closeSearch() {
      this.showSearch = false;
      document.body.classList.remove('no-scroll'); // Удалить класс для разрешения прокрутки страницы
    },
    toggleSearch() {
      this.showSearch = !this.showSearch;
      if (this.showSearch) {
        this.$nextTick(() => {
          this.$refs.searchInput.focus();
        });
        document.body.classList.add('no-scroll'); // Добавить класс для запрета прокрутки страницы
      } else {
        document.body.classList.remove('no-scroll'); // Удалить класс для разрешения прокрутки страницы
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.logoimg {
    width: 100px;
    height: 100px;
    
    
    transition: transform 1s ease;
  
    &:hover {
      transform: rotate(360deg);
    }
  }
  .fullscreen-search {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;

  .search-form {
    position: absolute;
    top: 350px;
    left: 700px;
  }

  .form-control {
    width: 600px;
  }

  .close-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    color: #fff;
    cursor: pointer;
  }
}
.no-scroll {
  overflow: hidden !important;
}
</style>
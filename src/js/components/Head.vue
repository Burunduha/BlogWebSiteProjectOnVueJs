<template>
    <header>
      <div class="container mt-3 p-3 bg-white border-bottom border-3 rounded-3">
        <div class="text-dark fs-5">
          <div class="row align-items-center">
            <div class="col-md-2 col-6">
              <div class="row align-items-center">
                <div class="col-auto">
                  <img class="logoimg" src="IMG/Vector.svg" alt="">
                </div>
                <div class="col-auto mt-3">
                  <span class="fs-4 fw-bolder ml-2">Burunduha</span> <br>
                  <span class="fs-5 text-info fw-bold ml-2">Blog</span>
                </div>
              </div>
            </div>
            <div class="col-md-4 col-6 mt-4 text-end">
              <div class="fullscreen-search" v-show="showSearch">
                <h1 class="search-form text-info">Форма поиска</h1>
                <input ref="searchInput" type="text" class="form-control" placeholder="Поиск" @blur="closeSearch">
                <span class="close-btn" @click="toggleSearch">&times;</span>
              </div>
              <div v-show="!showSearch" class="position-relative">
                <input @click="openSearch" placeholder="Поиск" class="form-control">
                <span class="close-btn" @click="closeSearch" v-show="showSearch">&times;</span>
              </div>
            </div>
            <div class="col-md-2 col-4 mt-4">
              <button class="btn border btn-dark border-1 ">Главная</button>
            </div>
            <div class="col-md-2 col-4 mt-4">
              <button class="btn border btn-dark border-1 ">Статьи</button>
            </div>
            <div class="col-md-2 col-4 mt-4">
              <button class="btn border btn-dark border-1 ">Контакты</button>
            </div>
          </div>
        </div>
      </div>
    </header>
  </template>
  
  <script>
  export default {
    data() {
      return {
        showSearch: false
      };
    },
    methods: {
      openSearch() {
        this.showSearch = true;
        document.body.classList.add('no-scroll');
      },
      closeSearch() {
        this.showSearch = false;
        document.body.classList.remove('no-scroll');
      },
      toggleSearch() {
        this.showSearch = !this.showSearch;
        if (this.showSearch) {
          this.$nextTick(() => {
            this.$refs.searchInput.focus();
          });
          document.body.classList.add('no-scroll');
        } else {
          document.body.classList.remove('no-scroll');
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
    top: 40%;
    left: 40%;
    transform: translate(-50%, -50%);
  }

  .form-control {
    width: 100%;
    max-width: 600px;
  }

  .close-btn {
    position: absolute;
    top: 10%;
    right: 10%;
    color: #fff;
    cursor: pointer;
    z-index: 1;
  }
}

.no-scroll {
  overflow: hidden !important;
}
</style>
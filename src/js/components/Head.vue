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
                            <input type="text" class="searchinput" placeholder="Поиск">
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
</style>
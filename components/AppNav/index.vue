<template>
    <b-navbar toggleable="lg"  class="fixed bg-white shadow w-100 animate__animated animate__fadeInDown" >

    <b-navbar-brand href="#">
      <div  class="d-flex align-items-center">
        <img :src="require(`~/assets/icon/logo.svg`)" class="logo" alt="icon"/>
      </div>
    </b-navbar-brand>
    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>


    <b-collapse id="nav-collapse" class="justify-content-between " is-nav>

      <b-navbar-nav class="pr-0 NavBar mr-5  text-center justify-content-between align-items-center">
        <NuxtLink  to="/" tag="li" exact class="nav-link" >الرئيسية</NuxtLink >
        <NuxtLink to="#2" class="nav-link"> دورتنا</NuxtLink>
        <NuxtLink to="#3" class="nav-link"> احجز دورة</NuxtLink>
        <NuxtLink to="#4" class="nav-link"> قناة ابسطهالك</NuxtLink>
        <NuxtLink to="#5" class="nav-link">  تطبيق المبدع</NuxtLink>
        <NuxtLink to="#6" class="nav-link"> فريق المبدع</NuxtLink>
        <NuxtLink to="#7" class="nav-link">تواصل معنا</NuxtLink>
        <NuxtLink to="#8" class="nav-link"> اخر الاخبار</NuxtLink>

      </b-navbar-nav>

      <b-navbar-nav class="pr-0">
        <div class="d-flex btns">
          <b-button size="sm" class="btn btn_orange my-2 my-sm-2 mx-2 py-2 px-4 rounded_0" type="button" >تدرب معنا مجانا</b-button>
        </div>


      </b-navbar-nav>

    </b-collapse>

    </b-navbar>
</template>

<script>
export default {


};

</script>

<style scoped>
.fixed{
  position: fixed;
  z-index: 20000000000;
}
 .logo{
  width: 65px;
  margin-left: 5px;
 }
 .logoText{
   display: flex;
   flex-direction: column;
   font-size: 10px;
 }
 .nav-link{
  margin: 0 15px;
  color: var(--DarkGray) !important;
  cursor: pointer;
 }
 .nav-link:hover{
  color: var(--BlackColor) !important;
 }
 .nuxt-link-active{
   color: var(--DarkBlueColor) !important;
   position: relative;
   display: flex;
   flex-direction: column;
   align-items: center;
 }
 .NavBar .nuxt-link-active::after{
   content: url('~/assets/icon/active.svg');
   position: absolute;
   bottom: -15px;
 }


@media (max-width:1170px) {
  .nav-link{
    margin: 0 5px
  }
  .NavBar{
    margin-right: 0 !important;
  }
}
@media (max-width:989px) {

  .nav-link{
    margin: 5px 0;
  }
  .btns{
    justify-content: center;
    align-items: center;
  }
}
</style>

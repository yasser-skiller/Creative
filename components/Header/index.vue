<template>
    <b-container class="">
      <b-row align-h="center"  class="flex-wrap-reverse align-items-center ">
        <b-col cols="12" lg="6" class="position-relative m-sec animate__animated animate__fadeInRight">
          <img :src="require(`~/assets/img/header.png`)" class="header_img" alt="icon"/>

        </b-col>
        <b-col cols="12" lg="6" class="mt-5 p-5 animate__animated animate__fadeInLeft">
          <div class="w-100">
            <p class="text_orange font-weight-bold big_text">
              المبدع في القدرات
              <br/>
دليلك الأكيد الي القدرات
            </p>
            <img :src="require(`~/assets/icon/headerPath.svg`)" class="path" alt="icon"/>

          </div>

          <p class="mt-5 font-16">
            دورات المبدع في القدرات (القسم اللفظي) هي طريقك
 للحصول على 100 % بإذن الله
          </p>
          <div class="d-flex m-sec">
            <b-button size="sm" class="btn btn_orange my-3 my-sm-2  mx-2 py-3 px-5 ppp rounded_0" type="button" > دورات المبدع</b-button>
            <b-button size="sm" class="btn btn_light my-3 my-sm-2 mx-2 py-3 px-5 ppp rounded_0" type="button" >احجز دورة</b-button>
          </div>


        </b-col>
      </b-row>
    </b-container>
</template>

<script>
  import 'animate.css';
export default {

};

</script>

<style scoped>
.path{
  width: 75%;
  margin: 0;
}


.header_img{
  width: 100%;
}

@media (max-width:567px) {
  .ppp{
    padding: 15px 20px !important;
  }

}

</style>

<template>
    <b-container class="m-sec">

      <b-row align-h="center"  class="flex-wrap-reverse align-items-center ">

        <b-col cols="12" lg="6" class="p-5 animate__animated animate__fadeInLeft">
          <h4 class="font-weight-bold text_orange ">  تطبيق المبدع</h4>
          <p class="my-5">
            هذا النص هو مثال لنص يمكن أن يستبدل في نفس المساحة، لقد تم توليد هذا النص من مولد النص العربى، حيث يمكنك أن تولد مثل هذا النص أو العديد من النصوص الأخرى إضافة إلى زيادة عدد الحروف التى يولدها التطبيق.
          </p>

          <div class="GarkLine"></div>

          <p class="my-4 text_sec">يأتيكم قريبا باذن الله</p>

        </b-col>

        <b-col cols="12" lg="6" class="position-relative animate__animated animate__fadeInRight">
          <img :src="require(`~/assets/img/Group 406.png`)" class="header_img" alt="icon"/>
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

.header_img{
  width: 100%;
}
.GarkLine{
  width: 300px;
  height: 2px;
  background-color: var(--Dark);
}

@media (max-width:567px) {
  .GarkLine{
  width: 150px;
}
}

</style>

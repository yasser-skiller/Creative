<template>
  <div>
    <b-row align-h="center"  class="flex-wrap">
      <b-col
       cols="12" lg="6" class="my-4"
       v-for="item in data.secondary_courses" :key="item.id"
       v-on:click="$router.push({path:`/Session/${item.id}`})"
       >
        <div class="position-relative">
          <img :src="require(`~/assets/img/Group 2280.png`)" class="w-100" alt="icon"/>
          <div class="over">
            <div class="d-flex justify-content-between px-3">
              <h5 class="text-white" v-html="item.title"></h5>
              <div class="d-flex text-white"><h5 class="ml-1">مجانية</h5></div>
            </div>
            <div class="d-flex pr-3 mb-3">
              <img :src="require(`~/assets/icon/star (6).svg`)" class="" alt="icon"/>
              <p class="text-white my-0 mr-2">(5.0)</p>
            </div>
          </div>
        </div>
      </b-col>
    </b-row>

    <div class="d-flex flex-wrap justify-content-between w-100 mt-4 ">

      <div class="d-flex flex-wrap align-items-center text_dark bg_blue px-3 font-16">
        <img :src="require(`~/assets/icon/premium-quality.svg`)" class="ml-3" alt="icon"/>
        <p class="my-0 ">
          عند الاشتراك في الدورتين معا (التأسيس) - (المحوسب) تكون رسوم الشراء
        </p>
        <h5 class="font-weight-bold my-0 mr-1">250</h5>
        <small class="mr-1">ر.س</small>
        <p class="my-0 mx-1">بدلا من 300</p>
        <small>ر.س</small>
      </div>
      <b-button size="sm" class="btn btn_Dark my-2 py-3 px-5 mr-auto rounded_0" type="button" >  اشترك الان</b-button>

    </div>

    <div class="d-flex flex-wrap justify-content-between w-100 mt-4 ">

      <div class="d-flex flex-wrap align-items-center text_orange bg_oran px-3 font-16">
        <img :src="require(`~/assets/icon/video-player.svg`)" class="ml-3" alt="icon"/>
        <p class="my-0 ">
          خصم خاص لأول 100 مشرتك الدورة تكون ب 100 ر.س والدورتين تكون بسعر        </p>
        <h5 class="font-weight-bold my-0 mr-1">150</h5>
        <small class="mr-1">ر.س</small>
        <p class="my-0 mx-1">بدلا من 300</p>
        <small>ر.س</small>
      </div>
      <b-button size="sm" class="btn btn_Dark my-2 py-3 px-5 mr-auto rounded_0" type="button" >  اشترك الان</b-button>

      </div>
  </div>
</template>

<script>
export default {
  props: ["data"],

}
</script>

<style>
.over{
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  display: flex;
  flex-direction: column;
  justify-content: end;
}
.bg_blue{
  background-color: #ECF9FC;
  border: 1px solid #0F4C5C;
  border-radius: 10px;
}
.bg_blue img,
.bg_oran img{
  width: 50px;
}
.bg_oran{
  background-color: #FFE3D1;
  border: 1px solid #E36414;
  border-radius: 10px;
}
</style>

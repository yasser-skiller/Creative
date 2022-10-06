<template>
  <div class="d-flex flex-wrap justify-content-between align-items-center bg p-3">
    <img :src="require(`~/assets/icon/Group 2284.svg`)"  class="" alt="icon"/>

    <div class="rig pl-3">
      <h6 class="text_dark font-weight-bold">امتحان الكتروني اونلاين</h6>
      <p>امتحان من 25 سؤال</p>
    </div>
    <p class="w-50">
      هذا النص هو مثال لنص يمكن أن يستبدل في نفس المساحة، لقد تم توليد هذا النص من مولد النص العربى، حيث يمكنك أن تولد مثل هذا النص
    </p>

    <b-button class="btn btn_orange rounded_0 px-5 py-3 "> ابدا الامتحان الان</b-button>

  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
  .bg{
    background-color: #F6F4F4;
    border-radius: 20px;
  }
  .rig{
    border-left: 1px solid #8E8F9B;
  }
</style>

<template>
  <div>
    <div v-if="Number.isInteger(CurentLessons_data.quiz_id) === true" class="d-flex flex-wrap justify-content-between align-items-center bg p-3">
      <img :src="require(`~/assets/icon/Group 2284.svg`)"  class="" alt="icon"/>

      <div class="rig pl-3">
        <h6 class="text_dark font-weight-bold">امتحان الكتروني اونلاين</h6>
        <p>امتحان من .... سؤال</p>
      </div>
      <p class="w-50">
        هذا النص هو مثال لنص يمكن أن يستبدل في نفس المساحة، لقد تم توليد هذا النص من مولد النص العربى، حيث يمكنك أن تولد مثل هذا النص
      </p>

      <b-button v-on:click = "$router.push({path:`/Quiz/${CurentLessons_data.quiz_id}`})" class="btn btn_orange rounded_0 px-5 py-3 "> ابدا الامتحان الان</b-button>

    </div>
    <div v-else>
      <h5 class="text-center">لا يوجد اختبار</h5>
    </div>
  </div>

</template>

<script>
export default {
props:['CurentLessons_data']
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

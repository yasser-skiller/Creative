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

      <b-button v-on:click = "ChangePath(CurentLessons_data.quiz_id)" v-b-modal.modal-Quiz class="btn btn_orange rounded_0 px-5 py-3 "> ابدا الامتحان الان</b-button>

      <b-modal id="modal-Quiz" title="اختر نظام الاختبار" hide-footer>
        <div class="d-flex flex-wrap justify-content-center">
          <div v-on:click = "ChosseNewPath()" class="bgGreen rounded block m-2">
            <p class="my-4 text-white font-16">الأختبار</p>
            <img :src="require(`~/assets/icon/lateww.svg`)" alt="img" class="clock_img"/>
          </div>

          <div v-on:click = "ChosseOldPath()" class="bluebg  rounded block m-2">
            <p class="my-4 text-white font-16">اختبار بنظام محاكي</p>
            <img :src="require(`~/assets/icon/lateww.svg`)" alt="img" class="clock_img"/>
          </div>
        </div>

      </b-modal>

    </div>
    <div v-else>
      <h5 class="text-center">لا يوجد اختبار</h5>
    </div>
  </div>

</template>

<script>
export default {
props:['CurentLessons_data'],
data() {
    return {
      path_id : '',
    }
  },
  methods:{
  ChangePath(id){
    this.path_id = id;
    if(screen.width <= 992){
      this.$router.push({path:`/Quiz/${id}`})
    }
  },
  ChosseNewPath(){
    this.$router.push({path:`/Quiz/${this.path_id}`})
  },
  ChosseOldPath(){
    this.$router.push({path:`/OldStyleQuiz/${this.path_id}`})
  },
}
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
  .block{
  width: 170px;
  height: 140px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
.bluebg{
  background-color: #036B98;
}
.bgGreen{
  background-color: #039A7B;
}
.clock_img{
  width: 25px;
  margin: auto;
}
</style>

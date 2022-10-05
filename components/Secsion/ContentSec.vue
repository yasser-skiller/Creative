<template>
  <div>
    <p>محتوي الدورة المحوسبة </p>

    <div class=" rounded_0 border my-4">
        <div class="d-flex justify-content-between align-items-center bgRed p-3 rounded_0">

          <div class="d-flex align-items-center cursor_pointer" v-on:click="Up = !Up">
            <img :src="require(`~/assets/icon/downUP.svg`)"  :class="Up === true ? 'd-block downUP cursor_pointer' : 'd-none'" alt="icon"/>
            <img :src="require(`~/assets/icon/upDown.svg`)"  :class="Up === false ? 'd-block downUP cursor_pointer' : 'd-none'" alt="icon"/>
            <p class="font-weight-bold my-0 mr-2">القسم الاولي: مقدمة عن كورس ودورة المحوسب</p>
          </div>

          <p class="my-0 text_orange font-weight-bold">عدد 3 فيديوهات - 15 دقيقة</p>

        </div>

        <div :class="Up === false ? 'd-block p-2' : 'd-none'">
          <div class="d-flex justify-content-between align-items-center my-4">
            <div class="d-flex align-items-center">
              <img :src="require(`~/assets/icon/Group 2282.svg`)" class="iconCheck" alt="icon"/>
              <p class="my-0 mr-2">   عنوان الفيديو الكامل بالنص هنا علي حسب الدورة </p>
            </div>
            <p class="my-0 text_green"><span class="gray">وقت الفيديو :</span> <span class="font-weight-bold">04:05</span></p>
          </div>

          <div class="d-flex justify-content-between align-items-center my-4">
            <div class="d-flex align-items-center">
              <img :src="require(`~/assets/icon/Group 2283.svg`)" class="iconCheck" alt="icon"/>
              <p class="my-0 mr-2">   عنوان الفيديو الكامل بالنص هنا علي حسب الدورة </p>
            </div>
            <p class="my-0 text_green"><span class="gray">وقت الفيديو :</span> <span class="font-weight-bold">04:05</span></p>
          </div>

          <div class="d-flex justify-content-between align-items-center my-4">
            <div class="d-flex align-items-center">
              <img :src="require(`~/assets/icon/Group 2283.svg`)" class="iconCheck" alt="icon"/>
              <p class="my-0 mr-2">   عنوان الفيديو الكامل بالنص هنا علي حسب الدورة </p>
            </div>
            <p class="my-0 text_green"><span class="gray">وقت الفيديو :</span> <span class="font-weight-bold">04:05</span></p>
          </div>

          <div class="d-flex justify-content-between align-items-center my-4">
            <div class="d-flex align-items-center">
              <img :src="require(`~/assets/icon/Group 2283.svg`)" class="iconCheck" alt="icon"/>
              <p class="my-0 mr-2">   عنوان الفيديو الكامل بالنص هنا علي حسب الدورة </p>
            </div>
            <p class="my-0 text_green"><span class="gray">وقت الفيديو :</span> <span class="font-weight-bold">04:05</span></p>
          </div>


        </div>



      </div>
  </div>
</template>


<script>
  export default {
    data() {
        return {
        Up: false,
      }
    },

  };

  </script>


<style scoped>
  .bgRed{
    background-color: #FFEAE3;
  }
  .video{
    position: relative;
  }
  .gray{
    color: #8E8F9B;
  }

</style>

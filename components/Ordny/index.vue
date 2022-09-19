<template>
    <b-container class="m-sec">
      <h4 class="font-weight-bold text_orange text-center animate__animated animate__fadeInRight">ترتيب دخول الدورات</h4>
      <p class="text-center my-3">
        في ثلاث (3) خطوات رئيسية
      </p>
      <b-row align-h="center"  class="flex-wrap-reverse align-items-center ">
        <b-col cols="8" sm="9" md="8" lg="7" class="position-relative animate__animated animate__fadeInRight">
          <img :src="require(`~/assets/img/Group 14190.png`)" class="header_img" alt="icon"/>
        </b-col>

        <b-col cols="4" sm="3" md="4" lg="5" class="parent animate__animated animate__fadeInLeft">
            <div >
              <p class="text_orange">دورة التأسيس</p>
              <p class="">هي دورة للتأسيس في القدرات ومعرفة أساسيات القدرات من الصفر للاحتراف</p>
            </div>

            <div >
              <p class="text_orange">دورة المحوسب </p>
              <p>دورة للاستعداد للاختبار المحوسب وحل تجميعات وأسئلة تأتي في الاختبار مع تحديثات دائمة وملفات شاملة لتأهيل الطالب لدخول الاختبار </p>
            </div>

            <div >
              <p class="text_orange">دخول الاختبار المحوسب </p>
              <p>الاختبار والخطوه الاخيره في الخطاوت تحصل على 100% بإذن الله</p>
            </div>

        </b-col>
      </b-row>
    </b-container>
</template>


<style scoped>

.header_img{
  width: 100%;
  height: 800px;
}

.parent{
  width: 100%;
  height: 800px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 60px;
  padding-bottom: 25px;
}

@media (max-width:768px) {
  .header_img{
    height: 650px;
  }

  .parent{
    height: 700px;
  }
}

@media (max-width:568px) {
  .header_img{
    height: 650px;
  }

  .parent{
    padding-right: 0;
  }
}

@media (max-width:400px) {
  .header_img{
    height: 600px;
  }

  .parent{
    padding-right: 0;
    height: 700px;
  }
}

</style>

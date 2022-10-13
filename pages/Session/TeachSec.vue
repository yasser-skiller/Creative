<template>
  <div>
    <div class="d-flex  flex-wrap">

      <div class="d-flex flex-wrap align-items-center">
        <img :src="require(`~/assets/img/Group 1970.png`)" class="w_img my-2" alt="icon"/>

        <div class="ml-5 mr-3 my-2">
          <h5 class="font-weight-bold text_orange">
            د/ السيد جاد الله
          </h5>
          <p class="gray">حاصل علي شهادة نص تكملة</p>
        </div>

        <div class="d-flex my-2 right_border">
          <img :src="require(`~/assets/icon/telegram.svg`)" class="so_icon" alt="icon"/>
          <img :src="require(`~/assets/icon/snapchat (2).svg`)" class="so_icon" alt="icon"/>
          <img :src="require(`~/assets/icon/whatsapp (6).svg`)" class="so_icon" alt="icon"/>
          <img :src="require(`~/assets/icon/facebook (4).svg`)" class="so_icon" alt="icon"/>
        </div>
      </div>

      <div class="d-flex align-items-center mx-4 my-2">
        <img :src="require(`~/assets/icon/Group 1995.svg`)" class="ml-3" alt="icon"/>
        <p class="my-0 right_border">000000000000000000</p>

      </div>

      <div class="d-flex align-items-center mx-4 my-2 ">
        <img :src="require(`~/assets/icon/Group 1994.svg`)" class="ml-3" alt="icon"/>
        <p class="my-0">e-mail@hot.com</p>

      </div>


    </div>

    <p class="mt-5">
        الحمد لله الذي بنعمته تتم الصالحات ، والصلاة والسلام على سيد الخلق والأنبياء ، وعلى آله وأصحابه الطيبين وبعد منذ أن بدأنا دوراتنا ونحن نعمل بجهد على توفير بيئة جيدة ومحتوى قوي للدورات بحيث يتعلم الطالب أساسيات القدرات ويحل تجميعات وأسئلة تأتي في الاختبار مع أحدث الأسئلة والتقفيلات والنماذج وقد كان ذلك جليا عند ظهور نموذج الخوارزمي وحصول الطلاب فيه على درجات متدنية فقد اجتهدنا وشرحنا النموذج في 4 فيديوهات مع أحدث الأسئلة لرفع درجة النموذج وقد حدث بالفعل ومن مميزات دوراتنا قوة المحتوى ووجود فريق خاص لإدارة الدورات وتجهيز فيديوهات شرح بجودة عالية تليق بكم والرد على استفساراتكم ووجود اختبارات إلكترونية تحاكي الاختبار المحوسب بحيث يدخل الطالب الاختبار وهو على أرض صلبة حتى يحصل على الدرجة النهائية بإذن الله شاهد قناتنا على اليوتيوب وشاهد مستوى الشرح وقوة المحتوى
    </p>


  </div>
</template>
<script>
import LastNews from '@/components/LastNews';


export default {
  components:{
    LastNews,
  },
}
</script>

<style scoped>
  .gray{
    color: #8E8F9B;
  }
.right_border{
  border-left: 2px solid #8E8F9B;
  padding-left: 20px;
}
.so_icon{
  width: 25px;
  margin: auto 5px;
}
.w_img{
  width: 100px;
}
</style>

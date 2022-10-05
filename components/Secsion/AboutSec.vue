<template>
  <div>
    <p>
      الحمد لله الذي بنعمته تتم الصالحات ، والصلاة والسلام على سيد الخلق والأنبياء ، وعلى آله وأصحابه الطيبين وبعد منذ أن بدأنا دوراتنا ونحن نعمل بجهد على توفير بيئة جيدة ومحتوى قوي للدورات بحيث يتعلم الطالب أساسيات القدرات ويحل تجميعات وأسئلة تأتي في الاختبار مع أحدث الأسئلة والتقفيلات والنماذج وقد كان ذلك جليا عند ظهور نموذج الخوارزمي وحصول الطلاب فيه على درجات متدنية فقد اجتهدنا وشرحنا النموذج في 4 فيديوهات مع أحدث الأسئلة لرفع درجة النموذج وقد حدث بالفعل ومن مميزات دوراتنا قوة المحتوى ووجود فريق خاص لإدارة الدورات وتجهيز فيديوهات شرح بجودة عالية تليق بكم والرد على استفساراتكم ووجود اختبارات إلكترونية تحاكي الاختبار المحوسب بحيث يدخل الطالب الاختبار وهو على أرض صلبة حتى يحصل على الدرجة النهائية بإذن الله شاهد قناتنا على اليوتيوب وشاهد مستوى الشرح وقوة المحتوى
    </p>
    <h5 class="text_orange mt-4">
      تقييم الدورة
    </h5>
    <div class="d-flex">
      <img :src="require(`~/assets/icon/star (12).svg`)" class="star" alt="icon"/>
      <img :src="require(`~/assets/icon/star (12).svg`)" class="star" alt="icon"/>
      <img :src="require(`~/assets/icon/star (12).svg`)" class="star" alt="icon"/>
      <img :src="require(`~/assets/icon/star (12).svg`)" class="star" alt="icon"/>
      <span class="mr-5">تقييم الدورة (5.0)</span>

    </div>
    <LastNews/>
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
.star{
  width: 20px;
  margin: auto 5px;
}
</style>

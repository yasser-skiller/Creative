<template>
    <b-container class="m-sec">
      <h4 class="font-weight-bold text_orange text-center animate__animated animate__fadeInRight">دورات المبدع</h4>
      <p class="text-center my-3">
        اشترك الآن في إحدى دوراتنا واحظ بالعديد من المميزات الحصرية والملفات الهامة وفيديوهات الشرح عالية المستوى<br/> وكن من طلابنا الحاصلين على 100 % إن شاء الله
      </p>
      <div v-if="this.PublishedCourses_data.length > 0 ">
        <b-row align-h="center"  class="flex-wrap align-items-center">
          <b-col
           cols="10" sm="10" md="8"  lg="6"
           class="mb-4 py-2 px-4 animate__animated animate__fadeInRight"
           v-for="item in PublishedCourses_data" :key="item.id"

           >
            <div class="parent">
              <img :src="item.image" class="w-100" alt="icon"/>
              <div class="overly">
                <div class="d-flex bgRed my-3 mx-3 p-2 rounded_0" >
                  <img :src="require(`~/assets/icon/share.svg`)" class="icon" alt="icon"/>
                </div>
              </div>
            </div>
            <div class="bgGray shadow p-2">
              <div class="d-flex flex_sm_wrap justify-content-between ">
                <div class="d-flex m-2  rounded_0" >
                  <img :src="require(`~/assets/icon/logo.svg`)" class="icon" alt="icon"/>
                  <h6 class="text_orange mr-2 mt-2 font-weight-bold" v-html="item.name">  </h6>
                </div>
                <div class="d-flex align-items-center bgYellow m-2 py-1 px-2 py-0 rounded_0" >
                  <img :src="require(`~/assets/icon/star.svg`)" class="icon m-0 p-0" alt="icon"/>
                  <span class="text-white m-0 mr-1 p-0 ">(5.0)</span>
                </div>
              </div>
              <div class="d-flex flex_sm_wrap justify-content-between align-items-end">
                <div>
                  <div class="d-flex align-items-center">
                    <img :src="require(`~/assets/icon/online-learning (1).svg`)" class="icon" alt="icon"/>
                    <p class="m-0 mr-3">شرح جميع نماذج المحوسب بأدق الصيغ والتفيلات</p>
                  </div>
                  <div class="d-flex align-items-center my-3">
                    <img :src="require(`~/assets/icon/file (1).svg`)" class="icon" alt="icon"/>
                    <p class="m-0 mr-3">اختبارت الكترونية وملفات لمحتوي الدورة</p>
                  </div>
                  <div class="d-flex align-items-center">
                    <img :src="require(`~/assets/icon/e-learning (1).svg`)" class="icon" alt="icon"/>
                    <p class="m-0 mr-3">ملخصات ومراجعات والمزيد داخل الدورة</p>
                  </div>
                </div>
                <b-button v-on:click="$router.push({path:`/Session/${item.id}`})" size="sm" class="btn btn_Dark fit-content mt-3 py-3  mx-2  px-5 ppp rounded_0" type="button" >  الذهاب للدورة</b-button>
              </div>
            </div>

          </b-col>

        </b-row>
      </div>
      <div v-else class="d-flex justify-content-center align-items-center spinner_loading">
        <Loading/>
      </div>

    </b-container>
</template>

<script>
  import config from "@/config";
  import Loading from "@/components/Loading";

export default {
  components:{
    Loading,
  },
  data (){
    return {
      PublishedCourses_data: [],
    }
  },
  mounted() {
    this.fetchCourses();

  },
  methods: {
    fetchCourses() {
      var myHeaders = new Headers();
      myHeaders.append("Authorization", `Bearer${config.token}`);

      var requestOptions = {
        method: 'GET',
        headers: myHeaders,
        redirect: 'follow'
      };

      fetch(config.apiUrl+"wp-json/learnpress/v1/courses", requestOptions)
        .then(response => response.text())
        .then(result => {
          this.PublishedCourses_data_method(JSON.parse(result));
        })
        .catch(error => console.log('error', error));
    },
    PublishedCourses_data_method(Courses_data){
      setTimeout(() => {
        Courses_data.forEach(element => {
          if(element.show_in_homepage === true ){
            if(element.status === 'publish'){
              this.PublishedCourses_data.push(element)
            }
          }
        });
      }, 4000);

    },
  },
};

</script>

<style scoped>
.parent{
  position: relative;
}
.overly{
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background-image: url('~/assets/img/Rectangle.png');
  width: 100%;
  display: flex;
  justify-content: end;
  align-items: flex-start;
}
.icon{
  width: 15px;
}
@media (max-width:768px) {
  .flex_sm_wrap{
    flex-wrap: wrap;
  }
}
</style>

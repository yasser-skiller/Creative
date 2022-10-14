<template>
  <div>
    <AppNav/>
    <b-container>
      <div v-if="this.Quiz_data.length > 0 ">
        <b-row align-h="center"  class="flex-wrap-reverse mb-5">
          <b-col cols="12" lg="6" class="m-sec">
            <p class="text-c">عداد الاسئلة :<span class="font-weight-bold text_orange bgfillOrange rounded px-3 py-2 mx-2">{{Quiz_serial+1}}</span>من <span class="font-weight-bold bgfillGrag rounded px-3 py-2 mx-2">{{Quiz_data.length}}</span></p>

            <b-progress class="mt-4">
              <b-progress-bar :value="(Quiz_serial+1)*100/Quiz_data.length"></b-progress-bar>
            </b-progress>

            <div class="d-flex justify-content-between align-items-center mb-5">

              <AddFoldersList :Quiz_data="Quiz_data" :Quiz_serial="Quiz_serial"/>


              <div
              class="d-flex bgGray0 width_30 rounded_0 mt-3 p-2 font-16 cursor_pointer"
              v-on:click="Favorite(Quiz_data[Quiz_serial])"
              >
                <span class="pl-5">السؤال في المفضلة</span>
                <img :src="HeartCase === false ? require(`~/assets/icon/add-to-favorites0.svg`) : require(`~/assets/icon/add-to-favorites.svg`)" class="icon_sm mr-auto" alt="icon"/>
              </div>

            </div>


            <p class="mt-4">اختر من الإجابات التالية</p>

            <div
              v-for="option in Quiz_data[Quiz_serial].options"
              :key="option.uid"
              :id="option.value"
              :class="`optionItem class${option.value}`"
              v-on:click="Save(Quiz_data[Quiz_serial].id, option.value, Quiz_serial)"
            >
              <label
              :for="option.uid"
              >
              {{option.title}}
              </label>
              <b-form-radio
                v-model="selected"
                :id="`${option.uid}`"
                class="d-none"
                :value="option.value"
              >
              </b-form-radio>
            </div>

            <!-- <div class="mt-3 ">Selected: <strong>{{ selected }}</strong></div> -->

            <div class="d-flex flex-wrap justify-content-center">
              <b-button size="sm" class="btn btn_light my-2 py-2 px-5 ml-4 rounded_0" type="button" v-if="Quiz_serial > 0 " v-on:click="Previous"> السابق</b-button>
              <b-button size="sm" class="btn btn_gradient my-2 py-2 px-5 rounded_0 mx-5" type="button" v-if="Quiz_serial !== Quiz_data.length-1 " v-on:click="Next"> التالي</b-button>
              <b-button size="sm" class="btn btn_gradient my-2 py-2 px-5 rounded_0 mx-auto" type="button" v-on:click="Finish_Quiz">إنهاء الاختبار</b-button>
            </div>

          </b-col>
          <b-col cols="12" lg="5" class="m-sec bgGray p-3">

            <div class="gridSy">

              <div class="">

                <div class="d-flex align-items-center mr-auto fit_width ">
                  <img :src="require(`~/assets/icon/clock5.svg`)" class="" alt="icon"/>
                  <span class="mx-1"> توقيت:</span>
                  <span class="py-1 px-2 font-16 time rounded_0  text_DarkRedColor">{{Quiz_duration}}</span>
                </div>

                <h5 class="font-weight-bold text_orange my-3" v-html="Quiz_data[Quiz_serial].title"></h5>

                <p>
                  هذا النص هو مثال لنص يمكن أن يستبدل في نفس المساحة، لقد تم توليد هذا النص من مولد النص العربى، حيث يمكنك أن تولد مثل هذا النص أو العديد من النصوص الأخرى إضافة إلى زيادة عدد الحروف التى يولدها التطبيق.
                إذا كنت تحتاج إلى عدد أكبر من الفقرات يتيح لك مولد النص العربى زيادة عدد الفقرات كما تريد، النص لن يبدو مقسما ولا يحوي أخطاء لغوية، مولد النص العربى مفيد لمصممي المواقع على وجه الخصوص، حيث يحتاج العميل فى كثير من الأحيان أن يطلع على صورة حقيقية لتصميم الموقع    .
                </p>
              </div>

              <div
              class="d-flex btn_sec rounded_0 fit_width px-5 py-2 mt-5 mx-auto font-16 cursor_pointer"
              v-on:click="Pass(Quiz_data[Quiz_serial])"
              >
              <img :src="PassCase === false ? require(`~/assets/icon/late0.svg`) : require(`~/assets/icon/late.svg`)" class="icon ml-3" alt="icon"/>
              <span class="text_blue">تأجيل السؤال</span>
              </div>

            </div>


          </b-col>
        </b-row>

      </div>
      <div v-else class="d-flex justify-content-center align-items-center spinner_loading">
        <Loading/>
      </div>
  </b-container>

  </div>

</template>


<script>
import Loading from "@/components/Loading";
import AppNav from '@/components/AppNav';
import AddFoldersList from "@/components/AddFoldersList";

  export default {
    components:{
      Loading,
      AppNav,
      AddFoldersList
    },
    data() {
      return {
        Quiz_data: [],
        Answered_obj : {},
        Answered:[],
        Favorite_Quiz:[],
        Pass_Quiz:[],
        selected: '',
        status_code: '',
        Quiz_serial:0,
        HeartCase: false,
        Favorite_Quiz :[],
        PassCase:false,
        Pass_Quiz :[],
        Result :[],
      }
    },
    mounted() {
      this.CurrentState();
      setTimeout(() => {
        this.Compare();
      }, 2000);
    },
    methods: {
      CurrentState(){
        this.Pass_Quiz = JSON.parse(localStorage.getItem(`Pass_Quiz_${this.$route.params.slug}`));
        this.Favorite_Quiz = JSON.parse(localStorage.getItem(`Favorite_Quiz_${this.$route.params.slug}`));
        this.Answered = JSON.parse(localStorage.getItem(`Answered_${this.$route.params.slug}`));
        this.Quiz_data = JSON.parse(localStorage.getItem(`Quiz_data_${this.$route.params.slug}`));
        this.Result = JSON.parse(localStorage.getItem(`Result_${this.$route.params.slug}`));
        if(JSON.parse(localStorage.getItem(`Quiz_serial${this.$route.params.slug}`)) !== null){
          this.Quiz_serial = JSON.parse(localStorage.getItem(`Quiz_serial${this.$route.params.slug}`))
        }
        console.log("localStorage_Answered",this.Answered)
      },
      Compare(){
        setTimeout(() => {
          if(this.Answered.length > 0){
          this.Answered.forEach(element => {
            if(element.my_Quiz_serial === this.Quiz_serial){
              if(this.Result.results.answered[element.id].correct === true){
                // this.selected = element.answer
                document.querySelector(`.class${element.answer}`).classList.add('selected')
              }
              if(this.Result.results.answered[element.id].correct === false){
                this.Result.results.answered[element.id].options.forEach(ele => {
                  if(ele.is_true === 'yes'){
                    document.querySelector(`.class${ele.value}`).classList.add('selected')
                    // this.selected = ele.value
                  }
                });
                document.querySelector(`.class${this.Result.results.answered[element.id].answered.answered}`).classList.add('Wrongselected')

              }
            }else{
              this.Result.results.answered[this.Quiz_data[this.Quiz_serial].id].options.forEach(ele => {
                if(ele.is_true === 'yes'){
                  document.querySelector(`.class${ele.value}`).classList.add('selected')
                }
                if(ele.value === this.Result.results.answered[this.Quiz_data[this.Quiz_serial].id].answered.answered){
                  document.querySelector(`.class${ele.value}`).classList.add('Wrongselected')
                }
              });
            }
          });
        }

        }, 500);
        //Favorite
        this.HeartCase = false;
        this.Favorite_Quiz.forEach(element => {
          if(element.id === this.Quiz_data[this.Quiz_serial].id){
            this.HeartCase = true;
          }
        });

        //Pass
        this.PassCase = false;
        this.Pass_Quiz.forEach(element => {
          if(element.id === this.Quiz_data[this.Quiz_serial].id){
            this.PassCase = true;
          }
        });

        //FoldersListCheckbox
        document.querySelectorAll('.FoldersListCheckbox input').forEach(element => {
          element.checked = false
        });

    },

    Next(){
      this.Quiz_serial++ ;
      this.Compare();
    },
    Pass(item){
      this.PassCase = !this.PassCase;
      if(this.PassCase === true){
        this.Pass_Quiz.push(item)
      }
      if(this.PassCase === false){
        console.log("Pass_Quiz false")
        this.Pass_Quiz =  this.Pass_Quiz.filter(e =>  e.id !== item.id)
      }
      console.log("Pass_Quiz",this.Pass_Quiz)
      console.log("item",item)
    },
    Previous(){
      this.Quiz_serial-- ;
      this.Compare();
    },
    Finish_Quiz(){
      localStorage.setItem(`Answered_${this.$route.params.slug}`, JSON.stringify(this.Answered));
      localStorage.setItem(`Favorite_Quiz_${this.$route.params.slug}`, JSON.stringify(this.Favorite_Quiz));
      localStorage.setItem(`Pass_Quiz_${this.$route.params.slug}`, JSON.stringify(this.Pass_Quiz));
      this.$router.push({path:`/ResultsRevsion/${this.$route.params.slug}`});
    },
    Favorite(item){
      this.HeartCase = !this.HeartCase;
      if(this.HeartCase === true){
        this.Favorite_Quiz.push(item)
      }
      if(this.HeartCase === false){
        console.log("Favorite_Quiz false")
        this.Favorite_Quiz =  this.Favorite_Quiz.filter(e =>  e.id !== item.id)
      }
      console.log("Favorite_Quiz",this.Favorite_Quiz)
    },


  },


  }
</script>

<style scoped>
  .spinner_loading{
    height: 90vh;
  }
 .progress{
  background-color: var(--Gray);
  height: .5rem;
 }
 .progress-bar{
  background-color: var(--Dark);
 }
 .optionItem{
  font-size: 16px;
  background-color: #F3F3F3;
  width: 100%;
  margin: 15px auto;
  padding: 7px 9px 0px 0px;
  border: 1px #B2B2B2 solid;
  border-radius: 12px;
  color: #363848;
  cursor: pointer;
 }
 .px-r{
  padding-right: 70px !important;
 }
 .px-l{
  padding-left: 70px !important;
 }


 label{
  width: 100%;
  height: 100%;
  cursor: pointer;
 }
 .selected{
  color: var(--YellowColor);
  border-color: var(--YellowColor);

 }

 .time{
  background-color: #ECECEC;
  border: 1px solid var(--DarkRedColor);
 }


.icon_sm{
  width: 20px;
}
.icon_plus{
  width: 30px;
  height: 30px;
}
.width_30{
  min-width: 200px;
}
.gridSy{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
}

.selected{
  color: lawngreen;
  border-color: lawngreen;

 }
.Wrongselected{
  color: crimson;
  border-color: crimson;
 }

</style>

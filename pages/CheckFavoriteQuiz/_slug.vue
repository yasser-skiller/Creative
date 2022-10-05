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

              <div id="list1" class="dropdown-check-list cursor_pointer bgGray0 width_30 rounded_0 p-2 mt-3 font-16" tabindex="100">
                <span class="anchor ">
                  <img :src="require(`~/assets/icon/folder4.svg`)" class="icon_sm ml-2" alt="icon"/>
                  <span class="pl-5 text-dark"> اضف السؤال لمجلد</span>
                </span>
                <ul class="items FoldersListCheckbox mt-2"  v-for="list in FoldersList" :key="list.index">
                  <div class="d-flex justify-content-between">
                    <li v-on:click="FoldersListCheckbox(Quiz_data[Quiz_serial])" class="d-flex ">
                      <input type="checkbox" :class="list.title" :id="list.title"/>
                      <label :for="list.title" class="my-0 mr-3">{{list.title}}</label>
                    </li>

                    <div>
                      <span
                        class="cursor_pointer text-danger font-weight-bold"
                        v-on:click="RemaoveFolderListCheckbox(list)"
                      >x
                      </span>
                      <span
                        class="cursor_pointer font-weight-bold"
                        v-on:click="EditFolderListCheckboxItem = list; EditeListName = list.title"
                        v-b-modal.modal-EditList
                      >
                      <img :src="require(`~/assets/icon/edit.png`)" class="icon mr-2" alt="icon"/>
                      </span>
                    </div>
                  </div>



                </ul>
              </div>

              <img
                :src="require(`~/assets/icon/plus.png`)"
                class="icon_plus mr-3 cursor_pointer"
                alt="icon"
                v-b-modal.modal-addList
              />

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
              :class="selected === option.value ? `optionItem selected` : `optionItem`"
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
                name="some-radios"
                :value="option.value"
              >
              </b-form-radio>
            </div>

            <div class="mt-3 ">Selected: <strong>{{ selected }}</strong></div>

            <div class="d-flex justify-content-center">
              <b-button size="sm" class="btn btn_light my-2 py-2 px-5 ml-4 rounded_0" type="button" v-if="Quiz_serial > 0 " v-on:click="Previous"> السابق</b-button>
              <b-button size="sm" class="btn btn_gradient my-2 py-2 px-5 rounded_0 " type="button" v-if="Quiz_serial !== Quiz_data.length-1 " v-on:click="Next"> التالي</b-button>
              <b-button size="sm" class="btn btn_gradient my-2 py-2 px-5 rounded_0 " type="button" v-if="Quiz_serial === Quiz_data.length-1 " v-on:click="Finish_Quiz">إنهاء الاختبار</b-button>
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
        <b-modal id="modal-EditList" title="تعديل اسم المجلد" hide-footer>
          <b-form-input v-model="EditeListName" class="my-4" placeholder="اكتب اسم المجلد"></b-form-input>
          <b-button size="sm" class="btn btn_Green my-2 py-2 px-r px-l rounded_0" type="button"  v-on:click="EditFolderListCheckbox(EditFolderListCheckboxItem)"> تعديل</b-button>
        </b-modal>

        <b-modal id="modal-addList" title="إضافة مجلد جديد" hide-footer>
          <b-form-input v-model="ListName" class="my-4" placeholder="اكتب اسم المجلد"></b-form-input>
          <b-button size="sm" class="btn btn_Green my-2 py-2 px-r px-l rounded_0" type="button"  v-on:click="CreateList"> إنشاء</b-button>
        </b-modal>
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

  export default {
    components:{
      Loading,
      AppNav
    },
    data() {
      return {
        Quiz_data: [],
        Answered:[],
        Favorite_Quiz:[],
        Pass_Quiz:[],
        selected: '',
        Quiz_serial:0,
        Quiz_duration:0,
        Minute:0,
        Seconds:0,
        Remseconds:0,
        HeartCase: false,
        Favorite_Quiz :[],
        PassCase:false,
        Pass_Quiz :[],
        ListName: '',
        EditeListName:'',
        FoldersList:[{title: 'default', content: []}],
        EditFolderListCheckboxItem: '',
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
        console.log('localStorage.Pass_Quiz_',JSON.parse(localStorage.getItem(`Pass_Quiz_${this.$route.params.slug}`)))
       console.log('localStorage.Quiz_duration',JSON.parse(localStorage.getItem(`Quiz_duration${this.$route.params.slug}`)))
       console.log('localStorage.Answered_',JSON.parse(localStorage.getItem(`Answered_${this.$route.params.slug}`)))
       console.log('localStorage.Quiz_data_',JSON.parse(localStorage.getItem(`Quiz_data_${this.$route.params.slug}`)))
        this.Pass_Quiz = JSON.parse(localStorage.getItem(`Pass_Quiz_${this.$route.params.slug}`));
        this.Favorite_Quiz = JSON.parse(localStorage.getItem(`Favorite_Quiz_${this.$route.params.slug}`));
        this.Answered = JSON.parse(localStorage.getItem(`Answered_${this.$route.params.slug}`));
        this.Quiz_data = JSON.parse(localStorage.getItem(`Favorite_Quiz_${this.$route.params.slug}`));
        this.Seconds = JSON.parse(localStorage.getItem(`Quiz_duration${this.$route.params.slug}`));
        console.log("localStorQuiz_serial", JSON.parse(localStorage.getItem (`Quiz_serial${this.$route.params.slug}`)))
        if(JSON.parse(localStorage.getItem(`Quiz_serial${this.$route.params.slug}`)) !== null){
          this.Quiz_serial = JSON.parse(localStorage.getItem(`Quiz_serial${this.$route.params.slug}`))
        }
        console.log("localStorage_Answered",this.Answered)
      },
      Compare(){
        if(this.Answered.length > 0){
          this.Answered.forEach(element => {
            if(element.my_Quiz_serial === this.Quiz_serial){
              this.selected = element.answer
            }
          });
        }

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
    Save(id, option_value, my_Quiz_serial){
      if(this.Answered.length > 0){
        this.Answered.forEach(element => {
          if(element){
            if(element.id === id){
              this.Answered =  this.Answered.filter(e => e !== element);
            }
          }
        });
        this.Answered.push({'id':id,'answer':option_value,'my_Quiz_serial':my_Quiz_serial});
      }if(this.Answered.length === 0){
        this.Answered.push({'id':id,'answer':option_value,'my_Quiz_serial':my_Quiz_serial});
      }


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
      console.log("localStorage_AnsweredvFinish_Quiz",this.Answered)
      localStorage.setItem(`Answered_${this.$route.params.slug}`, JSON.stringify(this.Answered));
      localStorage.setItem(`Quiz_duration${this.$route.params.slug}`, JSON.stringify((this.Minute*60)+this.Remseconds));
      localStorage.setItem(`Favorite_Quiz_${this.$route.params.slug}`, JSON.stringify(this.Favorite_Quiz));
      localStorage.setItem(`Pass_Quiz_${this.$route.params.slug}`, JSON.stringify(this.Pass_Quiz));
      this.$router.push({path:`/Result/${this.$route.params.slug}`});
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
    Drop(){
      var checkList = document.getElementById('list1');
      checkList.getElementsByClassName('anchor')[0].onclick = function(evt) {
        if (checkList.classList.contains('visible'))
          checkList.classList.remove('visible');
        else
          checkList.classList.add('visible');
      }
    },
    CreateList(){
      if(this.ListName !== ''){
        this.FoldersList.push({title:this.ListName, content:[]})
      }
      this.ListName = '';
      console.log('this.FoldersList',this.FoldersList)
    },
    FoldersListCheckbox(item){

      this.FoldersList.forEach(ele => {
        ele.content = ele.content.filter(e => e !== item)
      });

      document.querySelectorAll('.FoldersListCheckbox input').forEach(element => {
        if(element.checked){
          console.log("FoldersListCheckbox", element.className)
          this.FoldersList.forEach(ele => {
            if(ele.title === element.className){
              ele.content.push(item)
            }
          });
        }
      });
      console.log("this.FoldersList", this.FoldersList)
    },
    RemaoveFolderListCheckbox(item){
      this.FoldersList = this.FoldersList.filter(e => e !== item)
    },
    EditFolderListCheckbox(item){
      console.log("EditFolderListCheckbox",item)
      this.FoldersList.forEach(ele => {
        if(ele.title === item.title){
          item.title = this.EditeListName;
        }
      });
    },

    },
     watch: {
      Seconds: {
        handler(value) {
          if (value > 0) {
            setTimeout(() => {
              this.Minute = Math.floor(this.Seconds / 60)
              this.Remseconds = this.Seconds % 60
              this.Seconds--;
              if(this.Seconds < 9){
                this.Quiz_duration = this.Minute + ':0' + this.Remseconds
              }if(this.Minute < 9){
                this.Quiz_duration = "0"+this.Minute + ':' + this.Remseconds
              }else{
                this.Quiz_duration = this.Minute + ':' + this.Remseconds
              }
              localStorage.setItem(`Quiz_duration${this.$route.params.slug}`, JSON.stringify((this.Minute*60)+this.Remseconds));
            }, 1000);
            if(this.Minute === 0 && this.Remseconds === 1){
              this.$router.push({path:`/Result/${this.$route.params.slug}`})
            }
          }
        },
        immediate: true,
      },

    }

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


/* DropList */
.dropdown-check-list {
  display: inline-block;
}

.dropdown-check-list .anchor {
  position: relative;
  cursor: pointer;
  display: inline-block;
}

.dropdown-check-list .anchor:after {
  position: absolute;
  content: "";
  border-left: 2px solid #1D1F31;
  border-top: 2px solid #1D1F31;
  padding: 5px;
  right: 190px;
  top: 20%;
  transform: rotate(-135deg);
}

.dropdown-check-list .anchor:active:after {
  right: 190px;
  top: 21%;
}

.dropdown-check-list ul.items {
  padding: 2px;
  display: none;
  margin: 0;
  border-top: none;
}

.dropdown-check-list ul.items li {
  list-style: none;

}

.dropdown-check-list.visible .anchor {
  color: #0094ff;
}

.dropdown-check-list.visible .items {
  display: block;
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
</style>

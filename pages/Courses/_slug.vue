<template>
  <div>
    <AppNav/>
    <div v-if="CurentCourse_data !== '' && this.Lessons_data.length > 0">
      <b-container>
        <b-row align-h="center"  class="flex-wrap-reverse">
        <b-col cols="12"  lg="5" class="text_GraySec m-sec">

          <div class="bgGray rounded_1 border p-3 my-4" v-for="section in CurentCourse_data.sections" :key="section.id">
            <div class="d-flex justify-content-between " :id="section.id" v-on:click="Toggle(section.id)">
              <div>
                <p class="text_DarkRedColor my-0">  {{section.title}}</p>
                <p class="my-0">عدد {{section.items.length}} فيديو</p>
              </div>
              <img :src="require(`~/assets/icon/arrup.svg`)"  alt="icon"/>
            </div>

            <div class="content" :id="section.id">
              <div v-for="item in section.items" :key="item.id">
                <div v-on:click="CurentLessons(item.id)" :id="`id${item.id}`" v-if="item.type === 'lp_lesson'" class="list d-flex justify-content-between cursor_pointer align-items-center my-4">
                  <div class="d-flex align-items-center ">
                    <img :src="require(`~/assets/icon/CheckNumber.svg`)" class="iconCheck ml-2" alt="icon"/>
                    <p class="my-0">{{item.title}}</p>
                  </div>
                  <p class="my-0">13:12</p>
                </div>
              </div>

            </div>


          </div>

        </b-col>
        <b-col cols="12"  lg="7" class="m-sec" >
          <!-- <img :src="require(`~/assets/img/Live Courses.png`)"  class="w-100" alt="icon"/> -->
          <script src="https://vjs.zencdn.net/7.20.2/video.min.js"></script>

              <video
                id="my-video"
                class="video-js vjs-theme-sea video"
                controls
                preload="auto"
                data-setup='{
                  "playbackRates": [0.25, 0.5, 1, 1.25,1.50, 1.75, 2]
                }'
              >

              <source :src="CurentLessons_data.video_url" type="video/mp4">

            </video>

        </b-col>
        </b-row>

        <div class="tabs my-5">
          <p v-on:click="ChangeTab('about')" class="tab active"> الفيديو الحالي</p>
          <p  v-on:click="ChangeTab('content')" class="tab"> الملفات المرفقة</p>
          <p  v-on:click="ChangeTab('teach')" class="tab"> الامتحان التأهيلي</p>
          <p  v-on:click="ChangeTab('offer')" class="tab">   العروض علي الدورتين</p>

        </div>
        <div v-if="Classfcation === 'about'"><VedioSec :CurentLessons_data="CurentLessons_data"/></div>
        <div v-if="Classfcation === 'content'"><FilesSec :CurentLessons_data="CurentLessons_data"/></div>
        <div v-if="Classfcation === 'teach'"><TaskSec :CurentLessons_data="CurentLessons_data"/></div>
        <div v-if="Classfcation === 'offer'"><OfferSec :data="CurentCourse_data"/></div>

      </b-container>
    </div>
    <div v-else class="d-flex justify-content-center align-items-center spinner_loading">
      <Loading/>
    </div>
    <AppFooter/>

  </div>

</template>

<script>
import config from "@/config";
  import AppNav from "@/components/AppNav";
  import Loading from "@/components/Loading";
   import VedioSec from "@/pages/Courses/VedioSec";
   import FilesSec from "@/pages/Courses/FilesSec";
   import TaskSec from "@/pages/Courses/TaskSec";
   import OfferSec from "@/pages/Courses/OfferSec";
   import AppFooter from "@/components/AppFooter";

  export default {
    components:{
      AppNav,
      Loading,
      FilesSec,
      VedioSec,
      TaskSec,
      OfferSec,
      AppFooter,
    },
    data() {
        return {
        Up: false,
        Classfcation: '',
        CurentCourse_data: '',
        Lessons_data: [],
        CurentLessons_data: '',

      }
    },
    mounted() {
      this.fetchCurentCourses();
      this.fetchCurentLessons();
      this.ActiveTab();
      this.ChangeTab('about');
    },
    methods: {
      ActiveTab(){
        document.querySelectorAll('.tabs .tab').forEach(element =>{
            element.addEventListener('click',()=>{
              document.querySelectorAll('.tabs .tab').forEach(ele => {
            ele.classList.remove('active')
            });
            element.classList.add("active")

          })
        })
      },
      ChangeTab(key){
        this.Classfcation = key
        this.ActiveTab()
      },
      fetchCurentCourses() {
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
            this.CurentCourse(JSON.parse(result));

          })
          .catch(error => console.log('error', error));
      },
      fetchCurentLessons() {
        var myHeaders = new Headers();
        myHeaders.append("Authorization", `Bearer${config.token}`);

        var requestOptions = {
          method: 'GET',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch(config.apiUrl+"wp-json/learnpress/v1/lessons", requestOptions)
          .then(response => response.text())
          .then(result => {
            this.Lessons_data = JSON.parse(result)
            console.log("JSON.parse(result)",JSON.parse(result))
          })
          .catch(error => console.log('error', error));
      },
      CurentCourse(Course_data){
        Course_data.forEach(element => {
          if(element.id.toString() === this.$route.params.slug ){
            this.CurentCourse_data = element
          }
        });
        setTimeout(() => {
          this.CurentCourse_data.sections[0].items.forEach(element => {
            if(element.type === 'lp_lesson'){
              this.CurentLessons(element.id);
              document.querySelector(`#id${element.id}`).classList.add('activeList');
            }
          });

        }, 500);


      },
      CurentLessons(item_id){
        this.Lessons_data.forEach(element => {
          if(element.id === item_id ){
            this.CurentLessons_data = element
          }
        });

        document.querySelectorAll('.list').forEach(ele =>{
          ele.classList.remove('activeList')
        })
        document.querySelector(`#id${item_id}`).classList.add('activeList')
        console.log("this.CurentLessons_data",this.CurentLessons_data)

      },
      Toggle(id){
        document.querySelectorAll('.content').forEach(ele =>{
          if(ele.id === id.toString()){
            ele.classList.toggle('d-none')
          }
        });

      },
    },

  };

  </script>


<style scoped>
 .spinner_loading{
  height: 90vh;
}
  .gray{
    color: #696974;
  }
  .file,.iconCheck{
    width: 25px;
  }
  .NumberCheck{
    width: 25px;
    height: 25px;
    border-radius: 5px;
    color: #fff;
    background-color: #E36414;
  }

.active{
  color: var(--OrangeColor);
  border-bottom: var(--OrangeColor) 5px solid;
  padding-bottom: 5px;
}
.tabs{
  display: flex;
  border-bottom: 2px solid #E2E2E2;
  justify-content: space-around;
}
.tabs p{
  margin: 0;
  cursor: pointer;
}
.video {
    width: 100% ;
    height: 420px;
  }

@media (max-width:567px) {
  .tabs{
    justify-content: space-between;
  }

}
.activeList{
  color: #039A7B;
}
</style>

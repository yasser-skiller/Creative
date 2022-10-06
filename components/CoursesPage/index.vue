<template>
  <b-container>
    <b-row align-h="center"  class="flex-wrap-reverse">
    <b-col cols="12"  lg="5" class="text_GraySec m-sec">

      <div class="bgGray rounded_1 border p-3 my-4">
        <div class="d-flex justify-content-between " v-on:click="Up = !Up">
          <div>
            <p class="text_DarkRedColor my-0"> اسم القسم الأول هنا</p>
            <p class="my-0">عدد 6 فيديو</p>
          </div>

          <img :src="require(`~/assets/icon/arrdown.svg`)"  :class="Up === true ? 'd-block downUP' : 'd-none'" alt="icon"/>
          <img :src="require(`~/assets/icon/arrup.svg`)"  :class="Up === false ? 'd-block downUP' : 'd-none'" alt="icon"/>
        </div>

        <div :class="Up === false ? 'd-block' : 'd-none'">
          <div class="d-flex justify-content-between align-items-center my-4">
            <div class="d-flex align-items-center gray">
              <img :src="require(`~/assets/icon/CheckNumber.svg`)" class="iconCheck ml-2" alt="icon"/>
              <p class="my-0">اسم الفيديو هنا</p>
            </div>
            <p class="my-0">13:12</p>
          </div>
        </div>

        <div :class="Up === false ? 'd-block' : 'd-none'">
          <div class="d-flex justify-content-between align-items-center my-4">
            <div class="d-flex align-items-center gray">
              <img :src="require(`~/assets/icon/CheckNumber.svg`)" class="iconCheck ml-2" alt="icon"/>
              <p class="my-0">اسم الفيديو هنا</p>
            </div>
            <p class="my-0">13:12</p>
          </div>
        </div>

        <div :class="Up === false ? 'd-block' : 'd-none'">
          <div class="d-flex justify-content-between align-items-center my-4">
            <div class="d-flex align-items-center gray">
              <span class="NumberCheck ml-2 font-weight-bold text-center pt-1" alt="icon">3</span>
              <p class="my-0">اسم الفيديو هنا</p>
            </div>
            <p class="my-0">13:12</p>
          </div>
        </div>



      </div>


    </b-col>
    <b-col cols="12"  lg="7" class="m-sec">
      <img :src="require(`~/assets/img/Live Courses.png`)"  class="w-100" alt="icon"/>

    </b-col>
  </b-row>

  <div class="tabs my-5">
      <p v-on:click="ChangeTab('about')" class="tab active"> الفيديو الحالي</p>
      <p  v-on:click="ChangeTab('content')" class="tab"> الملفات المرفقة</p>
      <p  v-on:click="ChangeTab('teach')" class="tab"> الامتحان التأهيلي</p>
      <p  v-on:click="ChangeTab('offer')" class="tab">   العروض علي الدورتين</p>

    </div>
    <div v-if="Classfcation === 'about'"><VedioSec/></div>
    <div v-if="Classfcation === 'content'"><FilesSec/></div>
    <div v-if="Classfcation === 'teach'"><TaskSec/></div>
    <div v-if="Classfcation === 'offer'"><OfferSec/></div>

  </b-container>
</template>

<script>
   import VedioSec from "@/components/CoursesPage/VedioSec";
   import FilesSec from "@/components/CoursesPage/FilesSec";
   import TaskSec from "@/components/CoursesPage/TaskSec";
   import OfferSec from "@/components/CoursesPage/OfferSec";
  export default {
    components:{
      FilesSec,
      VedioSec,
      TaskSec,
      OfferSec,
    },
    data() {
        return {
        Up: false,
        Classfcation: '',

      }
    },
    mounted() {
      this.ActiveTab();
      this.ChangeTab('about')
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
      }
    },

  };

  </script>


<style scoped>

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

@media (max-width:567px) {
  .tabs{
    justify-content: space-between;
  }

}
</style>

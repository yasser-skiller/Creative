<template>
  <b-container class="">
    <b-row align-h="center"  class="flex-wrap-reverse">
      <b-col cols="12" lg="6" class="m-sec">
        <img :src="require(`~/assets/img/Group 2277.png`)" class="w-100" alt="icon"/>
      </b-col>
      <b-col cols="12" lg="6" class="m-sec">
        <div class="d-flex">
          <img :src="require(`~/assets/icon/logo.svg`)" class="logo_icon" alt="icon"/>
          <p class="my-0 mr-2">دورة المبدع</p>
        </div>
        <div class="my-4 position-relative pr-4">
          <h3 class="text_orange">دورة التأسيس</h3>
          <img :src="require(`~/assets/icon/Group 2278.svg`)" class="path" alt="icon"/>
        </div>
        <p class="pr-4 mb-5">
          هي دورة للتأسيس في القدرات ومعرفة أساسيات القدرات من الصفر للاحتراف وطريقك الأمثل للحصول علي المئة بأذن الله
        </p>
        <div class="d-flex">
          <img :src="require(`~/assets/icon/exam (3).svg`)" class="icon" alt="icon"/>
          <p class="my-0 mr-2">7 اختبارت مختلفة علي دورة التأسيس </p>
        </div>
        <div class="d-flex my-3">
          <img :src="require(`~/assets/icon/online-learning12.svg`)" class="icon" alt="icon"/>
          <p class="my-0 mr-2">4 اقسام تعليمية للتأسيس الشامل  </p>
        </div>
        <div class="d-flex my-3">
          <img :src="require(`~/assets/icon/file12.svg`)" class="icon" alt="icon"/>
          <p class="my-0 mr-2"> ملفات للتأسيس وغيرها داخل الدورة </p>
        </div>
        <div class="d-flex">
          <img :src="require(`~/assets/icon/low-price.svg`)" class="icon" alt="icon"/>
          <p class="my-0 mr-2">يوجد خصم 50 بالمئة علي الكورس الان  </p>
        </div>
        <div class="d-flex mt-5">
          <b-button size="sm" class="btn btn_Dark my-2 py-3 px-5 ml-4 rounded_0" type="button" > شراء الدورة</b-button>
          <div class="d-flex align-items-center position-relative">
            <img :src="require(`~/assets/icon/dollar (3).svg`)" class="dollar" alt="icon"/>
            <small class="my-0 mr-2 text_orange">فقط</small>
            <h5 class="my-0 mr-2 text_orange">   150 ر.س  </h5>
            <img :src="require(`~/assets/icon/Group 2279.svg`)" class="dollar_path" alt="icon"/>
          </div>
        </div>
      </b-col>

    </b-row>

    <div class="tabs my-5">
      <p v-on:click="ChangeTab('about')" class="tab active">عن الدورة</p>
      <p  v-on:click="ChangeTab('content')" class="tab"> المحتوي</p>
      <p  v-on:click="ChangeTab('teach')" class="tab"> المدرس</p>
      <p  v-on:click="ChangeTab('offer')" class="tab"> العروض علي الدورتين</p>

    </div>
    <div v-if="Classfcation === 'about'"><AboutSec/></div>
    <div v-if="Classfcation === 'content'"><ContentSec/></div>
    <div v-if="Classfcation === 'teach'"><TeachSec/></div>
    <div v-if="Classfcation === 'offer'"><OfferSec/></div>

  </b-container>
</template>

<script>
   import AboutSec from "@/components/Secsion/AboutSec";
   import TeachSec from "@/components/Secsion/TeachSec";
   import OfferSec from "@/components/Secsion/OfferSec";
   import ContentSec from "@/components/Secsion/ContentSec";


   export default {
    components:{
      AboutSec,
      TeachSec,
      OfferSec,
      ContentSec,
    },
    data (){
    return {
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
   }
</script>


<style scoped>
.logo_icon{
  width: 20px;
}
.icon{
  width: 16px;
}

.dollar{
  width:30px ;
}
.path{
  position: absolute;
  top: -20px;
  right: 190px;
  width: 35px;
}
.dollar_path{
  position: absolute;
  top: -20px;
  right: 140px;
  width: 35px;
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

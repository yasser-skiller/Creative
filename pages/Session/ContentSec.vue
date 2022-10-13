<template>
  <div>
    <p>محتوي الدورة المحوسبة </p>

    <div class=" rounded_0 border my-4" v-for="section in data.sections" :key="section.id">
        <div class="d-flex justify-content-between align-items-center bgRed p-3 rounded_0">

          <div class="d-flex align-items-center cursor_pointer" :id="section.id" v-on:click="Toggle(section.id)">
            <img :src="require(`~/assets/icon/downUP.svg`)" alt="icon"/>
            <p class="font-weight-bold my-0 mr-2">{{section.title}}</p>
          </div>

          <p class="my-0 text_orange font-weight-bold">عدد 3 فيديوهات - 15 دقيقة</p>

        </div>

        <div :id="section.id" class="content">

          <div v-for="item in section.items" :key="item.id" class="d-flex justify-content-between align-items-center px-2">
            <div  :id="`id${item.id}`" class="d-flex justify-content-between w-100 align-items-center my-4 cursor_pointer list" v-if="item.type === 'lp_lesson'">
                <div class="d-flex align-items-center ">
                 <img :src="require(`~/assets/icon/Group 2282.svg`)" class="iconCheck" alt="icon"/>
                 <p class="my-0 mr-2"> {{item.title}} </p>
               </div>
              <p class="my-0 text_green"><span class="gray">وقت الفيديو :</span> <span class="font-weight-bold">04:05</span></p>
            </div>

          </div>

          <!-- <div class="d-flex justify-content-between align-items-center my-4">
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
          </div> -->


        </div>



      </div>
  </div>
</template>


<script>
  export default {
    props: ["data"],
    data() {
        return {
        Up: false,
      }
    },
    methods:{
      Toggle(id){
        document.querySelectorAll('.content').forEach(ele =>{
          if(ele.id === id.toString()){
            ele.classList.toggle('d-none')
          }
        });

      },
    }

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

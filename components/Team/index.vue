<template>
    <b-container class="m-sec mb-5 animate__animated animate__bounceIn">
      <h4 class="font-weight-bold text_orange text-center animate__animated animate__fadeInRight">فريق المبدع</h4>
      <p class="text-center mt-3">
        شعارنا دقة الإنتاج و سرعة الأداء
      </p>
      <b-row align-h="center"  class="d-flex flex-wrap justify-content-between align-items-center">
        <b-col cols="12" sm="10" md="6" lg="3"  class="mt-4 mx-auto">
          <div class="parent">
            <img :src="require(`~/assets/img/Group 1417.png`)" class="Group" alt="icon"/>
            <div class="overly">
              <h6 class="text_orange font-weight-bold">الدكتور : السيد جاد الله</h6>
              <p>مدرس قدرات لفظي وقائد الدورات</p>
              <div class="d-flex justify-content-around px-3 w-100">
                <img :src="require(`~/assets/icon/facebook (2).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/linkedin (2).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/twitter (1).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/youtube (1).svg`)" class="" alt="icon"/>
              </div>
            </div>
          </div>

        </b-col>
        <b-col cols="12" sm="10" md="6" lg="3"  class="mt-4 mx-auto">
          <div class="parent">
            <img :src="require(`~/assets/img/Group 1417.png`)" class="Group" alt="icon"/>
            <div class="overly">
              <h6 class="text_orange font-weight-bold">الدكتور : السيد جاد الله</h6>
              <p>مدرس قدرات لفظي وقائد الدورات</p>
              <div class="d-flex justify-content-around px-3 w-100">
                <img :src="require(`~/assets/icon/facebook (2).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/linkedin (2).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/twitter (1).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/youtube (1).svg`)" class="" alt="icon"/>
              </div>
            </div>
          </div>

        </b-col>
        <b-col cols="12" sm="10" md="6" lg="3"  class="mt-4 mx-auto">
          <div class="parent">
            <img :src="require(`~/assets/img/Group 1417.png`)" class="Group" alt="icon"/>
            <div class="overly">
              <h6 class="text_orange font-weight-bold">الدكتور : السيد جاد الله</h6>
              <p>مدرس قدرات لفظي وقائد الدورات</p>
              <div class="d-flex justify-content-around px-3 w-100">
                <img :src="require(`~/assets/icon/facebook (2).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/linkedin (2).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/twitter (1).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/youtube (1).svg`)" class="" alt="icon"/>
              </div>
            </div>
          </div>

        </b-col>
        <b-col cols="12" sm="10"  md="6" lg="3"  class="mt-4 mx-auto">
          <div class="parent">
            <img :src="require(`~/assets/img/Group 1417.png`)" class="Group" alt="icon"/>
            <div class="overly">
              <h6 class="text_orange font-weight-bold">الدكتور : السيد جاد الله</h6>
              <p>مدرس قدرات لفظي وقائد الدورات</p>
              <div class="d-flex justify-content-around px-3 w-100">
                <img :src="require(`~/assets/icon/facebook (2).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/linkedin (2).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/twitter (1).svg`)" class="" alt="icon"/>
                <img :src="require(`~/assets/icon/youtube (1).svg`)" class="" alt="icon"/>
              </div>
            </div>
          </div>

        </b-col>

      </b-row>


    </b-container>
</template>

<script>
export default {

};

</script>

<style scoped>
.icon{
  width: 40px;
}
.icon_0{
  width: 16px;
}
.parent{
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}
.parent .Group{
  width: 130%;
}
.overly{
  position: absolute;
  bottom: 80px;
  right: 25px;
  left: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
@media (max-width:1200px) {
  .parent .Group{
    width: 140%;
  }
  .overly{
    right: 0px;
    bottom: 70px;

  }
  .overly p{
    font-size: 12px;
  }
}
@media (max-width:989px) {
  .parent .Group{
    width: 100%;
  }
  .overly{
    right: 50px;
    width: 75%;
  }
}
@media (max-width:768px) {
  .parent .Group{
    width: 100%;
  }
  .overly{
    right: 60px;
    bottom: 110px;
    width: 75%;
  }
}

@media (max-width:576px) {
  .parent .Group{
    width: 100%;
  }
  .overly{
    right: 65px;
    bottom: 150px;
    width: 80%;
  }
}
@media (max-width:500px) {
  .overly{
    right: 50px;
    bottom: 100px;
    width: 80%;
  }
}
@media (max-width:380px) {
  .overly{
    right: 37px;
    bottom: 70px;
    width: 80%;
  }
}
</style>

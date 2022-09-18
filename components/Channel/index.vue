<template>
    <b-container class="m-sec mb-5 animate__animated animate__bounceIn">
      <h4 class="font-weight-bold text_orange text-center animate__animated animate__fadeInRight">قناة أبسطها لك</h4>
      <p class="text-center mt-3">
        اسم يجمع بين الإبداع ومتعة التعلم
      </p>
      <b-row align-h="center"  class="d-flex flex-wrap justify-content-between align-items-center">
        <b-col cols="12" sm="10" lg="4"  class="mt-4">
          <div class="bgGray shadow rounded_0 p-3">
            <div class="parent">
              <img :src="require(`~/assets/img/imgg.png`)" class="w-100" alt="icon"/>
              <div class="overly">
                <img :src="require(`~/assets/icon/play.svg`)" class="icon" alt="icon"/>
              </div>
            </div>
            <p class="text_orange font-weight-bold my-2">نموذج الخوارزمي ( النموذج كامل)</p>
            <div class="d-flex justify-content-between">
              <div class="d-flex my-1 rounded_0 align-items-center" >
                <img :src="require(`~/assets/icon/clock2.svg`)" class="icon_0 ml-2" alt="icon"/>
                <span>05:36 د</span>
              </div>
              <div class="d-flex bgDark my-1 mx-2 p-2 rounded_0" >
                <img :src="require(`~/assets/icon/share.svg`)" class="icon_0" alt="icon"/>
              </div>
            </div>
          </div>

        </b-col>
        <b-col cols="12" sm="10" lg="4"  class="mt-4">
          <div class="bgGray shadow rounded_0 p-3">
            <div class="parent">
              <img :src="require(`~/assets/img/chris-liverani-ViEBSoZH6M4-unsplash.png`)" class="w-100" alt="icon"/>
              <div class="overly">
                <img :src="require(`~/assets/icon/play.svg`)" class="icon" alt="icon"/>
              </div>
            </div>
            <p class="text_orange font-weight-bold my-2">نموذج الخوارزمي ( النموذج كامل)</p>
            <div class="d-flex justify-content-between">
              <div class="d-flex my-1 rounded_0 align-items-center" >
                <img :src="require(`~/assets/icon/clock2.svg`)" class="icon_0 ml-2" alt="icon"/>
                <span>05:36 د</span>
              </div>
              <div class="d-flex bgDark my-1 mx-2 p-2 rounded_0" >
                <img :src="require(`~/assets/icon/share.svg`)" class="icon_0" alt="icon"/>
              </div>
            </div>
          </div>

        </b-col>
        <b-col cols="12" sm="10" lg="4"  class="mt-4">
          <div class="bgGray shadow rounded_0 p-3">
            <div class="parent">
              <img :src="require(`~/assets/img/img2.png`)" class="w-100" alt="icon"/>
              <div class="overly">
                <img :src="require(`~/assets/icon/play.svg`)" class="icon" alt="icon"/>
              </div>
            </div>
            <p class="text_orange font-weight-bold my-2">نموذج الخوارزمي ( النموذج كامل)</p>
            <div class="d-flex justify-content-between">
              <div class="d-flex my-1 rounded_0 align-items-center" >
                <img :src="require(`~/assets/icon/clock2.svg`)" class="icon_0 ml-2" alt="icon"/>
                <span>05:36 د</span>
              </div>
              <div class="d-flex bgDark my-1 mx-2 p-2 rounded_0" >
                <img :src="require(`~/assets/icon/share.svg`)" class="icon_0" alt="icon"/>
              </div>
            </div>
          </div>

        </b-col>
        <div class="d-flex justify-content-between align-items-center w-100">
          <button class="btn btn_orange my-5 mx-auto py-3 px-4 rounded_0">مشاهده كل الفيديوهات</button>
        </div>
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
}
.overly{
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background-image: url('~/assets/img/Rectangle 46.png');
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

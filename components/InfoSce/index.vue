<template>
    <b-container class="m-sec">
      <div class="d-flex justify-content-center">
        <div class="parent">
          <img :src="require(`~/assets/img/Group 14180.png`)" class="Group" alt="icon"/>
            <div class="overly text-white p-4">
              <h3 class="font-weight-bold mt-4">تواصلوا معنا</h3>
              <p class="my-2"> تواصلوا معنا عبر الأرقام التالية :</p>
              <div class="d-flex w-25 mt-5 justify-content-between dic">
                <p class="font-weight-bold">0556141191</p>
                <p class="font-weight-bold">0506085596</p>
              </div>
            </div>
          </div>
      </div>
    </b-container>
</template>


<style scoped>
  .Group{
    width: 75%;
  }
  @media (max-width:992px) {
    .Group{
     width: 100%;
    }
  }
  @media (max-width:767px) {
    .Group{
     width: 120%;
    }
    .dic{
     width: 50% !important;
    }
    .mt-4{
      margin-top: .2rem !important;
    }
  }
  @media (max-width:630px) {
    .Group{
     width: 100%;
     height: 120px;
    }
    .dic{
     width: 80% !important;
    }
    .mt-4{
      margin-top: 0rem !important;
    }
    .mt-5{
      margin-top: .5rem !important;
    }
    .p-4{
      padding: 5px !important;
    }
  }
.parent{
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}
.overly{
  position: absolute;
  bottom: 0px;
  top: 0;
  right: 0px;
  left: 0;
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
  align-items: center;
}
</style>

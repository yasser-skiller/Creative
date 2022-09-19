<template>
    <b-container class="m-sec">
      <b-row align-h="center"  class="d-flex flex-wrap bgGray p-4 shadow rounded_1 justify-content-between align-items-center">
        <b-col cols="12" sm="10" md="6" lg="6"  class="">
          <h4 class="font-weight-bold text_orange">اشترك في اخر الاخبار</h4>
          <p class="my-3">هذا النص هو مثال لنص يمكن أن يستبدل في نفس المساحة، لقد تم توليد هذا النص من مولد </p>
          <b-form  >
            <b-form-group id="input-group-2" class="text_dark font-weight-bold" label="البريد الالكتروني" label-for="input-2">
              <b-form-input
                id="input-2"
                placeholder="...اكتب البريد الالكتروني هنا"
                required
              ></b-form-input>
            </b-form-group>
          </b-form>
        </b-col>
        <b-col cols="12" sm="10" md="6" lg="6"  class="">
          <div class="position-relative">
            <img :src="require(`~/assets/img/Group 14182.png`)" class="Group" alt="icon"/>
          </div>
        </b-col>
      </b-row>
    </b-container>
</template>

<style scoped>
.Group{
  position:absolute ;
  width: 770px;
  top: -190px;
  left: 0;
}
#input-group-2{
  color: var(--DarkBlueColor);
}
#input-2::placeholder{
  color: var(--SecColor);
}

@media (max-width:992px) {
  .Group{
  width: 770px;
  top: -180px;
  left: -40px;
}
}
@media (max-width:768px) {
  .Group{
    width: 600px;
    position: relative;
    top: 0px;
    left: 220px;
  }
}
@media (max-width:568px) {
  .Group{
    width: 400px;
    position: relative;
    top: 0px;
    left: 120px;
  }
}
</style>

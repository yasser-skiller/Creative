<template>
    <b-container class="m-sec" id="contact">
      <b-row align-h="center"  class="flex-wrap align-items-center">
        <b-col cols="12"   lg="6" class="bg  padding animate__animated animate__fadeInRight">
          <div class="d-flex mt-5">
            <img :src="require(`~/assets/icon/logo.svg`)" class="logo" alt="icon"/>
            <h3 class="text_orange mr-4">تواصل معنا الان</h3>
          </div>
          <p class="mt-4 pr-5">هذا النص هو مثال لنص يمكن أن يستبدل في نفس المساحة، لقد تم توليد هذا النص من مولد النص العربى، حيث يمكنك أن تولد مثل هذا النص</p>
          <h6 class="mt-5 font-weight-bold mb-4 pr-5"> بيانات التواصل : </h6>
          <div class="d-flex align-items-center pr-2">
            <span class="mark"></span>
            <span>01033143665</span>
          </div>
          <div class="d-flex align-items-center pr-2">
            <span class="mark"></span>
            <span>البريد الالكتروني</span>
          </div>
          <div class="d-flex align-items-center pr-2">
            <span class="mark"></span>
            <span>العنوان</span>
          </div>

        </b-col>
        <b-col cols="12"  lg="6" class="bg2 p-4 px-5 animate__animated animate__fadeInLeft">
            <b-form @submit="onSubmit" @reset="onReset" >
             <b-form-group id="input-group-2" class="text-white" label="الاسم" label-for="input-2">
                <b-form-input
                  id="input-2"
                  v-model="form.name"
                  placeholder="محمد مصطفي علي"
                  required
                ></b-form-input>
              </b-form-group>

              <b-form-group id="input-group-2" class="text-white my-5" label="ما رقم هاتفك (على واتساب)؟" label-for="input-3">
                <b-form-input
                  id="input-3"
                  v-model="form.name"
                  placeholder="...اكتب الرقم هنا"
                  required
                ></b-form-input>
              </b-form-group>

              <p class="text-white mt-4">رسالتك</p>
              <b-form-textarea
                id="textarea-rows"
                placeholder="...اكتب رسالتك هنا"
                v-model="form.textarea"
                rows="7"
              ></b-form-textarea>


              <div class="d-flex justifiy-contant-center">
                <b-button v-b-modal.modal-contact type="submit" class="btn btn_light mt-5 mx-auto py-2 px-5 rounded_0" >ارسل الان</b-button>
              </div>

              <b-modal id="modal-contact"   hide-footer hide-header>
                <div class="modal_style rounded_1">
                  <h3 class="text-center text_blue">شكرا لك</h3>
                  <p class="text-center my-3">
                    يمكنك التواصل معنا الان عن طريق الوتساب
                    <br/>
مباشرة فقط اضغط علي الزر وتواصل معنا الان
                  </p>
                  <div class="d-flex flex-column w-100 justify-content-center align-items-center">
                    <img :src="require(`~/assets/img/Group 232.png`)" class="w-50" alt="icon"/>
                    <b-button v-b-modal.modal-contact type="submit" class="btn btn_blue mt-5 mx-auto py-3 px-5 rounded_0" >تواصل معنا</b-button>
                  </div>

                </div>
              </b-modal>


            </b-form>
        </b-col>
      </b-row>
    </b-container>
</template>

<script>
export default {
   data() {
      return {
        form: {
          name: '',
          textarea:''
        },

      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        alert(JSON.stringify(this.form))
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.name = ''
        this.form.textarea = ''

      }
    }

};

</script>

<style scoped>
.bg{
  position: relative;
  background-image: url('./../../assets/img/Group 1418.png');
  background-position: center;
  background-repeat:repeat-y repeat-x;
  background-size: cover;
  width: 100%;
  height: 600px;
}
.bg2{
  position: relative;
  background-image: url('./../../assets/img/Group 1419.png');
  background-position: center;
  background-repeat:repeat-y repeat-x;
  background-size: cover;
  width: 100%;
  height: 600px;
}
.mark{
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background-color: var(--GrayFill);
  margin: 10px 0 10px 10px;
}
#input-group-2,#input-group-3{
  color: var(--DarkBlueColor);
}
#input-2::placeholder{
  color: var(--SecColor);
}
#input-2{
  height: 40px;
  color: var(--SecColor);
  background-color: var(--fillBlue);
}
#textarea-rows,
#input-3{
  color: var(--DarkGray);
  background-color: var(--fillBlue);
}
.padding{
  padding: 4rem 5.5rem;
}
.logo{
  width: 35px;
}
</style>

<template>
  <b-row align-h="center"  class="flex-wrap-reverse bg_all">
    <b-col cols="12" lg="6" class=" p-5 animate__animated animate__fadeInRight">

      <div class="position-relative">
        <h3 class="my-4 text_blue">مرحبا بك في المبدع</h3>
        <img :src="require(`~/assets/icon/pathgreen.svg`)" class="path_1" alt="icon"/>
      </div>
      <p class="font-16 text_yellow">تسجيل الدخول بحاسبك الي المبدع</p>

      <b-form @submit="onSubmit" class="mt-5">


        <div class="d-flex flex-column position-relative mt-5">
          <label class="label">البريد الالكتروني</label>
          <input
            id="input"
            v-model="form.email"
            placeholder="...اكتب البريد الالكتروني هنا"
            type="email"
            required
          />
        </div>

        <div class="d-flex flex-column position-relative mt-5">
          <label class="label"> رمز المرور</label>
          <input
            id="input"
            v-model="form.password"
            placeholder="...اكتب رمز المرور"
            type="password"
            required
          />
        </div>


        <div class="mt-5 d-flex justify-content-center">
          <b-button type="submit" class="btn btn_orange rounded_1 px-5 py-2 ">تسجيل الدخول</b-button>
        </div>
        <div class="d-flex my-2 justify-content-center">
          <p>لديك حساب بالفعل!؟ </p>
          <NuxtLink to="/Signup" class="">انشاء حساب الان</NuxtLink>
        </div>
      </b-form>

    </b-col>
    <b-col cols="12" md="6" lg="6" class="animate__animated animate__fadeInRight">
      <img :src="require(`~/assets/img/Group 2275.png`)" class="img" alt="icon"/>
      <div class="parent">
        <h4 class="text-white">دورة التأسيس</h4>
        <p class="text-white px-5 py-3">
          دورة للاستعداد للاختبار المحوسب وحل تجميعات وأسئلة تأتي في الاختبار مع تحديثات دائمة وملفات شاملة لتأهيل الطالب لدخول الاختبار
        </p>
      </div>
    </b-col>
  </b-row>
</template>

<script>
  export default {
    data() {
      return {
        form: {
          email: '',
          password: '',
        },
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        alert(JSON.stringify(this.form))
        this.form.email = ''
        this.form.password = ''
      },

    }
  }
</script>


<style scoped>
.logo{
  width: 70px;
}
.parent{
  position: absolute;
  top: 0;
  right: 100px;
  left: 0;
  bottom: 0;
  display: flex;
  flex-direction: column;
  justify-content: end;
  align-items: center;
}
.bg_all{
  background-color:#F3F4F9
}
.img{
  width: 100%;
  height: 100vh;
}
@media (max-width:989px) {
  .img{
   display: none;
  }
}
.path_1{
  width: 30px;
  position: absolute;
  top: -10px;
  right: 250px;
}

#input{
  padding: 20px 15px;
  background-color: #F3F4F9;
  border:1px solid #B7B9CE;
  border-radius: 10px;
  color: #B7B9CE;
  outline: none;


}

#input :focus{
  background-color: #F3F4F9;
  border:1px solid #B7B9CE;
  outline: none;
}
.label{
  position: absolute;
  top: -10px;
  right: 30px;
  background-color: #F3F4F9;
  width: 140px;
  text-align: center;
}

</style>

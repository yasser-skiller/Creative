<template>
  <div>
    <div v-if="CurentLessons_data.pdf_files === null">
      <b-row align-h="center"  class="flex-wrap">
        <b-col cols="12"  lg="4" class="px-2 my-3" v-if="CurentLessons_data.pdf_files !== null && CurentLessons_data.pdf_files[0]">
          <div class="bg py-2 px-3 rounded_1">
            <div class="d-flex">
              <img :src="require(`~/assets/icon/Group 2286.svg`)"  class="ml-2" alt="icon"/>
              <div>
                <h6 class="font-weight-bold">ملف {{CurentLessons_data.pdf_files[0].file_name}}</h6>
                <p>ملف امتحان {{CurentLessons_data.pdf_files[0].file_name}} .... سؤال</p>
              </div>
            </div>
            <div class="d-flex mx-auto mt-5 justify-content-center ">
              <a  :href="CurentLessons_data.pdf_files[0].pdf_file.url" target="_blank">
                <img :src="require(`~/assets/icon/pdf0.svg`)" class="ml-2" alt="icon"/>
              </a>
              <p class="my-0">
                <span class="ml-1">بحجم</span>
                {{Math.ceil(CurentLessons_data.pdf_files[0].pdf_file.filesize/1000000)}}
                <sapn class="mr-1">ميجا</sapn>
              </p>
            </div>

            <div class="d-flex mt-4 justify-content-center ">
              <b-button v-on:click="DownLoad(CurentLessons_data.pdf_files[0].pdf_file)" size="sm" class="btn btn_Dark py-2 px-5  rounded_0" type="button" > تحميل الملف</b-button>

            </div>
          </div>

        </b-col>
        <b-col cols="12"  lg="4" class="px-2 my-3" v-if="CurentLessons_data.pdf_files !== null && CurentLessons_data.pdf_files[1]">
          <div class="bg py-2 px-3 rounded_1">
            <div class="d-flex">
              <img :src="require(`~/assets/icon/Group 35243.svg`)"  class="ml-2" alt="icon"/>
              <div>
                <h6 class="font-weight-bold">ملف {{CurentLessons_data.pdf_files[1].file_name}}</h6>
                <p>ملف امتحان {{CurentLessons_data.pdf_files[1].file_name}} .... سؤال</p>
              </div>
            </div>
            <div class="d-flex mx-auto mt-5 justify-content-center ">
              <a  :href="CurentLessons_data.pdf_files[1].pdf_file.url" target="_blank">
                <img :src="require(`~/assets/icon/pdf0.svg`)" class="ml-2" alt="icon"/>
              </a>
              <p class="my-0">
                <span class="ml-1">بحجم</span>
                {{Math.ceil(CurentLessons_data.pdf_files[1].pdf_file.filesize/1000000)}}
                <sapn class="mr-1">ميجا</sapn>
              </p>
            </div>

            <div class="d-flex mt-4 justify-content-center ">
              <b-button v-on:click="DownLoad(CurentLessons_data.pdf_files[1].pdf_file)" size="sm" class="btn btn_Dark py-2 px-5  rounded_0" type="button" > تحميل الملف</b-button>

            </div>
          </div>

        </b-col>
        <b-col cols="12"  lg="4" class="px-2 my-3" v-if="CurentLessons_data.pdf_files !== null && CurentLessons_data.pdf_files[2]">
          <div class="bg py-2 px-3 rounded_1">
            <div class="d-flex">
              <img :src="require(`~/assets/icon/Group 35244.svg`)"  class="ml-2" alt="icon"/>
              <div>
                <h6 class="font-weight-bold">ملف {{CurentLessons_data.pdf_files[2].file_name}}</h6>
                <p>ملف امتحان {{CurentLessons_data.pdf_files[2].file_name}} .... سؤال</p>
              </div>
            </div>
            <div class="d-flex mx-auto mt-5 justify-content-center ">
              <a  :href="CurentLessons_data.pdf_files[2].pdf_file.url" target="_blank">
                <img :src="require(`~/assets/icon/pdf0.svg`)" class="ml-2" alt="icon"/>
              </a>
              <p class="my-0">
                <span class="ml-1">بحجم</span>
                {{Math.ceil(CurentLessons_data.pdf_files[2].pdf_file.filesize/1000000)}}
                <sapn class="mr-1">ميجا</sapn>
              </p>
            </div>

            <div class="d-flex mt-4 justify-content-center ">
              <b-button v-on:click="DownLoad(CurentLessons_data.pdf_files[2].pdf_file)" size="sm" class="btn btn_Dark py-2 px-5  rounded_0" type="button" > تحميل الملف</b-button>

            </div>
          </div>

        </b-col>
      </b-row>
    </div>
    <div v-else>
      <h5 class="text-center">لا يوجد ملفات ملحقة</h5>
    </div>
  </div>

</template>

<script>
export default {
props:["CurentLessons_data"],

mounted(){

},

methods:{
  DownLoad(pdf_file){
        var FileSaver = require('file-saver');

        var blob = new Blob(["Hello, world!"], {type: "text/plain;charset=utf-8"});

        // FileSaver.saveAs(blob, "hello world.txt");
        var oReq = new XMLHttpRequest();
        // The Endpoint of your server
        var URLToPDF = pdf_file.url;

        // Configure XMLHttpRequest
        oReq.open("GET", URLToPDF, true);

        // Important to use the blob response type
        oReq.responseType = "blob";

        // When the file request finishes
        // Is up to you, the configuration for error events etc.
        oReq.onload = function() {
            // Once the file is downloaded, open a new window with the PDF
            // Remember to allow the POP-UPS in your browser
            var file = new Blob([oReq.response], {
                type: 'application/pdf'
            });

            // Generate file download directly in the browser !
            saveAs(file, pdf_file.filename);
        };

        oReq.send();
        setTimeout(() => {
          if(oReq.status === 0){
            alert("You must give permission to download from the browser settings")
          }
        }, 2000);
  },
}
}
</script>

<style scoped>

  .bg{
    background-color: #F6F4F4;
  }

</style>

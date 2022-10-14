<template>
  <div>

    <div id="list1" class="dropdown-check-list cursor_pointer bgGray0 width_30 rounded_0 p-2 mt-3 font-16" tabindex="100">
      <span class="anchor ">
        <img :src="require(`~/assets/icon/folder4.svg`)" class="icon_sm ml-2" alt="icon"/>
        <span class="pl-5 text-dark"> اضف السؤال لمجلد</span>
      </span>
      <ul class="items FoldersListCheckbox mt-2"  v-for="list in Folders" :key="list.index">
        <div class="d-flex justify-content-between">
          <li class="d-flex" v-on:click="AddQuestion(Quiz_data[Quiz_serial],list)">
            <input type="checkbox" :class="list.name" :id="list.name"/>
            <label :for="list.name" class="mx-2">{{list.name}}</label>
          </li>

          <div>
            <span
              class="cursor_pointer text-danger font-weight-bold"
              v-on:click="RemaoveFolder(list)"
            >x
            </span>
            <span
              class="cursor_pointer font-weight-bold"
              v-on:click="EditFolderListCheckboxItem = list; EditeListName = list.title"
              v-b-modal.modal-EditList
            >
            <img :src="require(`~/assets/icon/edit.png`)" class="icon mr-2" alt="icon"/>
            </span>
          </div>
        </div>

      </ul>
    </div>

    <b-modal id="modal-EditList" title="تعديل اسم المجلد" hide-footer>
      <b-form-input v-model="EditeListName" class="my-4" placeholder="اكتب اسم المجلد"></b-form-input>
      <b-button size="sm" class="btn btn_Green my-2 py-2 px-r px-l rounded_0" type="button"  v-on:click="EditFolderListCheckbox(EditFolderListCheckboxItem)"> تعديل</b-button>
    </b-modal>

    <img
      :src="require(`~/assets/icon/plus.png`)"
      class="icon_plus mr-3 cursor_pointer"
      alt="icon"
      v-b-modal.modal-addList
    />

    <b-modal id="modal-addList" title="إضافة مجلد جديد" hide-footer>
      <b-form-input v-model="ListName" class="my-4" placeholder="اكتب اسم المجلد"></b-form-input>
      <b-button size="sm" class="btn btn_Green my-2 py-2 px-r px-l rounded_0" type="button"  v-on:click="AddFolders"> إنشاء</b-button>
    </b-modal>
  </div>
</template>

<script>
import config from "@/config";

export default {
  props : ["Quiz_data","Quiz_serial"],
  data (){
    return {
      ListName: '',
      EditeListName:'',
      Folders:[],
      EditFolderListCheckboxItem: '',
    }
  },
  mounted() {
    setTimeout(() => {
      this.Drop();
      this.fetchFolders();
    }, 1000);
  },
  methods: {
    Drop(){
      var checkList = document.getElementById('list1');
      checkList.getElementsByClassName('anchor')[0].onclick = function(evt) {
        checkList.classList.toggle('visible');
      }
    },
    RemaoveFolder(list){
      var myHeaders = new Headers();
      myHeaders.append("Authorization", `Bearer${config.token}`);

      var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        redirect: 'follow'
      };

      fetch(config.apiUrl+`wp-json/learnpress/v1/folders/${parseInt(list.id)}`, requestOptions)
        .then(response => response.text())
        .then(result =>{
          console.log("RemaoveFolder",JSON.parse(result))
          this.fetchFolders()
        })
        .catch(error => console.log('error', error));
    },
    EditFolderListCheckbox(item){
      console.log("EditFolderListCheckbox",item)
      this.FoldersList.forEach(ele => {
        if(ele.title === item.title){
          item.title = this.EditeListName;
        }
      });
    },
    fetchFolders(){
      var myHeaders = new Headers();
      myHeaders.append("Authorization", `Bearer${config.token}`);
      myHeaders.append("Cookie", "__wpdm_client=9a6d88491b5c975242839b1e203e9118");


      var requestOptions = {
        method: 'GET',
        headers: myHeaders,
        redirect: 'follow'
      };

      fetch(config.apiUrl+"wp-json/learnpress/v1/folders/", requestOptions)
        .then(response => response.text())
        .then(result =>{
          this.Folders = JSON.parse(result)
          console.log("JSON.parse(result)",JSON.parse(result))
        })
        .catch(error => console.log('error f', error));
    },
    AddFolders(){
      if(this.ListName !== ''){
        var myHeaders = new Headers();
        myHeaders.append("Authorization", `Bearer${config.token}`);
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Cookie", "__wpdm_client=9a6d88491b5c975242839b1e203e9118");

        var raw = JSON.stringify({
          "name": this.ListName
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch(config.apiUrl+"wp-json/learnpress/v1/folders/", requestOptions)
          .then(response => response.text())
          .then(result => {
            this.fetchFolders()
          })
          .catch(error => console.log('error', error));
      }
    },
    AddQuestion(question,folder){
      var myHeaders = new Headers();
      myHeaders.append("Authorization", `Bearer${config.token}`);
      myHeaders.append("Content-Type", "application/json");
      myHeaders.append("Cookie", "__wpdm_client=9a6d88491b5c975242839b1e203e9118");

      var raw = JSON.stringify({
        "folder_id": parseInt(folder.id),
        "question_id": question.id
      });

      var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
      };

      fetch(config.apiUrl+"wp-json/learnpress/v1/folders/question", requestOptions)
        .then(response => response.text())
        .then(result => {
          console.log("AddQuestion",JSON.parse(result))
        })
        .catch(error => console.log('error', error));
    },
  }
}

</script>



<style scoped>
.dropdown-check-list {
  display: inline-block;
}

.dropdown-check-list .anchor {
  position: relative;
  cursor: pointer;
  display: inline-block;
}

.dropdown-check-list .anchor:after {
  position: absolute;
  content: "";
  border-left: 2px solid #1D1F31;
  border-top: 2px solid #1D1F31;
  padding: 5px;
  right: 190px;
  top: 20%;
  transform: rotate(-135deg);
}

.dropdown-check-list .anchor:active:after {
  right: 190px;
  top: 21%;
}

.dropdown-check-list ul.items {
  padding: 2px;
  display: none;
  margin: 0;
  border-top: none;
}

.dropdown-check-list ul.items li {
  list-style: none;

}

.dropdown-check-list.visible .anchor {
  color: #0094ff;
}

.dropdown-check-list.visible .items {
  display: block;
}

.icon_sm{
  width: 20px;
}
.icon_plus{
  width: 30px;
  height: 30px;
}
.width_30{
  min-width: 200px;
}
.gridSy{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
}


</style>

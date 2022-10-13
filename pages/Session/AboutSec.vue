<template>
  <div>
    <p v-html="data.content"></p>
    <h5 class="text_orange mt-4">
      تقييم الدورة
    </h5>
    <div class="d-flex">
      <img :src="require(`~/assets/icon/star (12).svg`)" class="star" alt="icon"/>
      <img :src="require(`~/assets/icon/star (12).svg`)" class="star" alt="icon"/>
      <img :src="require(`~/assets/icon/star (12).svg`)" class="star" alt="icon"/>
      <img :src="require(`~/assets/icon/star (12).svg`)" class="star" alt="icon"/>
      <span class="mr-5">تقييم الدورة (5.0)</span>

    </div>
    <LastNews/>
  </div>
</template>
<script>
import LastNews from '@/components/LastNews';


export default {
  props: ["data"],
  components:{
    LastNews,
  },

}
</script>

<style scoped>
.star{
  width: 20px;
  margin: auto 5px;
}
</style>

<template>
  <Swiper>
    <SwiperItem v-for="item in banners">
      <a :href="item.link">
        <img :src="item.image" alt="" @load="imageLoad">
      </a>
    </SwiperItem>
  </Swiper>
</template>

<script>
import {Swiper, SwiperItem} from "components/common/swiper"
export default {
  name: "HomeSwiper",
  props:{
    banners: {
      type: Array,
      default() {
        return []
      }
    }
  },
  data(){
    return {
      isLoad:false,
    //  记录是否emit过
    }
  },
  components:{
    Swiper,
    SwiperItem
  },
  methods:{
    imageLoad() {
      if (!this.isLoad) {
        this.$emit('swiperImageLoad')
        this.isLoad = true
        // this.isLoad 状态改为true控制 只发送一次emit
      }
    }

    }

}
</script>

<style scoped>

</style>

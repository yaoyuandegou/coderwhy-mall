<template>
  <div class="tab-bar-item" @click="itemClick">
      <slot v-if="!isActive" name="item-icon"></slot>
      <slot v-else name="item-icon-active"></slot>
      <div :style="activeStyle" class="title">
        <slot name="item-text"></slot>
      </div>
  </div>
</template>

<script>
export default {
  name:"TabBarItem",
  components:{},
  props:{
      path:String,
      activeColor:{
          type:String,
          default:"#5d63ce"
      }
  },
  data(){
    return {
       
    }
  },
  computed:{
      isActive(){
          return this.$route.path==this.path;
      },
      activeStyle(){
          return {
              color:this.isActive?this.activeColor:''
          }
      },
  },
  methods:{
      itemClick(){
          if(!this.isActive){
              this.$router.replace(this.path);
          };
      },
  },
}
</script>
<style lang="less" scoped>
.tab-bar-item{
    text-align: center;
    padding:16px 0;
    flex:1;
    img{
        vertical-align: middle;
        width:20px;
        padding-bottom:6px;
        opacity: 0.3;
    }
    .title{
        line-height: 1;
        color:#999;
        font-size: 12px;
    }

}
</style>
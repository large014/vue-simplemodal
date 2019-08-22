<template>
  <!-- <transition name="modal-transition"> -->
    <div ref="simpleModal" class="simpleModal_wrappear">
      <div class="bg" @click="hide"></div>
      <div ref="modal_inner">
        <slot name="modalCloseBtn"></slot>
        <slot name="modalContents"></slot>
      </div>
    </div>
  <!-- </transition> -->
</template>

<script>

export default {
  name: 'SimpleModal',
  props: {
    msg: String,
    transitionType:String,
  },
  data(){
    return{
      isShow:false,
      scrollTop:0
    }
  },
  created() {
      this.$root.$on('modal-hide-evt', this.hide);
      this.$root.$on('modal-show-evt', this.show);
  },

  methods:{
    hide(){
      console.log('hide');
      let body = document.getElementsByTagName('body')[0];
      body.style.position="";
      body.style.left="";
      body.style.right="";
      window.scrollTo(0, this.scrollTop)
      this.$refs.simpleModal.classList.remove(this.transitionType);
      this.isShow = false;
    },
    show(){
      console.log('show');
      this.isShow = true;
      let body = document.getElementsByTagName('body')[0];
      this.scrollTop = document.documentElement.scrollTop || document.body.scrollTop
      console.log('scrollTop = ' + this.scrollTop);
      body.style.position="fixed";
      body.style.left="0";
      body.style.right="0";
      body.style.top=( this.scrollTop*-1 ) + "px";
      this.$refs.simpleModal.classList.add(this.transitionType);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.simpleModal_wrappear{
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
  visibility: hidden;
  transition: opacity .3s ease;
  opacity: 0;
  &.fead{
    visibility: visible;
    opacity: 1;
  }
}

.bg{
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.35);
}

.v-enter-active,
.v-leave-active {
    transition: opacity .3s ease-out;
}

.v-enter,
.v-leave-to {
    opacity: 0;
}

</style>

<template>
    <div ref="simpleModal" class="simpleModal_wrappear" :style="styles">
      <div class="bg" @click="hide"></div>
      <div ref="modal_inner">
        <slot name="modalCloseBtn"></slot>
        <div ref="modalContents" class="modalContents">
          <slot name="modalContents"></slot>
        </div>
      </div>
    </div>
</template>

<script>

export default {
  name: 'SimpleModal',
  props: {
    color:{},
  },
  data(){
    return{
      isShow:false,
      scrollTop:0
    }
  },
  computed:{
    styles(){
      return{
        '--color': this.color,
      }
    }
  },
  created() {
      this.$root.$on('modal-hide-evt', this.hide);
      this.$root.$on('modal-show-evt', this.show);
  },
  mounted(){
  },
  destroyed(){
      this.$root.$off('modal-hide-evt', this.hide);
      this.$root.$off('modal-show-evt', this.show);
  },
  methods:{
    hide(){
      let body = document.getElementsByTagName('body')[0];
      body.style.position="";
      body.style.left="";
      body.style.right="";
      window.scrollTo(0, this.scrollTop)
      this.$refs.simpleModal.classList.remove("feadIn");
    },
    show(){
      let body = document.getElementsByTagName('body')[0];
      this.scrollTop = document.documentElement.scrollTop || document.body.scrollTop
      body.style.position="fixed";
      body.style.left="0";
      body.style.right="0";
      body.style.top=( this.scrollTop*-1 ) + "px";

      //---- transition
      this.$refs.simpleModal.classList.add("feadIn");
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
  &.feadIn{
    visibility: visible;
    opacity: 1;
  }
  --color : rgba(0, 0, 0, 0.35);
  .bg{
    width: 100%;
    height: 100%;
    background-color:var(--color);
  }
}


.modalContents{
  transition: transform .3s ease;
}

</style>

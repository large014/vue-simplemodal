<template>
  <div id="app">
    <div class="debugUI">
      <button @click="modalShow">表示</button>
      <button @click="modalHide">非表示</button>
    </div>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <SimpleModal ref="simplemodal" transitionType="fead">
      <CloseBtn slot="modalCloseBtn"/>
      <!-- <TestDialog/> -->
      <SimpleDialog slot="modalContents" title="これはテスト" msg="This will reset your device to its default factory settings." btn1_txt="CANCEL" btn2_txt="ACCEPT"/>
    </SimpleModal>
  </div>
</template>

<script>
import SimpleModal from './components/modal/SimpleModal.vue'
import SimpleDialog from './components/modal/SimpleDialog.vue'
import CloseBtn from './components/modal/CloseBtn.vue'
// import TestDialog from './components/modal/TestDialog.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    SimpleModal,
    // TestDialog,
    SimpleDialog,
    CloseBtn,
    HelloWorld
  },
  methods:{
    modalShow(){
      this.$refs.simplemodal.show();
    },
    modalHide(){
      this.$refs.simplemodal.hide();
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.debugUI{
  position: fixed;
  bottom: 50px;
  right: 0;
  border: 1px solid #000;
  padding: 10px;
  button{
    display: block;
    width: 100px;
    border: 1px solid #000;
    border-radius: 4px;
    padding: 10px;
  }
  button:first-child{
    margin-bottom: 10px;
  }
}
</style>

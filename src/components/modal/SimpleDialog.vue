<template>
  <div ref="simpleDialog" class="simpleDialog_wrappear">
    <div class="inner">
      <p class="title">{{title}}</p>
      <p class="msg">{{msg}}</p>
      <div class="uiarea">
        <p ref="btn1" class="btn _1">{{btn1_txt}}</p>
        <p ref="btn2" class="btn _2">{{btn2_txt}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SimpleDialog',
  props: {
    title: String,
    msg: String,
    btn1_txt : String,
    btn2_txt : String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.simpleDialog_wrappear{
  width: 100%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 0 30px;

}

.inner{
  background-color: #FFF;
  border-radius: 10px;
  padding: 20px 10px;
}

.title{
  margin-bottom: 10px;
}

.msg{
  margin-bottom: 20px;
}

.uiarea{
  display: flex;
  justify-content: flex-end;
}

.btn{
  &._1{
    margin-right: 10px;
  }
}


</style>

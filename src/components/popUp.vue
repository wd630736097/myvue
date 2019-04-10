<template>
<div class = 'popUp'>
    <div class = 'popTitle'>
        提示信息
        <div class = 'x' @click = 'popCancle'>X</div>
    </div>
    <div class = 'proContent'>
        确定要删除该项🐴？
        <button class = 'bY' @click = 'Ydelete'>确定</button>
        <button class = 'bN' @click = 'popCancle'>取消</button>
    </div>
</div>
</template>

<script>
export default {
  methods: {
    Ydelete () {
      this.$parent.delete()
    },
    popCancle () {
      this.$parent.popNoShow()
    }
  }
}
</script>

<style>
.popUp {
    color: white;
    position: absolute;
    z-index: 10;
    top: 50%;
    left: 50%;
    height: 100px;
    width: 200px;
    margin: -50px 0 0 -100px;
    border: #56688f solid 1px;
    background-color: #ddd9cf;
}
.popTitle {
    height: 25px;
    background-color: #0f5ce9;
}
.x {
    position: relative;
    text-align: center;
    border: black solid 1px;
    top: 1px;
    left: -5px;
    background-color: #dce4e4;
    height: 20px;
    width: 15px;
    float: right;
    overflow: hidden;
}
.proContent {
    margin-top: 10px;
    text-align: center;
    color: black;
}
.proContent button {
    border: black solid 1px;
    background-color: #dce4e4;
    box-shadow: 0px 0px 3px #e43938;
}
.bY {
    position: absolute;
    top:75px;
    left:110px;
}
.bN {
    position: absolute;
    top:75px;
    left:140px;
}
</style>

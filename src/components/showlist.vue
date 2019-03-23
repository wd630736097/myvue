<template>
<div class = 'tobuy'>
  <li>
    <input class = 'select' type = 'radio' :checked = item.checked @click = 'itemcheck'>
    <img :src = 'item.imgPic' class = 'itemimg'>
    <div class = 'itemname'>{{item.name}}</div>
    <div class = 'free'>
    赠品:
    <p>{{item.gifts[0].partName}}</p>
    </div>
    <div class = 'price'>{{item.price}}</div>
    <button class = 'buttonm' @click = 'numm'>-</button>
    <input class = 'number' v-model = item.count>
    <button class = 'buttonp' @click = 'nump'>+</button>
    <div class = 'sum' >{{item.count * item.price}}</div>
    <img :src = 'deleteicon' class = 'dicon'>
  </li>
</div>
</template>

<script>
export default {
  props: ['item', 'index'],
  data () {
    return {
      inputValue: '',
      deleteicon: '../../static/img/delete.png',
      sumprice: ''
    }
  },
  methods: {
    itemcheck: function () {
      this.item.checked = !this.item.checked
      this.$parent.calctotalmoney()
    },
    nump: function () {
      this.item.count++
      this.$parent.calctotalmoney()
    },
    numm: function () {
      if (this.item.count > 1) {
        this.item.count--
        this.$parent.calctotalmoney()
      } else {
        this.item.count = 1
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
li {
    list-style-type: none;
    height: 130px;
    width: 1200px;
    overflow: hidden;
    margin-top: 20px;
    margin-bottom: -60px;

}
.select{
    position: relative;
    top: 10px;
    left: 50px;
}
.itemimg {
    position: relative;
    top: 30px;
    left: 100px;
    height: 60px;
    width: 60px;
}
.itemname{
    position: relative;
    top: -40px;
    left: 200px;
}
.free {
    position: relative;
    top: -23px;
    left: 200px;
    overflow: hidden;
}
.free p {
    color: #ccc;
    position: relative;
    left: 50px;
    top: -22px;
}
.number {
    position: relative;
    height: 25px;
    width: 80px;
    border: 1px solid #ccc;
    left: 695px;
    top: -115px;
}
.buttonm {
    position: relative;
    height: 18px;
    width: 18px;
    left: 680px;
    top: -115px;
}
.buttonp {
    position: relative;
    height: 18px;
    width: 18px;
    left: 700px;
    top: -115px;
}
.price {
    color:#e4393c;
    position: relative;
    height: 25px;
    left: 565px;
    top: -90px;
}
.sum {
    position: relative;
    top: -140px;
    left: 910px;
    color: #ee4433
}
.dicon {
    position: relative;
    top: -170px;
    left: 1070px;
    height: 40px;
    width: 40px;
}

</style>

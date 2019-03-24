<template>
  <div>
    <div>
      <span class = 'spanline'></span>
      <h1>购物车</h1>
    </div>
    <div class = 'table'>
      <div class = 'tabletitle'>
        <p class = 'op'>商品信息</p>
        <p class = 'tp'>商品金额</p>
        <p class = 'thp'>商品数量</p>
        <p class = 'thp'>总金额</p>
        <p class = 'thp'>编辑</p>
      </div>
      <div>
        <ul>
          <listshow
          v-for= '(item,index) of list' :key = index
          :item = 'item'
          :list = 'list'
          :msg = 'msg'
          >
          </listshow>
        </ul>
      </div>
      <div class = 'tablebottom'>
        <input class = 'checkbox' type = 'checkbox' :checked = 'checkall' @click = 'ifcheckall ()'>
        <div class = 'selectAll' @click = 'mcheckall ()'>全选</div>
        <div class = 'noselectAll' @click = 'mnocheckall()'>取消全选</div>
        <div class = 'sumPrice'>{{totalmoney}}</div>
        <button>结算</button>
      </div>
    </div>
    <!-- <img :src = 'list[0].imgPic'> -->
    <!-- <router-view/> -->
  </div>
</template>

<script>
import showlist from './components/showlist'
export default {
  components: {
    'listshow': showlist
  },
  data () {
    return {
      msg: 'helloworld',
      checkall: false,
      item: '',
      totalmoney: 0,
      list: [
        {
          'name': '面具1',
          'checked': false,
          'price': 19,
          'count': 1,
          'amount': 19,
          'imgPic': '../static/img/test1.jpg',
          'gifts': [
            {
              'partId': '10001',
              'partName': '火'
            },
            {
              'partId': '10002',
              'partName': '火柴'
            }
          ]
        },
        {
          'name': '面具2',
          'checked': false,
          'price': 20,
          'count': 1,
          'amount': 20,
          'imgPic': '../static/img/test.jpg',
          'gifts': [
            {
              'partId': '10001',
              'partName': '打'
            },
            {
              'partId': '10002',
              'partName': '火柴盒'
            }
          ]
        },
        {
          'name': '面具3',
          'checked': false,
          'price': 21,
          'count': 1,
          'amount': 20,
          'imgPic': '../static/img/goods-1.jpg',
          'gifts': [
            {
              'partId': '10001',
              'partName': '机'
            },
            {
              'partId': '10002',
              'partName': '火柴盒'
            }
          ]
        }
      ]
    }
  },
  methods: {
    ifcheckall () {
      this.checkall = !this.checkall
      this.list.forEach((item) => {
        item.checked = this.checkall
        this.calctotalmoney()
      })
      // if (this.checkall) {
      //   this.list.forEach(function (item, checkall) {
      //     item.checked = true
      //   })
      // } else {
      //   this.list.forEach(function (item, checkall) {
      //     item.checked = false
      //   })
      // }
      // console.log(checked)
    },
    mcheckall: function () {
      this.checkall = true
      this.list.forEach((item) => {
        item.checked = true
      })
      this.calctotalmoney()
    },
    mnocheckall: function () {
      this.checkall = false
      this.list.forEach((item) => {
        item.checked = false
      })
      this.calctotalmoney()
    },
    calctotalmoney: function () {
      this.totalmoney = 0
      this.list.forEach((item) => {
        if (item.checked) {
          this.totalmoney += item.count * item.price
        }
      })
    },
    ifcheckallclick () {
      let i = 0
      this.list.forEach((item) => {
        if (item.checked) {
          i++
        }
      })
      if (i === this.list.length) {
        this.checkall = true
      } else if (i !== this.list.length) {
        this.checkall = false
      }
    }
  }
}
</script>

<style>
* {
  border: 0px;
  margin:0px;
  padding: 0px;
}
#app {

}
h1 {
  padding: 20px 20px;
  color: #605f5f;
  text-align: center;
  z-index: 10;
  background-color: white;
}
.spanline {
  width: 1200px;
  position: absolute;
  left: 50%;
  top: 40px;
  margin-left: -600px;
  border-bottom: 1px solid #605f5f;
}
.table {
  width: 1200px;
  border: 1px solid #605f5f;
  position: absolute;
  top: 100px;
  left: 50%;
  margin-left: -600px;
}
.tabletitle {
  height: 50px;
  color: white;
  background-color: #605f5f;
}
.tabletitle p {
  position: relative;
  display: inline;
  top: 10px;
  font-size: 20px;
}
.op {
  margin-left: 220px;
}
.tp {
  margin-left: 230px;
}
.thp {
  margin-left: 100px;
}
.tablebottom {
  width: 1200px;
  position: relative;
  left: 50%;
  bottom: -80px;
  margin-left: -600px;
}
.tablebottom input {
  position: relative;
  top: 20px;
  height: 20px;
  width: 20px;
  margin-right: 20px;
}
.selectAll {
  position: relative;
  top: 20px;
  display: inline-block;
  font-size: 20px;
}
.noselectAll {
  position: relative;
  top: 20px;
  display: inline-block;
  font-size: 20px;
}
.tablebottom button {
  position: relative;
  top: 20px;
  left: 740px;
  display: inline-block;
  width: 220px;
  height: 55px;
  color: white;
  font-size: 20px;
  background-color:#E43537;
}
.sumPrice {
  position: relative;
  top: 20px;
  left: 750px;
  width: 60px;
  display: inline-block;
  color: #e4393c;
  font-size: 20px;
}
.checkbox {
  border-radius: 50%
}
</style>

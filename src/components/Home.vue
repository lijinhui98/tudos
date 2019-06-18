<template>
  <div>
    <div class="bigBox">
      <div class="ip_box">
        <input type="text" class="ip" @keyup.enter="handleAdd($event)" v-model="val">
        <button class="btn" @click="handlePush">发布</button>
      </div>
      <ul>
        <li><input type="checkbox" @click='handleCkb'></li>
        <li v-for="(item, index) in data" :key="index">
        <input type="checkbox" v-model="qx">
          {{item}}
          <button class="del" @click="handleDel(index)">删除</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        data: [],
        val: [],
        qx:false
      };
    },
    methods: {
      handleAdd(e) {
        if (e.target.value == "") {
          return;
        }
        this.data.push(e.target.value);
      },
      handlePush() {
        if (this.val == "") {
          return;
        }
        this.data.push(this.val);
      },
      handleDel(i) {
        this.data.splice(i, 1);
      },
      handleCkb(){
          this.qx = !this.qx
      }
    },
    mounted() {}
  };
</script>

<style>
  * {
    margin: 0;
    padding: 0;
  }
  ul,
  li {
    list-style: none;
    margin-left: 30px;
  }
  li {
    margin-bottom: 10px;
  }
  .bigBox {
    width: 600px;
    height: 600px;
    margin: 100px auto;
    background: pink;
  }
  .ip_box {
    margin-left: 100px;
  }
  .ip {
    width: 300px;
    height: 50px;
    margin: 30px auto;
    border: 0;
    text-indent: 1em;
  }
  .btn {
    width: 80px;
    height: 50px;
  }
  .del {
    float: right;
    margin-right: 30px;
    width: 80px;
    height: 30px;
  }
</style>

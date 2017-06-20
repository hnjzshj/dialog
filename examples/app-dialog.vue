<template>
  <div class="dialog-container">
    <div class="mask"></div>
    <div class="dialog-model">
      <div class="dialog-title clearfix">        
        <span @click="closeDialog">关闭</span>
        <h3><slot name="dialogTitle"></slot></h3>
      </div>
      <div class="dialog-mod">
        <slot name="dialogMod"></slot>
      </div>
      <div class="dialog-btn clearfix">
        <button class="app-btn app-btn-default" @click="closeDialog">取消</button>
        <button class="app-btn app-btn-info">确定</button>
      </div>
    </div>

  </div>
</template>
<script>
  export default{
    props: ['isShowDialog'],
    data(){
      return {
        myResult: this.isShowDialog
      }
    },
    watch: {
      isShowDialog(val){
        this.myResult = val
      },
      myResult(val){
        this.$emit("dialogChange", val)
      }
    },
    methods: {
      closeDialog: function () {
        this.myResult = false;
      },
      closeMask:function(){
        this.myResult=false
      }
    }
  }
</script>
<style>
.clearfix::before,
.clearfix::after {
  content: " ";
}

.clearfix::after {
  clear: both;
}
  /*遮罩*/
  .mask{
    background: rgba(0,0,0,0.1);
    width: 100%;
    height: 100%;
    left: 0px;
    top: 0px;
    z-index: 98;
    /*opacity: 0.4;*/
    position: fixed;
    /*filter: alpha(opacity=90);*/
    /*display: none;*/
    overflow: hidden;
  }
  .dialog-container{
    width:100%;
    height:100%;
    left: 0;
    top:0;
    position: fixed;
  }
  .dialog-model {
    width: 33%;
    left:50%;
    top:50%;
    margin-top:-15%;
    margin-left:-16.5%;
    background: #fff;
    border-radius: 8px;
    padding: 10px 20px 20px 20px;
    box-sizing: border-box;
    z-index: 9999;
    position: absolute;
  }

  /*标题栏*/
  .dialog-title {
    line-height: 40px;
    margin-bottom: 40px;
  }

  .dialog-title h3 {
    font-size: 18px;
    float: left;
    font-weight: normal;
    color: #282828;
    display: inline-block;
        -webkit-margin-before: 0em;
    -webkit-margin-after: 0em;
    -webkit-margin-start: 0px;
    -webkit-margin-end: 0px;
  }

  .dialog-title span {
    float: right;
    color: rgba(0, 0, 0, 0.3);
    font-size: 15px;
    cursor: pointer;
    display: inline-block;
  }

  /*主要内容*/
  .dialog-mod {
    font-size: 14px;
    padding: 30px 0;
    color: #333;
    text-align: left;
  }

  /*按钮*/
  .app-btn {
  height: 36px;
  box-sizing: border-box;
  -webkit-border-radius: 18px;
  -moz-border-radius: 18px;
  border-radius: 18px;
  display: block;
  padding: 0px 20px;
  outline: 0 !important;
  cursor: pointer;
}
.app-btn-default {
  border: 1px solid #666;
  color: #b9b9b9;
  background: rgba(0, 0, 0, 0);
}

.app-btn-default:hover {
  border: 1px solid #4e93d5;
  color: #4e93d5;
}

.app-btn-default:active {
  border: 1px solid #666;
  color: #b9b9b9;
}
.app-btn-info {
  border: 0;
  color: #fff;
  background: #4e93d5;
}

.app-btn-info:hover {
  border: 0;
  color: #fff;
  background: #72b9fd;
}

.app-btn-info:active {
  border: 0;
  color: #F6F9FB;
  background: #3B76AE;
}
  .dialog-btn {
    text-align: right;
  }

  .dialog-btn button {
    display: inline-block;
  }
</style>

<template>
  <div id="app">
    <div>
      <div @click="openDialog()"><a  href="javascript:void(0)">Dialog框点我试试</a></div>
      <transition name="dialogToggle">
        <app-dialog v-if='isShowDialog' @dialogChange="onResultChange">
          <h3 slot="dialogTitle">角色信息录入</h3>
          <div slot="dialogMod">此操作将永久删除该文件，是否继续？</div>
        </app-dialog>
      </transition>
    </div>
  
  </div>
</template>

<script>
import appDialog from '../examples/app-dialog.vue'
export default {
  data() {
    return {
      isShowDialog: false
    }
  },
  methods: {
    openDialog: function () {
      this.isShowDialog = true;
    },
    onResultChange(val) {//
      this.isShowDialog = val;
    }
  },
  components: {
    appDialog
  }
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app a{
  color: #333;
  text-decoration: none;
}
.dialogToggle-enter-active {
  animation: bounce-in .5s;
}

.dialogToggle-leave-active {
  animation: bounce-out .5s;
}

@keyframes bounce-in {
  0% {
    opacity: 0;
    transform: translateY(60px)
  }
  100% {
    opacity: 1;
    transform: translateY(0)
  }
}

@keyframes bounce-out {
  0% {
    opacity: 1;
    transform: translateY(0)
  }
  100% {
    opacity: 0;
    transform: translateY(60px)
  }
}
</style>


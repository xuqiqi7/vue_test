<template>
  <h2>我是About的内容</h2>
</template>

<script>
export default {
  name: "About",
  beforeDestroy() {
    console.log("About组件即将销毁");
  },
  mounted() {
    console.log("About组件挂载完毕", this);
  },
  //通过路由规则，进入该组件时被调用
  beforeRouteEnter(to, from, next) {
    console.log("前置路由守卫", to, from);
    if (to.meta.isAuth) {
      //判断是否需要鉴权
      if (localStorage.getItem("school") === "atguigu") {
        next();
      } else {
        alert("学校名不对，无权查看");
      }
    } else {
      next();
    }
  },
  //通过路由规则，离开该组件时被调用
  beforeRouteLeave(to, from, next) {
    next();
  },
};
</script>


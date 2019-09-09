<template>

  <div class="container">
    <div class="container_">
      <!-- 内容区 -->
      <section class="content">
        <!-- 必须给以下div命一个id名 方便锚点跳转 -->
        <div id="div1">
          div1
        </div>
        <div id="div2">
          div2
        </div>
        <div id="div3">
          div3
        </div>
        <div id="div4">
          div4
        </div>
      </section>
      <!-- 导航 -->
      <nav class="nav">
        <a href="javascript:void(0)" v-for= "item in navList" :key="item.lable" @click="clickNav(item.name)" @dbclick="clearClickObj">
          <i :class="clickObj == item.name? 'activeIcon':'unActiveIcon' "></i>
          <span>{{item.name}}</span>
        </a>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      clickObj: "", //被点击的导航
      navList: [//导航菜单
        { lable: 1, name: "div1" },
        { lable: 2, name: "div2" },
        { lable: 3, name: "div3" },
        { lable: 4, name: "div4" }
      ]
    };
  },
  methods: {
    // 导航点击事件
    clickNav(event) {
      this.clickObj = event; //记录点击的导航
      document.querySelector(`#${event}`).scrollIntoView(true);
    },
    // 双击事件
    clearClickObj(){
      this.clickObj = "";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  position: fixed;
  width: 100%;
  height: 100%;
}
.container_{
 display: flex;
  width: 1200px;
  height: 100%;
  margin: auto;
}
.content {
  height: 100%;
  overflow-y: auto;
  flex: 1;
}
#div1,
#div2,
#div3,
#div4 {
  height: 400px;
  color: #fff;
}
#div1 {
  background: #ccc;
}
#div2 {
  background: #999;
}
#div3 {
  background: #666;
}
#div4 {
  background: #333;
}
/* 导航 */
.nav {
  width: 200px;
  margin-left: 30px;
  display: flex;
  flex-direction: column;
}
.nav a {
  display: flex;
  align-items: center;
}
.nav a span {
  color: #666;
  margin-left: 6px;
}
.activeIcon {
  width: 0;
  height: 0;
  border-top: 6px solid transparent;
  border-bottom: 6px solid transparent;
  border-left: 8px solid #244bbf;
}
.unActiveIcon {
  width: 8px;
  height: 8px;
  border-radius: 100%;
  display: block;
  background: #ccc;
}
</style>

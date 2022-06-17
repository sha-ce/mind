<template>
  <div>
    <!-- ハンバーガーメニューのボタン -->
    <div class="button" :class="{'close-button':ActiveBtn}" @click="ActiveBtn=!ActiveBtn">
      <span class="icon-bar line-1" :class="{'close-1':ActiveBtn}"></span>
      <span class="icon-bar line-2" :class="{'close-2':ActiveBtn}"></span>
      <span class="icon-bar line-3" :class="{'close-3':ActiveBtn}"></span>
    </div>
    <!-- サイドメニュー -->
    <transition name="fade">
      <div v-if="ActiveBtn" class="nav-content">
      </div>
    </transition>
    <div v-if="ActiveBtn" class="close-area" @click="ActiveBtn=!ActiveBtn"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ActiveBtn: false,
      linkUrl1: "#",
      linkUrl2: "#",
      linkUrl3: "#",
      linkUrl4: "#"
    }
  }
};
</script>

<style scoped>
p {
  margin: 0;
  padding: 0;
}
.button {
  position: fixed;
  cursor: pointer;
  z-index: 100;
  padding: 10px;
  transition: 0.3s ease;
}
.icon-bar {
  display: block;
  width: max(4vh, 20px);
  height: 2px;
  background: gray;
}
.button:hover .icon-bar {
  box-shadow: 0 1px 1px 1px rgb(225, 225, 255);
}
.icon-bar + .icon-bar {
  margin-top: 8px;
}
.line-1, .line-2, .line-3 {
  transition: 0.3s ease;
}
/* ボタンアニメーション */
.close-1 {
  transform: translate3d(0, 10px, 0) rotate(-45deg);
  transition: 0.3s ease;
}
.close-2 {
  transition: 0.3s ease;
  opacity: 0;
}
.close-3 {
  transform: translate3d(0, -10px, 0) rotate(45deg);
  transition: 0.3s ease;
}
.close-button {
  background: white;
  border-radius: 10px/10px;
  position: fixed;
  left: 10px;
  transition: 0.3s ease;
}
/* ↑ボタンアニメーション */
.nav-content {
  margin: 0;
  padding: 10px 0 0 40px;
  position: fixed;
  top: 90px;
  left: 10px;
  /*height: 60%;*/
  display: inherit;
  background: white;
  pointer-events: auto;
  flex-direction: column;
  border-radius: 20px/20px;
  z-index: 99;
}
.nav-content:hover {
  box-shadow: 0 0 5px 0.5px rgb(225, 225, 255);
  transition: 0.3s ease;
}
.fade-enter-active, .fade-leave-active {
  opacity: 1;
  transition: 0.3s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
  transition: 0.3s ease;
}
.home {
  margin: 10px 0;
}
.list {
  padding-left: 20px;
}
.home,
.list {
  display: flex;
}
.icon {
  color: #303030;
  font-size: 15px;
}
.nav-content li a,
.nav-content li p {
  padding: 5px 5px;
  display: block;
  text-transform: uppercase;
  transition: color 0.1s;
  color: #303030;
  font-size: max(5%, 20px);
}
.nav-content:hover a, .nav-content:hover p{
  opacity: 0.5;
  transition: 0.3s ease;
}
.nav-content li a:hover {
  opacity: 0.8;
  color: rgb(100, 100, 255);
  transform: translate3d(-10px, 0, 0);
  transition: 0.3s ease;
}
.nav-container:focus-within .nav-content {
  transform: none;
}
a,
a:visited,
a:focus,
a:active,
a:link {
  text-decoration: none;
  outline: 0;
}
a {
  color: currentColor;
  transition: 0.2s ease-in-out;
}
ul {
  padding: 0;
  list-style: none;
}
.close-area {
  position: fixed;
  width: 100%;
  height: 100%;
}
/* スマホ以上 */
@media screen and (min-width: 481px) {
  .button {
    top: 20px;
    left: 20px;
  }
  .nav-content {
    width: 300px;
  }
}
/* スマホ幅 */
@media screen and (max-width: 480px) {
  .button {
    top: 10px;
    left: 10px;
  }
  .nav-content {
    width: 80%;
  }
}
</style>

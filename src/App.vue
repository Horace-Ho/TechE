<script setup>
import { RouterLink, RouterView } from 'vue-router'

import { ref } from 'vue'
const search = ref('')
const count = ref('')
const load = () => {
  if (count.value <= 40)
    return{
    count: count.value++,
    }
}
</script>

<template>
    <div class="common-layout">
      <el-container>
        <div>
        <el-aside width="260px" class="aside">
          <div class="search-input-size">
            <el-input
                v-model="search"
                class="search-input"
                size="large"
                placeholder="搜索"
            />
          </div>
          <el-menu class ="aside-menu"
                   :router = "true"

          >
            <el-menu-item index="/">
              <RouterLink to="/">
                <span>首页</span>
              </RouterLink>
            </el-menu-item>
            <el-menu-item index="/about">
              <RouterLink to="AboutView">
                <span>团队</span>
              </RouterLink>
            </el-menu-item>
            <el-menu-item index="/">
              <RouterLink to="/">
                <span>稍后阅读</span>
              </RouterLink>
            </el-menu-item>
            <el-menu-item index="/library">
              <RouterLink to="LibraryView">
                <span>资料库</span>
              </RouterLink>
            </el-menu-item>
          </el-menu>

          <div class="subscribe">
          <el-text type="info" class="info-text">订阅源</el-text>
          <el-menu class="aside-menu" mode="horizontal" :ellipsis="false">
            <el-menu-item>
              <router-link to="/">
                <span>添加</span>
              </router-link>
            </el-menu-item><el-menu-item>
            <router-link to="/">
              <span>管理文章</span>
            </router-link>
          </el-menu-item>
          </el-menu>

            <ul v-infinite-scroll="load" class="subscribe-list">
              <li v-for="i in count" :key="i" class="subscribe-list-item">
                <el-link :underline ="false">
                  <span>获取内容{{ i }}</span>
                </el-link>
              </li>
            </ul>
          </div>
          <el-menu class="aside-system"
                   text-color="#909399"
                   :router = "true"
                   mode="horizontal"
                   :ellipsis = "false"
          >
            <el-menu-item>
              <router-link to="/setting">
                <span>偏好设置</span>
              </router-link>
            </el-menu-item>

            <el-menu-item>
              <router-link to="/about">
                <span>关于项目</span>
              </router-link>
            </el-menu-item>
          </el-menu>

        </el-aside>
        </div>
        <el-container>
          <el-header height="60px" class="header">
            <div class="flex-grow" />
            <el-button type="default">Button</el-button>
            <el-avatar :size="36" :src="circleUrl" class="avatar"/>
          </el-header>

          <div  class="main">
          <el-main>
            <router-view />
          </el-main>
          </div>
        </el-container>
      </el-container>
    </div>
</template>

<style scoped>
.aside{
  background-color: #FAFAFA;
  height: 100vh; /* 视口高度 */
  overflow-y: auto; /* 侧边栏滚动条 */
  padding: 10px;
  position: fixed;
  top: 0;
  left: 0;
  width: 260px; /* 固定宽度 */
}

.header{
  height: 60px;
  border-bottom: #EBEEF5 1px solid;
  position: fixed;
  z-index: 1;
  width: calc(100% - 260px); /* 减去侧边栏宽度 */
  height: 60px; /* 头部高度 */
  border-bottom: #EBEEF5 1px solid;
  background-color: #FFFFFF;
  display: flex;
  align-items: center;
  justify-content: space-between;
  left: 260px; /* 与侧边栏宽度相同 */
}

.search-input{
  width: 100%;
}

.aside-menu{
  margin-top: 20px;
  border: none;
  background-color: #FAFAFA;
}

.el-menu-item{
  border-radius: 18px;
  height: 40px;
}

.info-text{
  margin-left: 20px;

}

.aside-system{
  position: absolute;
  bottom: 0;
  border: none;
  background-color: #FAFAFA;
}

a {
  text-decoration: none;
  outline: none;
  color: #000;
}

.header{
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.avatar{
  align-items: center;
  margin-left: 20px;
}

.flex-grow {
  flex-grow: 1;
}


.main{
  height: 100vh; /* 视口高度 */
  overflow-y: auto; /* 内容区域滚动条 */
  padding-top: 60px; /* 为顶部导航留出空间 */
  position: relative;
  left: 260px;
  width: calc(100vw - 260px); /* 计算剩余空间的宽度 */
}

.subscribe{
  position: relative;
  top: 20px;
}

.subscribe-list{
  height: 300px;
  overflow-y: auto;
}

.subscribe-list-item{
  height: 40px;
  line-height: 40px;
  list-style: none;
}

</style>

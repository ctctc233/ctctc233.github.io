<template>
  <div class="navbar">
    <!-- 头部信息 -->
    <!-- 并列布局容器 -->
    <div class="header-contact-container">
      <!-- 第一个 selectedCode -->
      <div class="header">
        <div class="title">
          <h1>重庆红岩联线文化发展管理中心</h1>
          <h2>Chongqing Hongyan Alliance Culture Development Management Center</h2>
          <h1>重庆红岩革命历史博物馆</h1>
          <h2>Chongqing Hongyan Revolution History Museum</h2>
        </div>
      </div>

      <!-- 第二个 selectedCode -->
      <div class="contact">
        <span>设为首页 | 加入收藏 | 热线：023-65312300（沙坪坝片区） 023-63303457（渝中片区） | <a href="#">English</a></span>
      </div>
      <!-- 搜索框保持原位置 -->

    </div>
    <div class="search">
      <input type="text" placeholder="请输入检索关键词" v-model="searchQuery">
      <button @click="handleSearch">搜索</button>
    </div>



    <!-- 导航菜单 -->
    <div class="menu">
      <ul>
        <li @click="changeComponent('Home')">首页</li>
        <li @click="changeComponent('About')">关于红岩</li>
        <li @click="toggleDynamicsMenu" class="dynamics">
          公告动态
          <ul v-if="showDynamicsMenu" class="submenu">
            <li @click="changeComponent('Information')">文博信息</li>
            <li @click="changeComponent('Government')">政务平台</li>
            <li @click="changeComponent('Notice')">公告</li>
            <li @click="changeComponent('Report')">专题报道</li>
          </ul>
        </li>
        <li @click="changeComponent('Collections')">馆藏精品</li>
        <li @click="changeComponent('Exhibition')">陈列展览</li>
        <li @click="changeComponent('Research')">研究开发</li>
        <li @click="changeComponent('Education')">公共教育</li>
        <li @click="changeComponent('Service')">参观服务</li>
        <li @click="changeComponent('Reservation')">网上预约</li>
      </ul>
    </div>
  </div>
</template>


<script>
// 229971110冯冰艺
export default {
  data() {
    return {
      showDynamicsMenu: false // 控制公告动态下拉菜单的显示状态
    };
  },
  methods: {
    changeComponent(componentName) {
      this.$emit('change-component', componentName);
      this.showDynamicsMenu = false; // 点击其他菜单项时，关闭公告动态下拉菜单
    },
    toggleDynamicsMenu() {
      this.showDynamicsMenu = !this.showDynamicsMenu;
    }
  },
};
</script>


<style scoped>

.header-contact-container {
  display: flex;
  justify-content: space-between; /* 两个子元素分布在两侧 */
  align-items: center; /* 垂直居中 */
  gap: 20px; /* 可选：两个块之间的间距 */
}

.search{
  display: flex;
  justify-content: flex-end;
}

.menu {
  ul {
    list-style-type: none;
    padding: 0;
    display: flex;
  }

  li {
    margin-right: 20px;
    position: relative; /* 为子菜单定位 */
  }

  .submenu {
    display: none;
    position: absolute;
    background-color: #fff;
    border: 1px solid #ccc;
    z-index: 1;
    left: 0;
    top: 100%;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }

  .submenu li {
    padding: 10px;
    cursor: pointer;
  }

  .submenu li:hover {
    background-color: #f0f0f0;
  }

  .dynamics:hover .submenu {
    display: block;
  }
}
</style>


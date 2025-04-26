<template>
  <header class="navbar">
    <div class="navbar-left">
      <router-link to="/" class="logo">MemorUS</router-link>
    </div>
    <nav class="navbar-right">
      <router-link to="/" class="nav-item" @click="scrollToSection('memories')">MEMORIES</router-link>
      <router-link to="/" class="nav-item" @click="scrollToSection('ourstory')">OUR STORY</router-link>
      <router-link to="/" class="nav-item" @click="scrollToSection('coming')">COMING SOON</router-link>
      <router-link to="/login" class="nav-item">LOGIN</router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'AppNavbar',
  methods: {
    // 클릭한 섹션으로 부드럽게 스크롤
    scrollToSection(sectionId) {
      const headerHeight = document.querySelector('.navbar').offsetHeight; // 상단 메뉴 높이
      const section = document.getElementById(sectionId); // 해당 섹션
      if (section) {
        const sectionTop = section.offsetTop; // 섹션 위치
        window.scrollTo({
          top: sectionTop - headerHeight, // 메뉴 높이 만큼 조정
          behavior: 'smooth', // 부드러운 스크롤
        });
      }
    },
  },
};
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: rgba(157, 201, 255, 0.2);
  backdrop-filter: blur(10px);
  color: #333;
  padding: 15px 40px;
  font-size: 18px;
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
}

.logo {
  font-weight: bold;
  font-size: 28px;
  color: #4f46e5; /* 감성 보라 */
  text-decoration: none;
  transition: color 0.3s;
}

.logo:hover {
  color:rgb(227, 41, 41);
}

.navbar-right {
  display: flex;
  gap: 30px;
}

.nav-item {
  color: #333;
  text-decoration: none;
  font-weight: 700;
  padding: 8px 16px;
  border-radius: 10px;
  transition: background 0.3s, color 0.3s;
}

.nav-item:hover {
  background: #e0e7ff;
  color: #4f46e5;
}
</style>

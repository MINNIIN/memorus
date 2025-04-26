<template>
  <div class="home">
  <section id="memories">
    <div class="map-container">
    <div class="intro-text">
      <h1>사랑하는 사람들과 함께한 순간을 기록하세요.</h1>
      <h3>MemorUS, 당신의 특별한 순간을 기억합니다.</h3>

      <div class="third-text">
        <h2 class="third-text-main">
        지도를 눌러 당신만의 추억을 남겨보세요
        <span class="arrow">≫</span>
        </h2>
      </div>
    </div>
      <svg
        viewBox="0 0 800 1000"
        class="korea-map"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          v-for="region in regions"
          :key="region.id"
          :d="region.path"
          :class="['region', { hovered: hoveredRegion === region.id }]"
          @mouseenter="handleMouseEnter($event, region.id)"
          @mouseleave="hoveredRegion = null"
          @click="handleRegionClick(region.name)"
        />
      </svg>
    </div>
    </section>

    <section id="ourstory">
    <div class="ourstory-section">
      <p style="color: white; padding: 20px;">Our Story Section.</p>
    </div>
    </section>

    <section id="coming">
      <!-- MOMENTS 콘텐츠 -->
    </section>

  </div>
</template>

<script>
import regions from '@/assets/regions';

export default {
  name: 'HomeView',
  data() {
    return {
      hoveredRegion: null,
      regions,
    };
  },
  methods: {
    handleRegionClick(name) {
      alert(`${name} 지역을 클릭했습니다!`);
    },
    handleMouseEnter(event, regionId) {
      this.hoveredRegion = regionId;
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.home {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  min-height: 100vh; /* min-height로 변경! */
}

.map-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 92vh;
}

.korea-map {
  width: 50%;
  height: auto;
  cursor: pointer;
  display: block;
  margin-left: 20px;
}

.ourstory-section {
  background: #5d5d5d;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.region {
  fill: #d0e6ff;
  stroke: #888;
  transition: transform 0.3s ease, fill 0.3s ease, filter 0.3s ease;
  transform-box: fill-box;
  transform-origin: center;
}

.region:hover,
.region.hovered {
  fill: #3399ff;
  transform: scale(1.05);
  filter: drop-shadow(0 0 6px rgba(0, 0, 0, 0.3));
}
.intro-text {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  
  padding-left: 50px;
  animation: fadeIn 1.5s ease;
}

.intro-text h1 {
  font-size: 36px;
  color: #333;
  margin-bottom: 15px;
  line-height: 1.3;
  font-weight: bold;
}

.intro-text h3 {
  font-size: 22px;
  color: #3399ff;
  margin-bottom: 10px;
  font-weight: 500;
}

.intro-text h2 {
  font-size: 20px;
  color: #666;
  font-weight: 400;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
.third-text {
  flex-direction: row;
}

.arrow {
  display: inline-block;
  margin-left: 10px;
  animation: arrowMove 1s ease-in-out infinite alternate;
  font-size: 20px;
  color: #666;
}

/* 화살표 애니메이션 */
@keyframes arrowMove {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(10px);
  }
}

</style>

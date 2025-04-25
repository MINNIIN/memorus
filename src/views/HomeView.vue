<template>
  <div class="home">
    <h1>MemorUS 🗺️</h1>
    <div class="map-container">
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

    // 현재 path를 svg의 마지막 자식으로 이동 (위로 올리기)
    const path = event.target;
    const parent = path.parentNode;
    parent.appendChild(path); // 해당 path를 맨 뒤로 이동시켜 가장 위로
  },
}
};
</script>

<style scoped>
.map-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 40px;
}

.korea-map {
  width: 800px;
  height: auto;
  cursor: pointer;
  display: block;
  margin: 0 auto;
  transform: translateX(170px);
}

.region {
  fill: #d0e6ff;
  stroke: #888;
  transition: all 0.5s ease;
}

.region:hover,
.region.hovered {
  fill: #3399ff;
  transform: scale(1.02);
  filter: drop-shadow(0 0 6px rgba(0, 0, 0, 0.3));
}
</style>

<template>
  <div id="main-view">
    <!-- 无人机部分 -->
    <div id="drones">
      <h3>无人机</h3>
      <div class="drone" v-for="drone in drones" :key="drone.id">
        <Drone
          :drone="drone"
          @detect="$emit('detect', drone.id)"
          @sendToGround="$emit('sendToGround', drone.id)"
        />
      </div>
    </div>
    
    <!-- 地面站部分 -->
    <GroundStation class="ground-station" :receivedImages="groundStation.receivedImages" />
  </div>
</template>

<script>
import Drone from "./Drone.vue";
import GroundStation from "./GroundStation.vue";

export default {
  name: "MainView",
  components: { Drone, GroundStation },
  props: {
    drones: Array,
    groundStation: Object,
  },
};
</script>

<style>
/* 主容器：上下布局 */
#main-view {
  display: flex;
  flex-direction: column; /* 改为上下排列 */
  height: 100vh; /* 占据整个视口高度 */
}

/* 无人机部分：横向布局 */
#drones {
  display: flex;
  flex-direction: column; /* 保证标题和无人机部分是上下排列 */
  align-items: center; /* 水平居中标题 */
  flex: 1; /* 让无人机部分占据剩余空间 */
}

#drones h3 {
  margin-bottom: 20px;
}

.drone {
  display: flex;
  flex-direction: row; /* 无人机横向排列 */
  justify-content: center; /* 水平居中 */
  gap: 20px; /* 无人机之间的间距 */
}

/* 地面站部分 */
.ground-station {
  flex: 0; /* 地面站占据最小高度 */
  margin-top: 20px; /* 与无人机部分的间距 */
}
</style>
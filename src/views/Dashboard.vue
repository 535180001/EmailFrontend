<template>
  <div class="dashboard">
    <transition name="fade">
      <sidebar v-if="$store.state.sided" class="sidebar"></sidebar>
    </transition>
    <div :class="'content-container '+sidedclass">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import sidebar from "@/components/Sidebar"
export default {
  name: "Dashboard",
  components: {
    sidebar,
  },
  computed: {
    sidedclass() {
      if(this.$store.state.sided){
        return "sided";
      }
      return "";
    }
  },
}
</script>

<style scoped lang=scss>

$animation-duration: .5s;
.dashboard{
  display: flex;
}

.content-container{
  display: flex;
  flex-direction: column;
  width: 100%;
  transition: all $animation-duration;
}
.sided{
  transform: translateX(250px);
  width: calc(100% - 250px);
}

.fade-enter-active, .fade-leave-active {
  transition: transform $animation-duration;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  transform: translateX(-250px);
}
</style>
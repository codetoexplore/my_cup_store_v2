<template>
  <v-container fluid fill-height class="home-hero">
    <v-layout justify-center align-center column pa-5>
      <div class="main-box">
        <home-pay> </home-pay>
      </div>
    </v-layout>
  </v-container>
</template>

<script>
import HomeLink from "@/components/HomeLink";
import HomeAdr from "@/components/HomeAdr";
import HomePay from "@/components/HomePay";
export default {
  components: {
    HomeLink,
    HomeAdr,
    HomePay
  }
};
</script>

<style scoped>
.main-box {
  border-style: solid;
  border-color: brown;
}
</style>

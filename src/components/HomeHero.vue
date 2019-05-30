<template>
  <v-container fluid fill-height class="home-hero">
    <v-layout justify-center align-center column pa-5>
      <div class="main-box">
        <home-adr> </home-adr>
      </div>
    </v-layout>
  </v-container>
</template>

<script>
import HomeLink from "@/components/HomeLink";
import HomeAdr from "@/components/HomeAdr";
export default {
  components: {
    HomeLink,
    HomeAdr
  }
};
</script>

<style scoped>
.main-box {
  border-style: solid;
  border-color: brown;
}
</style>

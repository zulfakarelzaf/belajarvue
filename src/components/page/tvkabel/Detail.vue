<template>
  <v-container fluid grid-list-md>
    <v-layout row wrap>
      <v-flex xs12 sm12 md8 lg8 class="mb-4">
        <TvKabelStat/>
      </v-flex>
      <v-flex xs12 sm12 md4 lg4 class="mb-4">
        <v-flex xs12 class="mb-4">
          <StatCard v-bind:obj="dusun" :count="obj.dusunCount"/>
        </v-flex>
        <v-flex xs12 class="mb-4">
          <StatCard v-bind:obj="customer" :count="obj.customerCount"/>
        </v-flex>
        <v-flex xs12 class="mb-4">
          <StatCard v-bind:obj="worker" :count="obj.workerCount"/>
        </v-flex>
        <v-flex xs12 class="mb-4">
          <StatCard v-bind:obj="channel" :count="obj.channelCount"/>
        </v-flex>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import StatCard from "@/components/stats/StatCard";
import TvKabelStat from "@/components/stats/TvKabelStat";
export default {
  components: {
    StatCard,
    TvKabelStat
  },
  data: () => ({
    obj: {},
    dusun: {
      title: "Dusun",
      icon: "location_city",
      color: "yellow darken-3"
    },
    customer: {
      title: "Customer",
      icon: "group",
      color: "green darken-3"
    },
    worker: {
      title: "Worker",
      icon: "supervised_user_circle",
      color: "cyan darken-3"
    },
    channel: {
      title: "Channel",
      icon: "storage",
      color: "red darken-3"
    }
  }),
  mounted() {
    console.log("mounted");
    this.obj = this.$store.state.viewedTvKabel;
    console.log(this.obj.name);
  },
  created() {
    console.log("created");
  }
};
</script>

<template>
  <div>
    <div>野球チーム一覧</div>
    <div v-for="team of teams" :key="team.id">
      <router-link :to="'/teamDetail' + team.id">{{
        team.teamName
      }}</router-link>
    </div>
  </div>
</template>

<script lang="ts">
import { Team } from "@/type/team";
import { Component, Vue } from "vue-property-decorator";
@Component
export default class XXXComponent extends Vue {
  get teams(): Array<Team> {
    return this.$store.getters.getTeams;
  }
}
</script>

<style scoped></style>

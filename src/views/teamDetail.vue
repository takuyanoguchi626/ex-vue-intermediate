<template>
  <div id="context">
    <div>
      <strong> 球団名<br /> </strong>
      {{ team.teamName }}
    </div>
    <div>
      <strong> 本拠地<br /> </strong>
      {{ team.headquarters }}
    </div>
    <div>
      <strong> 発足日<br /> </strong>
      {{ inauguration }}
    </div>
    <div>
      <strong> 歴史<br /> </strong>
      <pre
        >{{ team.history }}
  </pre
      >
    </div>
    <div>
      <button @click="back">戻る</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Team } from "@/type/team";
import { Component, Vue } from "vue-property-decorator";
import { format } from "date-fns";
@Component
export default class XXXComponent extends Vue {
  get teams(): Array<Team> {
    // const teamId = this.$route.params.id;
    // const teams = this.$store.getters.getTeams;
    return this.$store.getters.getTeams;
  }

  get team(): Team {
    const teamID = Number(this.$route.params.id);
    return this.teams.filter((team) => team.id === teamID)[0];
  }

  get inauguration(): string {
    return format(this.team.inauguration, "yyyy年MM月dd日");
  }

  back(): void {
    this.$router.push("/Ex01");
  }
}
</script>

<style scoped>
#context {
  text-align: left;
}
</style>

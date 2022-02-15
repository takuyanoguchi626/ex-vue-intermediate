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
      {{ team.getInauguration }}
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
@Component
export default class XXXComponent extends Vue {
  private team = new Team(0, "", "", new Date(), "");

  /**
   * Ex01.vueでクリックされたチームをストアから取得.
   *
   */
  async created(): Promise<void> {
    const teamID = Number(this.$route.params.id);
    this.team = this.$store.getters.getTeamById(teamID);
  }

  /**
   * Ex01.vueに戻るボタン.
   *
   */
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

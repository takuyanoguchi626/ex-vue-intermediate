<template>
  <div>
    <!-- start div -->
    <div>
      ホテル検索<br />
      <input type="number" v-model="price" />円以下<br />
      <button type="button" @click="setHotelsByPrice">検索</button>
    </div>
    <div>
      <table v-for="hotel of hotels" :key="hotel.id">
        <tr>
          <td>ホテル名</td>
          <td>{{ hotel.hotelName }}</td>
        </tr>
        <tr>
          <td>最寄駅</td>
          <td>{{ hotel.nearestStation }}</td>
        </tr>
        <tr>
          <td>価格</td>
          <td>{{ hotel.price }}</td>
        </tr>
      </table>
    </div>
    <!-- end div -->
  </div>
</template>

<script lang="ts">
import { Hotel } from "@/type/hotel";
import { Component, Vue } from "vue-property-decorator";
@Component
export default class XXXComponent extends Vue {
  //入力する金額
  private price = "";
  //ホテル一覧
  private hotels = Array<Hotel>();

  /**
   * 金額で絞り込んだホテル一覧を取得.
   *
   */
  setHotelsByPrice(): void {
    if (this.price === "") {
      this.hotels = this.$store.getters.getHotelByPrice(999999999);
    } else {
      this.hotels = this.$store.getters.getHotelByPrice(this.price);
    }
  }
}
</script>

<style scoped>
table {
  border: solid red;
}
</style>

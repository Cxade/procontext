<template>
  <div class="home center">
    <div class="home__box">
      <ItemComp
        v-for="(item, key, index) in allLists"
        :key="index"
        :list="item"
        :arrayName="'List ' + (index + 1)"
      />
    </div>
    <div class="home__box">
      <div class="list__right">
        <ItemSquareComp
          v-for="(item, key, index) in allLists"
          :key="index"
          :list="item"
          :arrayName="'List ' + (index + 1)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ItemComp from "@/components/ItemComp.vue";
import ItemSquareComp from "@/components/ItemSquareComp.vue";

export default {
  name: "MainPage",
  props: {},
  components: {
    ItemComp,
    ItemSquareComp,
  },
  data() {
    return {
      allLists: {
        list_1: [
          { name: "item 1", value: 10, color: "#FF0000", isChecked: false },
          { name: "item 2", value: 16, color: "#FFFF00", isChecked: false },
          { name: "item 3", value: 40, color: "#008000", isChecked: false },
          { name: "item 4", value: 0, color: "#0000FF", isChecked: false },
        ],
        list_2: [
          { name: "item 1", value: 4, color: "#FF00FF", isChecked: false },
          { name: "item 2", value: 10, color: "#000080", isChecked: false },
          { name: "item 3", value: 22, color: "#D2691E", isChecked: false },
          { name: "item 4", value: 9, color: "#00FF00", isChecked: false },
        ],
        list_3: [
          { name: "item 1", value: 4, color: "#FF00FF", isChecked: false },
          { name: "item 2", value: 10, color: "#000080", isChecked: false },
          { name: "item 3", value: 22, color: "#D2691E", isChecked: false },
          { name: "item 4", value: 9, color: "#00FF00", isChecked: false },
          { name: "item 5", value: 3, color: "#0000FF", isChecked: false },
          { name: "item 6", value: 15, color: "#FF0000", isChecked: false },
        ],
        list_4: [
          { name: "item 1", value: 4, color: "#FF00FF", isChecked: false },
          { name: "item 2", value: 10, color: "#000080", isChecked: false },
          { name: "item 3", value: 22, color: "#D2691E", isChecked: false },
          { name: "item 4", value: 9, color: "#00FF00", isChecked: false },
          { name: "item 5", value: 10, color: "#FFFF00", isChecked: false },
        ],
        list_5: [
          { name: "item 1", value: 4, color: "#FF00FF", isChecked: false },
          { name: "item 2", value: 10, color: "#000080", isChecked: false },
          { name: "item 3", value: 22, color: "#D2691E", isChecked: false },
          { name: "item 4", value: 24, color: "#00FF00", isChecked: false },
          { name: "item 5", value: 12, color: "#FFFF00", isChecked: false },
          { name: "item 6", value: 4, color: "#FF0000", isChecked: false },
          { name: "item 7", value: 8, color: "#800000", isChecked: false },
        ],
      },
    };
  },
};
</script>

<style scoped lang="scss">
.home {
  display: flex;
  justify-content: space-between;
  margin-top: 200px;
  &__box {
    border: 1px solid black;
    padding: 30px;
    position: relative;
    width: 45%;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
}

.list__right {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>

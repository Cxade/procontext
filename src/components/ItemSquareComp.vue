<template>
  <div class="main_box">
    <div class="head">
      <p>{{ arrayName }}</p>
      <button class="mix_btn" @click="changeSortedFlag()">{{ btnText }}</button>
    </div>

    <div class="square_main" v-if="isSorted">
      <div v-for="(item, index) in list" :key="index">
        <div class="square_box" v-if="item.isChecked">
          <div
            class="square"
            @click="deleteSquare(item.name)"
            v-for="n in item.value"
            :key="n"
            :style="{ backgroundColor: item.color }"
          ></div>
        </div>
      </div>
    </div>
    <div class="square_box" v-else>
      <div v-for="(item, index) in shuffledList" :key="index">
        <div
          @click="
            ($event) => {
              removeElement($event);
              deleteSquare(item.name);
            }
          "
          class="square"
          :style="{ backgroundColor: item.color }"
        ></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ItemSquareComp",
  props: { list: Array, arrayName: String },
  data() {
    return {
      listCopy: [],
      squares: [],
      isSorted: true,
    };
  },
  methods: {
    shuffleSquares() {
      this.squares = [];
      this.list.forEach((item) => {
        for (let i = 0; i < item.value; i++) {
          if (item.isChecked) {
            this.squares.push({ name: item.name, color: item.color });
          }
        }
      });
    },

    changeSortedFlag() {
      this.shuffleSquares();
      this.isSorted = !this.isSorted;
    },

    deleteSquare(name) {
      const index = this.listCopy.findIndex((item) => item.name === name);
      if (index !== -1) {
        this.listCopy[index].value -= 1;
      }
    },

    removeElement(event) {
      event.target.remove();
    },
  },
  computed: {
    shuffledList() {
      return this.squares.slice().sort(() => Math.random() - 0.5);
    },
    btnText() {
      return this.isSorted ? "Перемешать" : "Сортировать";
    },
  },
  mounted() {
    this.listCopy = [...this.list];
  },

  created() {
    this.shuffleSquares();
  },
};
</script>

<style lang="scss">
.main_box {
  border: 1px solid black;
  padding: 10px;
}
.head {
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
  align-items: center;
}
.square {
  width: 10px;
  height: 10px;
  margin: 2px;

  &_main {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  &_box {
    display: flex;
    flex-wrap: wrap;
  }
}

.mix_btn {
  right: 10px;
  top: 10px;
  padding: 5px;
  color: white;
  background-color: rgb(50, 177, 245);
  border-radius: 10px;
  transition: background-color 0.3s;
  cursor: pointer;
}
.mix_btn:hover {
  background-color: rgb(121, 196, 236);
}
</style>

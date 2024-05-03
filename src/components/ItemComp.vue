<template>
  <div class="title__box">
    {{ isShow ? "▼" : "►" }}
    <CustomCheckbox @input="handleInput" :value="checkboxValue" />
    <p @click="toggleShow">
      {{ arrayName }}
    </p>
  </div>
  <div v-show="isShow" class="list">
    <div v-for="(item, index) in listCopy" :key="index">
      <div class="list__box">
        <div>
          <input
            class="list__item-checkbox"
            type="checkbox"
            :id="item.name + arrayName"
            :name="item.name"
            v-model="item.isChecked"
          />
          <label :for="item.name + arrayName">{{ item.name }}</label>
        </div>
        <div class="flex">
          <input type="number" min="0" v-model="item.value" />
          <div>
            <input type="color" id="color" name="color" v-model="item.color" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CustomCheckbox from "@/components/CustomCheckbox.vue";
export default {
  name: "ItemComp",
  props: {
    list: Array,
    arrayName: String,
  },
  components: { CustomCheckbox },
  data() {
    return {
      listCopy: [],
      isShow: true,
    };
  },
  methods: {
    handleInput(isChecked) {
      if (isChecked === 0 || isChecked === 1) {
        this.listCopy.forEach((item) => {
          item.isChecked = true;
        });
      } else if (isChecked === 2) {
        this.listCopy.forEach((item) => {
          item.isChecked = false;
        });
      }
    },
    toggleShow() {
      this.isShow = !this.isShow;
    },
  },
  computed: {
    checkboxValue() {
      let checkedCount = this.listCopy.filter((item) => item.isChecked).length;

      if (checkedCount === 0) {
        return 0;
      } else if (checkedCount === this.listCopy.length) {
        return 2;
      } else {
        return 1;
      }
    },
  },
  mounted() {
    this.listCopy = [...this.list];
  },
};
</script>

<style scoped lang="scss">
.title__box {
  display: flex;
  align-items: center;
  gap: 10px;
}
.list {
  display: flex;
  flex-direction: column;

  &__box {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &__item-checkbox {
    margin-left: 56px;
  }
}
p {
  cursor: pointer;
  user-select: none;
}

label {
  cursor: pointer;
  user-select: none;
}

input {
  margin: 3px;
}

input[type="number"] {
  width: 30px;
  text-align: center;
}
input[type="color"] {
  width: 30px;
}
</style>

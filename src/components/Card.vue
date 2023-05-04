<template>
  <div class="itemContainer" v-for="item in items" :key="item.id">
    <div class="col1">
      <img
        class="checkboxItem"
        v-if="!item.selected"
        src="../assets/emptyCheckbox.svg"
        alt=""
        @click="checkBoxAction(item.id)"
      />
      <img
        class="checkboxItem"
        v-else
        src="../assets/filledCheckbox.svg"
        alt=""
        @click="checkBoxAction(item.id)"
      />
      <img class="pin" src="../assets/pin.svg" alt="" />
    </div>

    <div class="col2">
      <div class="row1">
        <span class="price">{{ item.price }}</span>
        <div class="type" v-if="item.type">
          <img
            style="margin-right: 10px"
            src="../assets/apartment.svg"
            alt=""
          />
          <div>{{ item.type.text }}</div>
        </div>
      </div>
      <div class="nameRow">
        <span class="name">{{ item.name }}</span>
        <span class="subname">{{ item.subname }}</span>
      </div>
      <div class="floorData">
        <div class="floorDataCol1">
          <span class="apartment">{{ item.apartment }}</span>
          <span class="apartment">{{ item.apartmentType }}</span>
        </div>
        <div class="vDivider"></div>
        <div class="floorDataCol2">
          <span class="size">{{ item.size }}</span>
          <span v-if="item.floor" class="floor">{{ item.floor }}</span>
        </div>
      </div>
      <div class="addressRow">
        <span class="address">{{ item.address }}</span>
      </div>
    </div>
    <div class="col3">
      <div class="status">
        <img style="margin-right: 10px" src="../assets/dot.svg" alt="" />
        <div>{{ item.status }}</div>
      </div>
      <img class="apartment" src="../assets/apartment.png" />
      <span class="addedDate">{{ item.addedDate }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  methods: {
    checkBoxAction(id) {
      const index = this.items.findIndex((e) => e.id == id);
      this.items[index].selected = !this.items[index].selected;
    },
  },
};
</script>

<style>
.itemContainer {
  position: relative;
  display: flex;
  background: #ffffff;
  /* table_gray */
  border: 1px solid #e5e5e5;
}
.col1 {
  position: relative;
  display: flex;
  width: 68px;
}
.col2 {
  margin: 25px 30px 25px 5px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.col3 {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}
.row1 {
  display: flex;
  flex-direction: row;
}
.type {
  display: flex;
  flex-direction: row;
  width: 100px;
  background: #ffffff;
  box-shadow: 0px 0px 2px rgba(94, 119, 157, 0.25);
  border-radius: 32px;
  justify-content: center;
}
.floorData {
  display: flex;
  align-items: center;
}
.vDivider {
  border-left: 1px solid #c4c4c4;
  margin-left: 15px;
  margin-right: 26px;
  min-height: 25px;
  max-height: 48px;
}
.price {
  margin-right: 8px;
  font-family: "PT Sans";
  font-style: normal;
  font-weight: 700;
  font-size: 15px;
  line-height: 20px;
  color: #ff0d29;
}
.checkboxItem {
  position: absolute;
  right: 25%;
  top: 50%;
}
.pin {
  position: absolute;
  right: 0;
  bottom: 55px;
}
.floorDataCol1 {
  display: flex;
  flex-direction: column;
}
.floorDataCol2 {
  display: flex;
  flex-direction: column;
}
.addedDate {
  position: absolute;
  bottom: 25px;
  right: 39px;
  font-family: "PT Sans";
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 20px;
  /* or 154% */
  text-align: right;

  /* dark_gray */
  color: #9b9b9b;
}
.status {
    display: flex;
    align-items: center;
  width: max-content;
  margin-top: 21px;
  margin-left: 0px;
  height: 30px;
  background: #ffe4e4;
  color: #DD4C5D;
}
.apartment {
  margin-right: 38px;
}

@media screen and (max-width: 600px) {
  .itemContainer {
    width: 502px;
    height: 238px;
  }
  .col1 {
    width: 67.75px;
  }
}
</style>

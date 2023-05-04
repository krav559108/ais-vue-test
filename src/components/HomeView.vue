<template>
  <div class="mainContainer">
    <div class="searchBar">
      <img class="searchIcon" src="../assets/search.svg" alt="" />
      <input
        class="searchInput"
        v-model="searchQuery"
        placeholder="Введите ЖК / корпус / № квартиры / № паркинга"
      />
    </div>

    <div class="filterArea">
      <img
        class="checkbox"
        v-if="!this.clickedCheckbox"
        src="../assets/emptyCheckbox.svg"
        alt=""
        @click="checkBoxAction"
      />
      <img
        class="checkbox"
        v-else
        src="../assets/filledCheckbox.svg"
        alt=""
        @click="checkBoxAction"
      />
      <span>Все</span>
      <div class="deleteButton">
        <span class="deleteText">Удалить</span>
        <img class="deleteIcon" src="../assets/trash.svg" alt="" />
      </div>
    </div>

    <card :items="filteredItems"></card>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: { Card },
  data() {
    return {
      items: [
        {
          selected: false,
          id: 1,
          name: "Чистое Небо, ",
          subname: "корпус 10, III кв. 2022 г.",
          price: "7 733 300 руб.",
          type: {
            enum: 1,
            text: "Квартира",
          },
          status: "Уступка от юр. лица",
          address:
            "Лен. область, Всеволожский район,д. Кудрово, ул. Столичная, д. 5, к. 1",
          apartment: "кв. 62",
          apartmentType: "1 комн. кв.",
          size: "234.38 м²",
          floor: "7 этаж",
          picture: "",
          addedDate: "21/11/2020",
        },
      ],
      searchQuery: "",
      clickedCheckbox: false,
    };
  },
  methods: {
    checkBoxAction() {
      this.clickedCheckbox = !this.clickedCheckbox;
    },
  },
  computed: {
    filteredItems() {
      if (!this.searchQuery) {
        return this.items;
      }
      return this.items.filter((item) =>
        item.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
};
</script>

<style>
.mainContainer {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0 auto;
}
.searchBar {
  display: flex;
  align-items: center;
  border: 1px solid #c4c4c4;
  font-family: "PT Sans";
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 18px;

  /* dark_gray */
  color: #9b9b9b;
}

.searchIcon {
  display: flex;
  align-items: center;
  justify-content: center;
}

.searchInput {
  flex: 1;
  border: none;
  background-color: transparent;
}

.checkbox {
  margin-right: 10px;
}
.filterArea {
  display: flex;
  align-items: center;
}
.deleteButton {
  display: flex;
  align-items: center;
  width: 101px;
  height: 38px;
  background: #e5e5e5;
  justify-content: center;
  margin-left: 13px;
}
.deleteIcon {
  width: 12px;
  height: 14px;
  margin-left: 12px;
}

@media screen and (max-width: 600px) {
  .mainContainer {
    max-height: 1300px;
    margin: 35px 49px 112px 49px;
  }
  .searchBar {
    width: 93%;
    height: 38px;
    margin: 0 30px 0 0;
  }
  .searchIcon {
    margin-left: 7.36px;
    margin-right: 13.88px;
  }
  .filterArea {
    margin: 25px auto 25px 0px;
  }
}
</style>

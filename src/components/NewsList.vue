<template>
  <div class="news-list">
    <button v-if="showButton" class="news-list__button" @click="getNews">
      Завантажити новини
    </button>
    <ul v-if="!loading && articles" class="news-list__list">
      <li v-for="article in articles" :key="article.id" class="news-list__item">
        <div class="news-image">
          <img :src="article.imageUrl" alt="image" />
        </div>
        <div class="news-data">
          <div class="news-data__time">
            <span class="time">
              {{ formattedDate(article.createdAt) }}
            </span>
            <span class="comment">
              <img src="../assets/img/icon-messenger.svg" alt="vector" />
              {{ article.commentsCount }}
            </span>
          </div>
          <h3 class="news-data__title">{{ article.title }}</h3>
          <p class="news-data__text">{{ article.content }}</p>
        </div>
      </li>
    </ul>
    <p v-if="loading" class="loading">Loading...</p>
    <button
      class="news-list__button"
      v-if="showMoreButton"
      @click="getMoreNews"
      :disabled="loading"
    >
      Більше новин
    </button>
  </div>
</template>

<script>
import axios from "axios";
import moment from "moment";

export default {
  name: "NewsList",
  data() {
    return {
      articles: [],
      page: 1,
      showButton: true,
      showMoreButton: false,
      loading: false,
    };
  },
  methods: {
    async getNews() {
      try {
        this.loading = true;
        const response = await axios.get(
          "https://63ee0ec0388920150dd83e3c.mockapi.io/news",
          {
            params: {
              page: this.page,
              limit: 5,
            },
          }
        );
        this.showButton = false;
        this.loading = false;
        this.articles = response.data;
        this.page += 1;
        this.showMoreButton = true;
      } catch (error) {
        console.error(error);
        alert("Failed to get news. Please try again later.");
      } finally {
        this.loading = false;
      }
    },
    async getMoreNews() {
      try {
        const response = await axios.get(
          "https://63ee0ec0388920150dd83e3c.mockapi.io/news",
          {
            params: {
              page: this.page,
              limit: 5,
            },
          }
        );
        if (response.data.length > 0) {
          this.articles = [...this.articles, ...response.data];
          this.page += 1;
        } else {
          this.showMoreButton = false;
        }
      } catch (error) {
        console.error(error);
        alert("Failed to get more news. Please try again later.");
      }
    },
    formattedDate(date) {
      const dateObj = new Date(date);
      const formattedDate = moment(dateObj).format("hh:mm - MMMM DD, YYYY");
      return formattedDate;
    },
  },
};
</script>

<style scoped lang="scss">
$mainBlackColor: rgba(0, 0, 0, 0.8);
$mainBlackLightColor: rgba(0, 0, 0, 0.54);
$mainBlueColor: #4b99f5;

.news-list {
  text-align: center;
  &__button {
    font-weight: 700;
    font-size: 16px;
    line-height: 19px;
    padding: 10px 57px;
    border: 2px solid $mainBlueColor;
    border-radius: 24px;
    text-align: center;
    margin: 40px 0 15px;
  }
  &__item {
    display: flex;
    padding: 24px 0 23px;
    border-bottom: 1px dashed rgba(0, 0, 0, 0.15);
    gap: 24px;
  }
}
.news-image {
  max-width: 200px;
  max-height: 125px;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  border-radius: 12px;
}
.news-image img {
  max-width: 100%;
}
.news-data {
  text-align: start;
  &__time {
    line-height: 20px;
    color: $mainBlackLightColor;
    display: flex;
    gap: 24px;
  }
  &__title {
    font-family: "Roboto Slab";
    font-weight: 500;
    font-size: 20px;
    line-height: 26px;
    color: $mainBlackColor;
    padding: 6px 0 8px;
  }
  &__text {
    color: $mainBlackLightColor;
    line-height: 20px;
  }
}
.comment {
  display: flex;
  align-items: center;
  gap: 4px;
}
.loading {
  font-weight: 500;
  font-size: 20px;
  padding-top: 20px;
}
@media screen and (max-width: 630px) {
  .news-list {
    padding-bottom: 17px;
    border-bottom: 1px dashed rgba(0, 0, 0, 0.15);
    &__item {
      flex-direction: column;
      align-items: center;
      gap: 12px;
      border-bottom: none;
      padding: 10px 0;
    }
    &__list {
      margin-top: 36px;
    }
  }
  .news-list__button {
    margin: 27px 0 15px;
  }
  .news-image {
    max-width: 336px;
    max-height: 190px;
  }
  .news-data__time {
    justify-content: space-between;
  }
}
@media screen and (max-width: 450px) {
  .news-data {
    width: 100%;
  }
  .news-data__title {
    padding: 6px 0 0px;
  }
  .news-data__text {
    display: none;
  }
}
</style>

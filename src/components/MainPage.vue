<template>
  <div class="container">
    <main class="main-page">
      <div class="flex-container">
        <section class="main-block">
          <div class="user-info">
            <div class="user-info__container">
              <img src="../assets/img/user.svg" alt="user`s photo" />
              <div>
                <div class="user-info__block">
                  <div class="following-data">
                    <div class="following-data__item">
                      <img src="../assets/img/icon-page.svg" alt="vector" />
                      <span>345</span>
                    </div>
                    <div class="following-data__item">
                      <img src="../assets/img/icon-user.svg" alt="vector" />
                      <span>4 567</span>
                    </div>
                    <div class="following-data__item">
                      <img src="../assets/img/icon-eye.svg" alt="vector" />
                      <span>12 809 678</span>
                    </div>
                  </div>
                  <h2 class="following-data__title">Костянтин Заруцький</h2>
                </div>
                <div class="user-data">
                  <p class="user-data__text">
                    Костантин Заруцький — справжнє ім’я популярного автоблогера,
                    який публікується в мережі під ніком AcademeG. Його відео
                    про перетворення старих авто дивляться міліони підписників.
                    Сам він називає свою роботу автокритикою
                  </p>
                </div>
              </div>
            </div>
          </div>
          <NewsList />
        </section>
        <section class="additional-block">
          <div class="flex-block">
            <div class="advertising-new-block">
              <img src="../assets/img/img-glovo.svg" alt="advertising" />
            </div>
            <div class="program-block">
              <h3 class="program-block__title">Програма ТВ</h3>
              <div class="program-block__content">
                <ul class="program-block__list">
                  <li class="program-block__item">
                    <span class="time">09:25</span>
                    <span class="name">т/с “Мене звуть Міша”</span>
                    <span class="sourse">Інтер</span>
                  </li>
                  <li class="program-block__item">
                    <span class="time">09:25</span>
                    <span class="name">х/ф “Безславные убл...</span>
                    <span class="sourse">1+1</span>
                  </li>
                  <li class="program-block__item">
                    <span class="time">09:25</span>
                    <span class="name">Фінал Ліги Чемпіо...</span>
                    <span class="sourse">Інтер</span>
                  </li>
                  <li class="program-block__item">
                    <span class="time">09:25</span>
                    <span class="name">т/с “Мене звуть Міша”</span>
                    <span class="sourse">ICTV</span>
                  </li>
                  <li class="program-block__item">
                    <span class="time">09:25</span>
                    <span class="name">Шоу “Голос Діти”</span>
                    <span class="sourse">Інтер</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </section>
      </div>
    </main>
  </div>
</template>

<script>
import NewsList from "./NewsList.vue";

export default {
  name: "MainPage",
  components: {
    NewsList,
  },
};
</script>

<style scoped lang="scss">
$mainBlackColor: rgba(0, 0, 0, 0.8);
$mainBlueColor: #4b99f5;
$mainGreyColor: #f6f6f6;
$whiteColor: #ffffff;
$blackColor: #000000;

$maxWidthContainer: 1250px;
$fontSize: 14px;
$fontFamily: "Roboto", sans-serif;
$minWidth: 320px;
.main-page {
  padding: 40px 0;
}
.flex-container {
  display: flex;
  gap: 28px;
}
.main-block {
  flex: 1 0 0;
}
//-----------------
.user-info {
  &__container {
    display: flex;
    gap: 24px;
    align-items: start;
    padding: 8px 0 40px;
    border-bottom: 1px dashed rgba(0, 0, 0, 0.15);
  }
  &__block {
    display: flex;
    flex-direction: column;
  }
}
.following-data {
  display: flex;
  align-items: center;
  gap: 32px;
  &__item {
    display: flex;
    align-items: center;
    gap: 6px;
  }
  &__title {
    font-weight: 700;
    font-size: 32px;
    line-height: 36px;
    padding: 12px 0 16px;
  }
}
.user-data {
  color: $mainBlackColor;
  &__text {
    font-size: 14px;
    line-height: 20px;
    max-width: 735px;
  }
}
//-----------------
.additional-block img {
  border-radius: 8px;
}
.flex-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2.5rem;
}
.program-block {
  background-color: $mainGreyColor;
  border-radius: 0.75rem;
  &__title {
    padding: 0.75rem 1rem;
    font-family: "Roboto Slab";
    font-style: normal;
    font-weight: 700;
    font-size: 20px;
    line-height: 24px;
    border-bottom: 1px dashed rgba(0, 0, 0, 0.15);
  }
  &__content {
    padding: 16px 12px 11px 14px;
  }
  &__list {
    width: 250px;
  }
  &__item {
    display: flex;
    line-height: 20px;
    margin-bottom: 12px;
    .time {
      color: rgba(0, 0, 0, 0.4);
      padding-right: 8px;
    }
    .name {
      flex: 1 0 0;
    }
    .sourse {
      color: $mainBlueColor;
    }
  }
}
@media screen and (max-width: 991px) {
  .flex-container {
    flex-direction: column;
  }
  .flex-block {
    gap: 2rem;
  }
  .advertising-new-block {
    max-width: 336px;
    width: 100%;
  }
  .additional-block img {
    width: 100%;
  }
  .program-block {
    max-width: 336px;
    width: 100%;
    &__list {
      width: 100%;
    }
  }
}
@media screen and (max-width: 630px) {
  .flex-container {
    gap: 32px;
  }
  .main-page {
    padding: 24px 0 100px;
  }
  .user-info__container {
    flex-direction: column;
    align-items: center;
    gap: 10px;
  }
  .user-info__block {
    flex-direction: column-reverse;
    text-align: center;
  }
  .following-data {
    padding-bottom: 28px;
    justify-content: center;
  }
  .following-data__title {
    padding: 0 0 12px;
    font-size: 28px;
  }
  .user-data {
    text-align: center;
  }
}
</style>

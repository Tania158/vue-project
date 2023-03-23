<template>
  <div class="header">
    <div :class="showMobileMenu ? 'overlay' : 'overlay-none'"></div>
    <div class="header-nav">
      <div class="container">
        <div class="flex-block">
          <div class="btn-burger" @click="showMenu()">
            <div
              class="burger burger-menu"
              :class="showMobileMenu ? 'open' : ''"
            >
              <div class="icon"></div>
            </div>
          </div>
          <div class="logo">
            <a href="#">
              <img src="../assets/img/logo.svg" alt="logo" />
            </a>
          </div>
          <div class="nav-menu" :class="showMobileMenu ? 'open-menu' : ''">
            <ul class="nav-menu__list">
              <li class="nav-menu__item"><a href="#">Новини</a></li>
              <li class="nav-menu__item"><a href="#">Спорт</a></li>
              <li class="nav-menu__item"><a href="#">Фінанси</a></li>
            </ul>
          </div>
          <div class="nav-lang">
            <ul class="nav-lang__list">
              <li class="nav-lang__link">
                <a class="active" href="#">ua</a>
              </li>
              <li class="nav-lang__link">
                <a href="#">ru</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Header",
  data() {
    return {
      showMobileMenu: false,
    };
  },
  methods: {
    showMenu() {
      this.showMobileMenu = !this.showMobileMenu;
    },
  },
};
</script>

<style lang="scss" scoped>
$header-height: 3rem;
$header-color: #343434;
$mainBlueColor: #4b99f5;
.header {
  display: block;
}
.header-nav {
  background-color: $header-color;
  height: $header-height;
  width: 100%;
  position: relative;
}
.flex-block {
  height: 100%;
  display: flex;
  align-items: center;
  gap: 1.75rem;
}
.btn-burger {
  cursor: pointer;
  display: block;
}
.burger-menu {
  width: 22px;
  height: 18px;
  position: relative;
  display: inline-block;
  z-index: 1000;
  transition-duration: 1s;
  cursor: pointer;
}
.icon {
  height: 1.8px;
  width: 21px;
  top: 10px;
  background-color: #fff;
  position: absolute;
  -webkit-transition-duration: 0.5s; /* Safari, Chrome */
  -moz-transition-duration: 0.5s; /* Firefox */
  -o-transition-duration: 0.5s; /* Opera */
  transition-duration: 0.5s;
}
.icon:before {
  left: 0;
  position: absolute;
  top: -7.5px;
  height: 1.8px;
  width: 21px;
  background-color: #fff;
  content: "";
  -webkit-transition-duration: 0.5s; /* Safari, Chrome */
  -o-transition-duration: 0.5s; /* Opera */
  -moz-transition-duration: 0.5s; /* Firefox */
  transition-duration: 0.5s;
}
.icon:after {
  left: 0;
  position: absolute;
  top: 7.5px;
  height: 1.8px;
  width: 21px;
  background-color: #fff;
  content: "";
  -webkit-transition-duration: 0.5s; /* Safari, Chrome */
  -o-transition-duration: 0.5s; /* Opera */
  -moz-transition-duration: 0.5s; /* Firefox */
  transition-duration: 0.5s;
}
.burger .icon {
  -webkit-transition-duration: 0.5s; /* Safari, Chrome */
  -o-transition-duration: 0.5s; /* Opera */
  -moz-transition-duration: 0.5s; /* Firefox */
  transition-duration: 0.5s;
  -webkit-transition-delay: 0.5s; /* Safari, Chrome */
  -o-transition-delay: 0.5s; /* Opera */
  -moz-transition-delay: 0.5s; /* Firefox */
  transition-delay: 0.5s;
}
.burger .icon:before,
.burger .icon:after {
  -webkit-transition: top 0.5s 0.5s, -webkit-transform 0.5s; /* Safari, Chrome */
  transition: top 0.5s 0.5s, -webkit-transform 0.5s;
  transition: transform 0.5s, top 0.5s 0.5s;
  transition: transform 0.5s, top 0.5s 0.5s, -webkit-transform 0.5s;
  -o-transition: transform 0.5s, top 0.5s 0.5s; /* Opera */
}
//-------------------------
.logo img {
  max-width: 91px;
  cursor: pointer;
}
//-------------------------
.nav-menu {
  margin: 0 1.75rem;
  color: $mainBlueColor;
  font-weight: 500;
  font-size: 12px;
  text-transform: uppercase;
  &__list {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    line-height: 14px;
  }
}
.nav-lang {
  flex: 1 0 0;
  color: rgba(255, 255, 255, 0.54);
  font-weight: 500;
  font-size: 12px;
  text-transform: uppercase;
  &__list {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    gap: 0.5rem;
    line-height: 14px;
  }
  .active {
    color: $mainBlueColor;
  }
}
.nav-content {
  display: flex;
  justify-content: space-between;
  padding: 10px 30px;
  align-items: center;
}

.nav-items {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 0;

  li {
    padding: 0 10px;
  }
}

// Mobile version - hidden hamburger menu
@media screen and (max-width: 768px) {
  .overlay {
    display: block;
    background: #403b3b;
    opacity: 0.5;
    -webkit-transition: opacity 0.8s; /* Safari, Chrome */
    -moz-transition: opacity 0.8s; /* Firefox */
    -o-transition: opacity 0.8s; /* Opera */
    transition: opacity 0.8s;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 90;
    width: 100vw;
    height: 100vh;
  }
  .overlay-none {
    opacity: 0;
  }
  .flex-block {
    gap: 1.5rem;
  }
  .burger.open .icon {
    -webkit-transition-duration: 0.1s; /* Safari, Chrome */
    -o-transition-duration: 0.1s; /* Opera */
    -moz-transition-duration: 0.1s; /* Firefox */
    transition-duration: 0.1s;
    -webkit-transition-delay: 0.5s; /* Safari, Chrome */
    -o-transition-delay: 0.5s; /* Opera */
    -moz-transition-delay: 0.5s; /* Firefox */
    transition-delay: 0.5s;
    background: transparent;
    background-color: #000;
    height: 3px;
  }
  .burger.open .icon:before,
  .burger.open .icon:after {
    -webkit-transition: top 0.5s, -webkit-transform 0.5s 0.5s; /* Safari, Chrome */
    transition: top 0.5s, -webkit-transform 0.5s 0.5s;
    transition: top 0.5s, transform 0.5s 0.5s;
    transition: top 0.5s, transform 0.5s 0.5s, -webkit-transform 0.5s 0.5s;
    -o-transition: top 0.5s, transform 0.5s 0.5s; /* Opera */
    top: 0px;
    background-color: #000;
    height: 3px;
  }
  .nav-menu {
    margin: 0;
    position: fixed;
    background: #fff;
    left: -100%;
    width: 80%;
    z-index: 999;
    top: 0;
    padding: 60px;
    min-height: 100vh;
    height: 100%;
    overflow-y: auto;
    &__list {
      flex-direction: column;
      gap: 2rem;
      line-height: 14px;
      font-size: 18px;
    }
  }
  .nav-menu {
    -webkit-transition: left 0.8s ease-in-out; /* Safari, Chrome */
    -o-transition: left 0.8s ease-in-out; /* Opera */
    -moz-transition: left 0.8s ease-in-out; /* Firefox */
    transition: left 0.8s ease-in-out;
  }
  .nav-menu.open-menu {
    left: 0;
    -webkit-transition: left 0.8s ease-in-out; /* Safari, Chrome */
    -o-transition: left 0.8s ease-in-out; /* Opera */
    -moz-transition: left 0.8s ease-in-out; /* Firefox */
    transition: left 0.8s ease-in-out;
  }

  .nav-content {
    flex-direction: column;
    z-index: 100;
    position: relative;
    transition: all 0.2s ease-in;
  }

  .nav-items {
    flex-direction: column;
  }
}
</style>

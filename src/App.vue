<template>
  <div id="app">
    <header class="header">
      <nav class="menu">
        <li class="menu__item">
          <a href="#" class="menu__link">About</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">Delivery</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">Payment</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">Contacts</a>
        </li>
      </nav>
      <div class="logo">
        <a href="#">
          <img src="./img/logo.svg" alt="img" />
        </a>
      </div>
      <nav class="menu menu--user">
        <li class="menu__item">
          <a href="#" class="menu__link">USD</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">My profile</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link js-bag">Bag ( 0 )</a>
        </li>
      </nav>
    </header>

    <div class="header__mobile">
      <nav class="menu__mobile">
        <a href class="side__closer">&times;</a>
        <h4 class="menu__mobile__title">Navigate</h4>
        <li class="menu__item">
          <a href="#" class="menu__link">About</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">Delivery</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">Payment</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">Contacts</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">USD</a>
        </li>
        <li class="menu__item">
          <a href="#" class="menu__link">My profile</a>
        </li>
      </nav>
      <div class="humburger">Menu</div>
      <div class="logo">
        <a href="#">
          <img src="./img/logo.svg" alt="img" />
        </a>
      </div>
      <nav class="menu menu--user">
        <li class="menu__item">
          <a href="#" class="menu__link js-bag">Bag ( 0 )</a>
        </li>
      </nav>
    </div>

    <section class="section">
      <div id="sync1" class="goods owl-carousel owl-theme">
        <div class="goods__item" v-for="good in goods" :key="good.id">
          <div class="goods__img">
            <img :src="imgPath+good.img" alt="img" />
          </div>
          <div class="goods__description">
            <h3 class="goods__title">{{good.name}}</h3>
            <h4 class="goods__city">{{good.color}}</h4>
            <h5 class="goods__price">{{good.cost}} $</h5>
            <p class="goods__text">{{good.description}}</p>

            <div class="goods__btn-block">
              <button
                @click="viewSize(good.size)"
                class="js-select_size goods__button goods__button--select-size"
                v-if="selectSiz"
              >Size {{selectSiz}}</button>

              <button
                @click="viewSize(good.size)"
                v-else
                class="js-select_size goods__button goods__button--select-size"
              >Select your size</button>

              <button
                @click="toBag(selectSiz, )"
                v-if="selectSiz"
                class="goods__button goods__button--add"
              >ADD TO BAG</button>

              <button
                v-else
                class="goods__button goods__button--add goods__button--disabled"
              >ADD TO BAG</button>
            </div>
          </div>
        </div>
      </div>

      <div id="sync2" class="goods goods--thumbnail owl-carousel owl-theme">
        <div class="goods__item" v-for="good in goods" :key="good.id">
          <div class="goods__img">
            <img :src="imgPath+good.img" alt="img" />
          </div>
        </div>
      </div>
    </section>

    <div class="sidebar-overlay"></div>
    <aside class="side side__size">
      <a href class="side__closer">&times;</a>
      <h5 class="side__title">SELECT YOUR SIZE</h5>
      <div class="size-guide">
        <div
          class="size-guide__item"
          @click="selectSize(siz)"
          v-for="siz in sizes"
          :key="siz.id"
        >{{siz}}</div>
        <!-- size-guide__item--active -->
        <p class="side__text">
          Concerns about sizes?
          <a href="#" class="side__link">View size guide</a>
        </p>
      </div>
    </aside>

    <aside class="side side__cart">
      <a href class="side__closer side__closer--invert">&times;</a>
      <h5 class="side__title side__title--invert">SHOPPING BAG</h5>
      <div class="cart">
        <div class="cart__item">
          <div class="cart__item__img">
            <img src="./img/shoes4.jpg" alt="img" />
          </div>
          <div class="cart__item__info">
            <h6 class="cart__item__title">Classic Nubuck</h6>
            <span class="cart__item__subinfo">Berghain</span>
          </div>
          <div class="cart__item__action">
            <h6 class="cart__item__price">238,35 $</h6>
            <a href="#" class="cart__item__remove">Remove</a>
          </div>
        </div>
        <p class="side__text side__text--invert">
          You have not items in your bag yet.
          <a
            href="#"
            class="side__link side__link--invert"
          >Add first</a>
        </p>
      </div>
    </aside>
  </div>
</template>

<script>
import json from "./js/goods.json";

export default {
  name: "app",
  data() {
    return {
      goods: json,
      imgPath: "src/img/",
      sizes: [],
      selectSiz: ""
    };
  },
  methods: {
    viewSize(size) {
      return (this.sizes = size);
    },
    selectSize(siz) {
      return (this.selectSiz = siz);
    },
    toBag(siz) {
      console.log(siz);
    }
  },
  watch: {},
  created: function() {}
};
</script>

<style lang="sass">

@import '../node_modules/owl.carousel/dist/assets/owl.carousel.min.css'
@import '../node_modules/owl.carousel/dist/assets/owl.theme.default.css'

@import "./src/sass/main.sass"
</style>

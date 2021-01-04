<template>
  <b-container fluid class="cont">
    <b-row class="sale-image">
      <b-col xs="12" md class="sale-cont">
        <b-carousel
          id="carousel-1"
          v-model="slide"
          :interval="4000"
          controls
          @sliding-start="onSlideStart"
          @sliding-end="onSlideEnd"
          class="w-100"
        >
          <b-carousel-slide v-for="(item, index) in logo" :key="index">
            <template #img>
              <img
                class="img-fluid sale-img-pos"
                :src="item"
                alt="image slot"
              />
              <span class="span"></span>
              <span class="sale-text">
                <p>Best offer</p>
                <h2 name="h2-sale" id="h2-sale" style="color:white">
                  Sale
                </h2>
                <span class="shop-now">Shop Now</span>
              </span>
            </template>
          </b-carousel-slide>
        </b-carousel>
      </b-col>
    </b-row>
    <h1
      style="margin-bottom:3%; text-align:center; text-transform:uppercase; text-decoration:underline"
    >
      Merchants
    </h1>
    <b-row class="row just" v-if="this.items.length >= 1">
      <b-card
        v-for="(item, index) in items"
        :key="index"
        title=""
        img-alt="Image"
        img-center
        tag="article"
        class="mb-5 card-img"
        align="center"
        bg-variant="dark"
        footer-tag="footer"
        footer-bg-variant="white"
        footer-border-variant="white"
      >
        <b-card-img
          :src="item.image"
          alt="Image"
          class="d-img"
          bottom
        ></b-card-img>
        <template #footer>
          <em>{{ item.name }}</em>
          <p>{{ item.text }}</p>
          <p style="font-size:11px">{{ item.category }}</p>
        </template>
      </b-card>
    </b-row>
    <b-row v-else>
      <h1>No Item Found</h1>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: 'WebPage',
  props: {
    items: Array,
    logo: Array,
    searchValue: String,
  },
  data: () => {
    return {
      slide: 0,
      sliding: null,
      colors: ['red', 'yellow', 'blue', 'purple', 'pink', 'gold', 'cyan'],
    };
  },
  methods: {
    onSlideStart() {
      this.sliding = true;
    },
    onSlideEnd() {
      this.sliding = false;
    },
    getColor() {
      let colorName = document.getElementsByName('h2-sale');
      colorName.forEach((k) => k.style.color);
      let currentFont = 0;
      return setInterval(() => {
        colorName.forEach(
          (k) =>
            (k.style.color = this.colors[currentFont++ % this.colors.length])
        );
      }, 500);
    },
  },
  mounted() {
    this.getColor();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.nav-color {
  color: red;
  background-color: blue;
}
#navtest {
  background-color: yellow;
}
.sale-image {
  background: linear-gradient(#0a1f5a, transparent),
    linear-gradient(to top left, #1538e0, transparent),
    linear-gradient(to top right, #dcdc1b, transparent);
  background-blend-mode: screen;
  margin: 5% 0;
}
.card-img {
  width: 20rem;
}
footer em {
  font-size: 1.2rem;
  font-weight: 700;
  color: #176f2b;
  text-transform: uppercase;
}
footer p {
  font-size: 14px;
}
.sale-text {
  position: relative;
  text-align: center;
  border: solid 8px;
  right: 1%;
  padding: 11px 3% 7% 6%;
}
.sale-text h2 {
  font-size: 4.5rem;
  font-family: unset;
  font-weight: 600;
  font-style: italic;
  text-transform: uppercase;
  color: #f5f5f5;
  text-shadow: 2px 2px 1px black;
  margin-bottom: 2rem;
  margin-top: 1rem;
}
.sale-text p {
  margin: 0;
  position: relative;
  top: 0.9rem;
  color: red;
  text-transform: uppercase;
  font-weight: 500;
}
.shop-now {
  background-color: white;
  padding: 2% 7%;
  color: red;
  text-transform: uppercase;
  font-weight: 700;
  text-transform: uppercase;
}
.sale-cont {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2% 0;
}
.span {
  height: 100%;
  position: relative;
  width: 7rem !important;
  left: 12%;
  padding: 11% 8%;
  background: linear-gradient(45deg, #91a71d, #858a7500);
}
.sale-img-pos {
  width: 22rem;
  position: relative;
  left: 24%;
  z-index: 2;
  display: flex !important;
}
.just {
  justify-content: start;
  column-gap: 3.4rem;
}
.row.just {
  margin-right: 0;
  margin-left: 0;
}
.d-img {
  width: 100%;
}
.cont {
  padding: 1px 7%;
  background-color: #e6e0e0;
  min-height: 100vh;
}
.carousel-item.active,
.carousel-item-next,
.carousel-item-prev {
  display: flex;
  max-height: 19rem;
}
/* Media query for xs */
@media (max-width: 575.98px) {
  h1 {
    font-size: 30px;
  }
  .sale-img-pos {
    width: 8rem;
    position: relative;
    height: 10rem;
    left: 13%;
    z-index: 2;
  }
  .sale-text {
    position: relative;
    text-align: center;
    right: 24%;
    border: solid;
    padding: 7px 3% 5% 4%;
  }
  .sale-cont {
    display: flex;
    align-items: center;
    justify-content: center;
    /* height: 10rem; */
    padding: 4%;
  }
  .shop-now {
    background-color: white;
    padding: 2% 7%;
    color: red;
    text-transform: uppercase;
    font-weight: 700;
    text-transform: uppercase;
    font-size: 12px;
  }
  .sale-text p {
    font-size: 10px;
    margin-bottom: 5%;
  }
  .sale-text h2 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }
  .card-img {
    width: 90%;
  }
  .just {
    justify-content: center;
  }
  .sale-image {
    margin: 7% 0;
  }
  .d-img {
    width: 80%;
  }
  .cont {
    padding: 15px 7% 15% 7%;
  }
  .carousel-item.active,
  .carousel-item-next,
  .carousel-item-prev {
    display: flex;
    max-height: auto;
  }
  .span {
    height: 87%;
    position: relative;
    width: 15rem;
    right: 7%;
    left: 0;
    padding: 13%;
    background: linear-gradient(45deg, #91a71d, #858a7500);
  }
}
</style>

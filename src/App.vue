<template>
  <div>
    <Header
      :items="items"
      @new="testCreate"
      @sort="doSortBy"
      :searchValue="searchValue"
      :sortBy="sortBy"
    />
    <Webpage :items="filteredItems" :logo="Logo" :searchValue="searchValue" />
  </div>
</template>

<script>
import Webpage from './components/Webpage';
import Header from './components/Header';
import Logo from './assets/images/ClipartKey_1992977.png';
import Logo1 from './assets/images/ClipartKey_1992966.png';
import Logo2 from './assets/images/ClipartKey_3003437.png';
import TestImg from './assets/images/product-1.jpg';
import TestImg1 from './assets/images/product-3.jpg';
import TestImg2 from './assets/images/product-2.jpg';
import TestImg3 from './assets/images/product-4.jpg';
import TestImg4 from './assets/images/product-5.jpg';
import TestImg5 from './assets/images/product-6.jpg';
import TestImg6 from './assets/images/product-7.jpg';
import TestImg7 from './assets/images/product-8.jpg';
import TestImg8 from './assets/images/vegetable-header-4-768x270.png';

export default {
  name: 'App',
  components: { Webpage, Header },
  data: () => {
    return {
      Logo: [Logo, Logo1, Logo2],
      items: [
        {
          image: TestImg2,
          text: 'Fresh Product',
          name: 'Strawberry',
          category: 'Product Merchant',
        },
        {
          image: TestImg,
          text: 'Fresh',
          name: 'pepper',
          category: 'Product Merchant',
        },
        {
          image: TestImg,
          text: 'Fresh',
          name: 'Tomato',
          category: 'Service Merchant',
        },
        {
          image: TestImg2,
          text: 'Fresh Product',
          name: 'Strawberry',
          category: 'Service Merchant',
        },
        {
          image: TestImg4,
          text: 'Fresh from the farm. Limited supply available',
          name: 'Tomato',
          category: 'Product Merchant',
        },
        {
          image: 'TestImg7',
          text: 'This is New',
          name: 'Melon',
          category: 'Service Merchant',
        },
        {
          image: TestImg5,
          text: 'Fresh Yo',
          name: 'Greens',
          category: 'Service Merchant',
        },
        {
          image: TestImg3,
          text: 'New Supply',
          name: 'Carbbage',
          category: 'Product Merchant',
        },
        {
          image: TestImg1,
          text: 'Fresh from the farm',
          name: 'Green Pea',
          category: 'Product Merchant',
        },
        {
          image: TestImg6,
          text: 'Fresh from Ota farm',
          name: 'Carrot',
          category: 'Service Merchant',
        },
        {
          image: TestImg7,
          text: 'Fresh Supply',
          name: 'Juice',
          category: 'Service Merchant',
        },
        {
          image: TestImg8,
          text: 'Fresh and healthy vegetables',
          name: 'Veggies',
          category: 'Product Merchant',
        },
        {
          image: TestImg3,
          text: 'New Supply',
          name: 'carbbage',
          category: 'Service Merchant',
        },
      ],
      colors: ['red', 'yellow', 'blue'],
      slide: 0,
      sliding: null,
      ascending: true,
      sortBy: '',
      searchValue: '',
      maxCookingTime: null,
    };
  },
  methods: {
    testCreate(e) {
      this.searchValue = e;
    },
    doSortBy(e) {
      this.sortBy = e.target.value;
    },
  },
  computed: {
    filteredItems() {
      let allItems = this.items;

      // Process search input
      if (this.searchValue != '' && this.searchValue) {
        allItems = allItems.filter((item) => {
          return item.name
            .toUpperCase()
            .includes(this.searchValue.toUpperCase());
        });
      }

      // Show sorted array by merchants
      if (this.sortBy === 'product') {
        let newArray = [];
        allItems.map((item) => {
          if (item.category === 'Product Merchant') {
            newArray = [...newArray, item];
          }
        });
        allItems = newArray;
      }
      if (this.sortBy === 'service') {
        let newArray = [];
        allItems.map((item) => {
          if (item.category === 'Service Merchant') {
            newArray = [...newArray, item];
          }
        });
        allItems = newArray;
      }

      return allItems;
    },
  },
};
</script>

<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info" id="navtest">
      <b-navbar-brand href="#">VEGGIES</b-navbar-brand>
      <b-navbar-nav class="nav-search">
        <b-nav-form>
          <b-form-input
            size="sm"
            class="mr-sm-2"
            placeholder="Filter"
            v-on:input="filter"
          ></b-form-input>
        </b-nav-form>
        <b-navbar-nav>
          <h6 class="d-none d-sm-block">Sort By:</h6>
          <select
            name="sortBy"
            id="select"
            v-model="sortBy"
            @change="doSort"
            class="select"
          >
            <option value="select">Default</option>
            <option value="product">Product</option>
            <option value="service">Service</option>
          </select>
        </b-navbar-nav>
      </b-navbar-nav>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    items: Array,
  },
  data: () => {
    return {
      ascending: true,
      sortBy: 'select',
    };
  },
  methods: {
    filter: function(e) {
      this.$emit('new', e);
    },
    doSort(e) {
      this.$emit('sort', e);
      this.sortBy = e.target.value;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.nav-color {
  color: red;
  background-color: blue;
}
.bg-info {
  background-color: #7e92e1 !important;
}
h6 {
  align-self: flex-end;
  padding: 0px 4px;
  margin-top: 8px;
  position: revert;
}
.select {
  height: auto;
  padding: 4px 4px;
  border-radius: 5px;
  background-color: white;
}
@media (min-width: 992px) {
  .navbar-expand-lg {
    flex-flow: row nowrap;
    justify-content: space-around;
  }
  .nav-search {
    column-gap: 8rem;
  }
}
@media (max-width: 575.98px) {
  .nav-search {
    display: flex;
    flex-direction: row;
    width: 68%;
    column-gap: 10%;
  }
}
@media (max-width: 767.98px) {
  .nav-search {
    display: flex;
    flex-direction: row;
    width: 68%;
    column-gap: 10%;
  }
}
</style>

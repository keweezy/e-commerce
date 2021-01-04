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
        <!-- <h6>Sort By</h6> -->
        <select name="sortBy" id="select" v-model="sortBy" @change="doSort">
          <option value="select">Sort</option>
          <option value="ascending">acending</option>
          <option value="descending">descending</option>
        </select>
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
</style>

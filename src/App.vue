<template>
  <div class="container">
    <TheHeader
      class="mb-4"
      :all-length="realStateData.length"
      :active-length="filterBy('active').length"
      :inactive-length="filterBy('active', false).length"
      @filter-changed="setFilter"
      @order-changed="setOrder"
      @search-change="setSearch"
    />
    <RealStateList :real-state-data="presentationList" />
  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader';
import RealStateList from '@/components/RealStateList';

import realStateData from './data/realState';

export default {
  name: 'App',
  components: {
    TheHeader,
    RealStateList
  },
  data() {
    return {
      realStateData,
      filter: '',
      sort: 'address',
      search: ''
    }
  },
  methods: {
    filterBy(filter, boolean = true) {
      return filter ?
        this.realStateData
          .filter(data => boolean ? data[filter] : !data[filter])
        : this.realStateData;
    },
    setFilter(filter) {
      this.filter = filter;
    },
    orderBy(field) {
      return this.filteredList.sort((a, b) => {
        return typeof field === 'number'
          ? a[field] - b[field]
          : a[field].localeCompare(b[field]);
      });
    },
    setOrder(field) {
      this.sort = field;
    },
    setSearch(text) {
      this.search = text;
    }
  },
  computed: {
    filteredList() {
      return this.filterBy(...this.filter);
    },
    sortedList() {
      return this.orderBy(this.sort);
    },
    presentationList() {
      const regex = new RegExp(this.search, 'ig');
      return this.sortedList.filter(({ address, city }) =>
        address.match(regex) || city.match(regex)
      );
    }
  }
}
</script>

<style lang="scss">
.container {
  width: 100%;
  padding: .3rem 1rem;
}
</style>

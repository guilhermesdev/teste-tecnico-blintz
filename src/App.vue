<template>
  <div class="container">
    <TheHeader
      class="mb-4"
      :total-number="totalNumber"
      :number-of-active="numberOfActive"
      :number-of-inactive="numberOfInactive"
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
    },
    totalNumber() {
      const regex = new RegExp(this.search, 'ig');

      return this.realStateData.filter(({ address, city }) =>
        address.match(regex) || city.match(regex)
      ).length;
    },
    numberOfActive() {
      const filteredArray = this.filterBy(...['active', true]);
      const regex = new RegExp(this.search, 'ig');

      return filteredArray.filter(({ address, city }) =>
        address.match(regex) || city.match(regex)
      ).length;
    },
    numberOfInactive() {
      const filteredArray = this.filterBy(...['active', false]);
      const regex = new RegExp(this.search, 'ig');

      return filteredArray.filter(({ address, city }) =>
        address.match(regex) || city.match(regex)
      ).length;
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

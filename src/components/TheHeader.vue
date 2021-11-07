<template>
  <header>
    <div class="filters">
      <div class="input-field">
        <label for="filter">Filter</label>
        <select
          id="filter"
          v-model="selectedFilter"
          @change="$emit('filter-changed', selectedFilter)"
        >
          <option value="">All ({{ allLength }})</option>
          <option :value="['active', true]">Active ({{ activeLength }})</option>
          <option :value="['active', false]">Inactive ({{ inactiveLength }})</option>
        </select>
      </div>
      <div class="input-field">
        <label for="sort">Sort</label>
        <select
          id="sort"
          v-model="selectedSort"
          @change="$emit('order-changed', selectedSort)"
        >
          <option value="address">Address</option>
          <option value="city">City</option>
          <option value="state">State</option>
          <option value="zip">Zip</option>
        </select>
      </div>
    </div>

    <div class="search">
      <div class="input-field">
        <label for="search">Search</label>
        <input
          type="text"
          id="search"
          placeholder="Search Packages"
        />
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'TheHeader',
  props: {
    allLength: {
      type: Number,
      required: true
    },
    activeLength: {
      type: Number,
      required: true
    },
    inactiveLength: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      selectedFilter: '',
      selectedSort: 'address'
    }
  }
}
</script>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;

  background-color: var(--color-bg-header);
  padding: 2rem 1.5rem;

  border-radius: .3rem;
  border: 2px solid var(--color-border);
}

.filters {
  display: flex;
  gap: 1rem;
}
.input-field {
  display: flex;
  flex-direction: column;

  label {
    margin-bottom: .5rem;
    font-weight: 600;
    color: var(--color-text);
    text-transform: uppercase;
  }

  input, select {
    padding: .5rem .7rem;
    border-radius: .3rem;
    border: 2px solid var(--color-border);
    background-color: var(--color-bg);

    font-size: 1rem;

    outline-color: var(--color-text);
  }
}
</style>

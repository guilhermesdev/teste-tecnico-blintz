<template>
  <header>
    <div class="filters">
      <div class="input-field">
        <label for="filter">Filter</label>
        <select
          id="filter"
          class="mr-4"
          v-model="selectedFilter"
          @change="$emit('filter-changed', selectedFilter)"
        >
          <option value="">All ({{ totalNumber }})</option>
          <option :value="['active', true]">Active ({{ numberOfActive }})</option>
          <option :value="['active', false]">Inactive ({{ numberOfInactive }})</option>
        </select>
      </div>
      <div class="input-field">
        <label for="sort">Sort</label>
        <select
          id="sort"
          v-model="selectedSort"
          @change="$emit('order-changed', selectedSort)"
        >
          <option :value="['address', 'asc']">Address (A-Z)</option>
          <option :value="['address', 'desc']">Address (Z-A)</option>
          <option :value="['city', 'asc']">City (A-Z)</option>
          <option :value="['city', 'desc']">City (Z-A)</option>
          <option :value="['state', 'asc']">State (A-Z)</option>
          <option :value="['state', 'desc']">State (Z-A)</option>
          <option :value="['zip', 'asc']">Zip (0-9)</option>
          <option :value="['zip', 'desc']">Zip (9-0)</option>
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
          v-model.trim="search"
          @input="$emit('search-change', search)"
        />
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'TheHeader',
  props: {
    totalNumber: {
      type: Number,
      required: true
    },
    numberOfActive: {
      type: Number,
      required: true
    },
    numberOfInactive: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      selectedFilter: '',
      selectedSort: ['address', 'asc'],
      search: ''
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

  @media (max-width: 630px) {
    flex-direction: column;
    align-items: stretch;

    .filters {
      margin-bottom: 1rem;

      > * {
        flex: 1;
      }
    }
  }
}

.filters {
  display: flex;
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

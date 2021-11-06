<template>
  <header>
    <div class="filters">
      <div class="input-field">
        <label for="filter">Filter</label>
        <select id="filter">
          <option value="active">Active (2)</option>
        </select>
      </div>
      <div class="input-field">
        <label for="sort">Sort</label>
        <select id="sort">
          <option value="most_recent">Most Recent</option>
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
  name: 'TheHeader'
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

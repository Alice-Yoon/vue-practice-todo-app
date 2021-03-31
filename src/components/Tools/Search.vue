<template>
  <v-text-field
    v-model="$store.state.searchTerm"
    @input="$store.commit('setSearch', $event)"
    @focus="searchClosed = false"
    @blur='searchClosed = true'
    class="expanding-search mt-1"
    :class="{ closed : searchClosed && !$store.state.searchTerm }"
    placeholder="Search"
    prepend-inner-icon="mdi-magnify"
    filled
    dense
    clearable
  ></v-text-field>
</template>

<script>
export default {
  data() {
    return {
      searchClosed: true
    }
  }
}
</script>

<style>
  .expanding-search {
    transition: max-width 0.3s;
  }
  .expanding-search .v-input__slot {
    cursor: pointer !important;
  }
  .expanding-search.closed {
    max-width: 45px;
  }
  .expanding-search.closed .v-input__slot {
    background: transparent !important;
  }
</style>
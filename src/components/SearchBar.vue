<template>
  <nav>
    <div class="nav-wrapper">
      <form @submit="onSubmit">
        <div class="input-field">
          <input id="search" type="search" placeholder="Search" />
          <label class="label-icon" for="search">
            <i class="material-icons">search</i>
          </label>
          <i class="material-icons">close</i>
        </div>
      </form>
    </div>
  </nav>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onSubmit(event) {
      event.preventDefault();
      this.$emit("termChange", event.target.search.value);
    },
  },
};
</script>

<style scoped>
nav {
  margin-bottom: 25px;
}
</style>

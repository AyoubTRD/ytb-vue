<template>
  <nav>
    <div class="nav-wrapper container">
      <form>
        <div class="input-field">
          <input id="search" type="search" @input="onInput" />
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
    onInput(event) {
      this.$emit("termChange", event.target.value)
    }
  }
};
</script>

<style>
</style>
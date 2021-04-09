<template>
  <div class="search">
    <input
      :value="ip"
      placeholder="Search for any IP address or domain"
      class="input__search"
      @input="$emit('input', $event)"
    />
    <div class="btn__search" @click="$emit('click')">
      <img src="@/assets/images/icon-arrow.svg" alt="">
    </div>
  </div>
</template>

<script>
export default {
  props: ['ip'],
};
</script>

<style scoped>
.search {
  margin-top: 20px;
  width: 90vw;
  max-width: 600px;
  display: flex;
}

.input__search {
  border-radius: 10px 0 0 10px;
  width: calc(100% - 50px);
  outline: none;
  border: none;
  padding: 10px;
  box-sizing: border-box;
  color: #3d3d3d;
}

.btn__search {
  height: 50px;
  width: 50px;
  border-radius: 0 10px 10px 0;
  background-color: black;
  display: grid;
  place-content: center;
  cursor: pointer;
}
</style>
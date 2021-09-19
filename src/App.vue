<template>
  <div class="container">
    <FolderView name="$" :folders="folders" :files="files" />
  </div>
</template>

<script>
import FolderView from "./components/FolderView.vue";
import data from "./data/list";

export default {
  name: "App",
  components: {
    FolderView,
  },
  data: () => 
      data
  
  
};
</script>

<style lang="scss">
$backgroundColor: rgb(245, 226, 226);
$paddingAll: 1rem;
$marginDefault: 0;
$paddingDefault: 0;

* {
  margin: $marginDefault;
  padding: $paddingDefault;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
.container {
  margin: 0 auto;
  max-width: 1140px;
  background-color: $backgroundColor;
  padding: $paddingAll;
}
</style>

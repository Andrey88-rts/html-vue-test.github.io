<template>
  <p class="folder" data-folder="Это папка!" @click="toggleFolder">
    <figure>
      <img src="../img/iconFolder.png" alt="Файл" />
    </figure>
    {{ name }}
  </p>
  <template v-if="isOpened">
    <template v-for="(folder, idx) in folders" :key="idx.toString()">
      <FolderView :name="folder.name" :folders="folder.folders" :files="folder.files" />
    </template>
    <template v-for="(file, idx) in files" :key="idx.toString()">
      <FileView :name="file.name" />
    </template>
  </template>
</template>

<script>
import FileView from "./FileView";
export default {
  name: "FolderView",
  components: { FileView },
  props: {
    name: String,
    folders: Array,
    files: Array
  },
  data() {
    return {
      isOpened: false
    };
  },
  methods: {
    toggleFolder() {
      this.isOpened = !this.isOpened;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.folder {
  color: orangered;
  background-color: rgb(105, 201, 42);
  transition: background-color 0.3s ease-in-out;
  transition-delay: 0.1s;
  padding: 0.5rem;
  margin-bottom: 0.3rem;
  border-radius: 0.6rem;
  display: flex;
  align-items: center;

  &:hover {
    cursor: pointer;
    background-color: rgb(74, 163, 47);
    transition: background-color 0.3s ease-in-out;
    transition-delay: 0.1s;
  }
}

[data-folder] {
  position: relative;

  &::after {
    position: absolute;
    left: 0;
    top: 0;
    color: #333;
    background-color: rgb(72, 216, 137);
    box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
    content: attr(data-folder);
    padding: 0.3rem;
    border-radius: 0.3rem;
    opacity: 0;
    transition: 1s;
    pointer-events: none;
  }

  &:hover::after {
    opacity: 1;
    left: 10rem;
  }
}
</style>

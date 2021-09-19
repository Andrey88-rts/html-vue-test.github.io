<template>
  <p class="file" data-file="Это файл!">
    <figure>
      <img src="../img/iconFile.png" alt="Файл" />
    </figure>
    {{ name }}
  </p>
</template>

<script>
export default {
  name: "FileView",
  props: {
    name: String
  }
};
</script>

<style scoped lang="scss">
.file {
  color: green;
  padding: 1rem;
  background-color: rgb(24, 255, 255);
  margin-bottom: 0.5rem;
  margin-left: 1rem;
  border-radius: 0.6rem;
  transition: background-color 0.3s ease-in-out;
  transition-delay: 0.1s;
  display: flex;
  align-items: center;

  &:hover {
    cursor: pointer;
    background-color: rgb(20, 209, 209);
    transition: background-color 0.3s ease-in-out;
    transition-delay: 0.1s;
  }
}

[data-file] {
  position: relative;

  &::after {
    position: absolute;
    left: 0;
    top: 0;
    color: #333;
    background-color: rgb(87, 230, 255);
    box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
    content: attr(data-file);
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

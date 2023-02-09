<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import TheWelcome from "./components/TheWelcome.vue";
import instance from "./api";
import { ref, onMounted } from "vue";

const videoUrl = ref("");
const downloadTag = ref();
const filename = ref("");
onMounted(async () => {
  const result = await instance.get(
    "/api/addVideo?url=https://v.douyin.com/B5c7gFG/"
  );
  videoUrl.value =
    "https://vv.techxx.top/download?filename=" + result.data.filename + ".mp4";
  filename.value = result.data.filename + ".mp4";
  console.log(downloadTag.value);
  downloadTag.value.click();
});
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <a
      ref="downloadTag"
      style="display: none"
      :href="videoUrl"
      :download="filename"
      target="_blank"
      >kkk</a
    >
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

<template>
  <div class="app">
    <div v-if="preview" @click="toggle">{{ text }}</div>
    <textarea v-else v-model="text" rows="4" />

    <img
      class="img"
      src="https://source.unsplash.com/400x450/?girl,sexy"
      alt="image"
    />

    <div class="profile">
      <img
        class="avatar"
        src="./assets/thaddeusjiang.jpg"
        alt="thaddeus jiang"
      />
      <div>
        <div>
          TJ <span>@{{ today }}</span>
        </div>
        <div>
          <div>https://thaddeusjiang.com</div>
        </div>
      </div>
    </div>

    <button v-if="!preview" @click="toggle">preview</button>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const text = ref("");
    const preview = ref(false);

    const today = new Intl.DateTimeFormat("zh-CN").format(new Date());

    const toggle = () => {
      preview.value = !preview.value;
    };

    return { text, preview, today, toggle };
  },
};
</script>

<style scoped>
.app {
  padding: 16px 16px;
  background-color: #04293a;
  color: #e5e7eb;
}

textarea,
img {
  width: 100%;
}

.img {
  margin-top: 16px;
}

.avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
}

.profile {
  display: flex;
  margin-top: 16px;
}

.profile > div > div {
  padding-top: 4px;
  padding-left: 16px;
}

button {
  margin-top: 16px;
  width: 50%;
}
</style>
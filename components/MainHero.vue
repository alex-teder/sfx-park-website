<template>
  <section class="my-bkg text-white">
    <div style="background-color: rgba(40, 40, 40, 0.49)">
      <div class="q-px-lg q-py-xl q-mx-auto" style="width: min(800px, 100%)">
        <h1 class="text-h3 q-pb-md q-my-none text-weight-bold">Explore our library and find the perfect sound!</h1>
        <div v-if="!isUser">
          <p class="text-h6 text-weight-regular">Become a community member to download your favorite sounds.</p>
          <QBtn to="login" rounded color="primary">Register</QBtn>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts" setup>
import { useMyUserStore } from "~/stores/user";

const store = useMyUserStore();
const isUser = ref(!!store.user);

watch(store, () => {
  if (store.user) {
    isUser.value = true;
  } else {
    isUser.value = false;
  }
});
</script>

<style scoped>
.my-bkg {
  background-image: url("~/assets/hero-bkg.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>

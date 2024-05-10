<template>
  <div class="row container" style="min-height: inherit">
    <q-item
      v-for="service of services"
      :key="service.id"
      class="col-12 col-md-6 q-pa-none filter"
      clickable
      :to="{
        name: 'Service',
        params: { id: service.id },
      }"
    >
      <q-img
        class="img"
        :src="
          require(`@/assets/pages/${service.tag}/facade-1.jpg`)
        "
        :alt="service.name"
      >
        <div
          class="absolute-full text-h6 flex justify-center items-center text-uppercase shadow"
          style="background: transparent"
        >
          {{ service.name }}
        </div>
      </q-img>
    </q-item>
  </div>
</template>

<script>
import { services } from "@/data/services";
export default {
  data() {
    return {
      services,
    };
  },
};
</script>

<style lang="scss">
@keyframes filter {
  from {
    filter: grayscale(1);
  }
  to {
    filter: grayscale(0);
  }
}
.filter {
  filter: grayscale(1);
  &:hover {
    animation-name: filter;
    animation-duration: 0.5s;
    animation-fill-mode: both;

    & .shadow {
      font-size: 25px;
      opacity: 1;
    }
  }
}
.img {
  height: calc((100vh - 93px) / 2) !important;

  body.screen--xs & {
    height: auto !important;
  }
}
.shadow {
  text-shadow: 0px 5px 15px rgb(35, 33, 33);
  opacity: 0.6;
  transition: font-size 0.5s, opacity 0.5s;
}
</style>

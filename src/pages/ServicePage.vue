<template>
  <div class="row wrapper" v-if="service">
    <div class="col q-my-lg">
      <div class="row q-col-gutter-lg">
        <div class="col-12 col-md-6">
          <q-carousel animated v-model="slide" infinite autoplay>
            <q-carousel-slide
              v-for="n of service.facadeCount"
              :key="n"
              :name="n"
              :img-src="require(`@/assets/pages/${service.tag}/facade-${n}.jpg`)"
            />
          </q-carousel>
        </div>
        <div class="col-12 col-md-6 text-grey">
          <h1 class="text-h6 text-weight-bold q-mt-none text-uppercase">
            {{ service.name }}
          </h1>
          <div v-html="service.fullDescription"></div>
        </div>

        <div class="col-12" v-if="service.imagesCount">
          <h2 class="text-subtitle1 q-mt-none q-mb-lg text-uppercase">ФОТО</h2>

          <images-list :images="images" :total-count="service.imagesCount" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { services } from "@/data/services";
import ImagesList from "@/components/ImagesList.vue";

export default {
  components: { ImagesList },
  data() {
    return {
      service: null,
      imagesCount: 3,
      images: [],
      slide: 1,
    };
  },
  created() {
    const id = this.$route.params.id;
    this.service = services.find((service) => service.id === +id);

    this.getImages();
  },
  methods: {
    getImages() {
      for (let i = 1; i <= this.service.imagesCount; i++) {
        this.images.push({
          src: require(`@/assets/pages/${this.service.tag}/${i}.jpg`),
          name: `${this.service.tag} портфолио ${i}`,
        });
      }
    },
  },
};
</script>

<style></style>

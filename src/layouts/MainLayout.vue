<template>
  <q-layout view="lHh Lpr lFf">
    <div :class="{ 'slide-up': !visible }" class="slide fit">
      <video poster="https://cdn.quasar.dev/img/polina.jpg" autoplay loop muted>
        <source
          type="video/mp4"
          src="@/assets/main.mp4"
        />
      </video>
      <div class="fit absolute-top-left column justify-center items-center">
        <img src="@/assets/logo-white.svg" alt="" style="max-width: 250px" />
        <h1
          class="text-h2 text-white  text-center text-weight-regular"
        >
          Выполнение строительных работ <br />
          люой сложности
        </h1>

        <q-btn round @click="visible = false">
          <q-avatar size="42px">
            <img src="@/assets/down-chevron.png" />
          </q-avatar>
        </q-btn>
      </div>
    </div>

    <q-header
      class="header"
      :class="[rightDrawerOpen ? 'header-dark' : 'header-light']"
    >
      <q-toolbar class="q-py-md">
        <q-toolbar-title class="col-auto logo">
          <router-link to="/" class="">
            <img
              v-if="rightDrawerOpen"
              src="@/assets/logo-white.svg"
              alt=""
              width="100"
              height="61.48"
              style="display: block"
            />
            <img
              v-else
              src="@/assets/logo-black.svg"
              alt=""
              width="100"
              height="61.48"
              style="display: block"
            />
          </router-link>
        </q-toolbar-title>

        <q-space />

        <q-item clickable to="/requisites">Реквизиты</q-item>

        <q-item clickable to="/contacts">Контакты</q-item>

        <q-item clickable to="/portfolio">Фотогалерея</q-item>

        <div v-if="$q.screen.isMobile">
          <q-btn
            v-if="!rightDrawerOpen"
            flat
            dense
            icon="menu"
            aria-label="Menu"
            ref="menuButton"
            @click="rightDrawerOpen = true"
          />
          <q-btn
            v-else
            flat
            dense
            icon="close"
            aria-label="close"
            @click="rightDrawerOpen = false"
          />
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="rightDrawerOpen"
      overlay
      side="right"
      :width="$q.screen.gt.sm ? $q.screen.width * 0.3 : $q.screen.width"
      class="bg-secondary column justify-between"
      behavior="desktop"
    >
      <q-list class="text-white text-h5">
        <q-item class="q-py-md q-px-xl" clickable :to="{ name: 'Contacts' }">
          КОНТАКТЫ
        </q-item>
        <q-item class="q-py-md q-px-xl" clickable :to="{ name: 'Portfolio' }">
          ФОТОГАЛЕРЕЯ
        </q-item>
        <q-item class="q-py-md q-px-xl" clickable :to="{ name: 'Requisites' }">
          РЕКВИЗИТЫ
        </q-item>
      </q-list>
      <div
        class="row q-gutter-lg justify-center text-accent q-pa-xl "
      >
        <div class="col-12 text-center">
          <a href="tel:+79283332390" class="link">+7(928)333-23-90</a>
        </div>

        <div class="col-12 text-center">
          <a href="mailto:9283333390@mail.ru" class="link">
            9283333390@mail.ru
          </a>
        </div>

        <div class="row items-start col-12 justify-center">
          <a href="https://t.me/+79283332390" class="light-hover">
            <img src="@/assets/telegram.svg" width="16" />
          </a>

          <a href="https://wa.me/79283332390" class="q-ml-lg light-hover">
            <img src="@/assets/whatsapp.svg" width="16" />
          </a>
        </div>
      </div>
    </q-drawer>

    <q-page-container>
      <q-page class="bg-primary">
        <router-view />
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      rightDrawerOpen: false,
      visible: true,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/quasar.variables.scss";
@keyframes color {
  from {
    background: $primary;
    color: $dark;
  }
  to {
    background: $secondary;
    color: $primary;
  }
}

.logo {
  position: absolute;
  top: 16px;
  left: 50%;
  transform: translateX(-50%);
}

.q-toolbar {
  min-height: calc(61px + 32px);
}

.header {
  background: $primary;
  color: $dark;

  &-dark {
    animation-name: color;
    animation-duration: 0.3s;
    animation-fill-mode: forwards;
  }

  a {
    color: inherit;
    text-decoration: none;
  }
}

.slide {
  top: 0;
  position: absolute;
  z-index: 10000;
  transform: translateY(0);
}

.slide.slide-up {
  top: -100%;
  transition: all 0.5s;
}

video {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>

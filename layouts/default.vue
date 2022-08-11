<template>
  <section>
    <!-- LOADING SCREEN -->
    <loading :class="{ isDoneLoading: !isLoading }"></loading>

    <v-app dark class="dbd-container">
      <!-- HEADER -->
      <v-app-bar app class="mx-auto py-2 black">
        <Nuxt-link to="/" class="d-flex align-center">
          <img :src="logo" alt="Dead By Daylight" class="dbd-container__logo" />
        </Nuxt-link>
        <v-list class="d-flex black">
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :to="item.to"
            router
            exact
            class="d-none d-md-flex dbd-container__nav-link"
          >
            <img
              :src="item.icon"
              alt="navigation-icons"
              class="mr-4 dbd-container__nav-icon"
            />
            <v-list-item-content class="text-center">
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>
          <div class="d-flex justify-end">
            <v-btn icon class="d-md-none" @click="openMobileMenu()">
              <v-icon size="40px">
                {{ mobileMenu }}
              </v-icon>
            </v-btn>
          </div>
          <div :class="{ mobileMenuTranslated: mobileMenuIsClicked }" class="d-md-none dbd-container__overlay"></div>
          <div
            :class="{ mobileMenuTranslated: mobileMenuIsClicked }"
            class="
              d-flex
              justify-end
              dbd-container__mobile-menu
            "
          >
          <div class="d-flex flex-column justify-center align-center black dbd-container__mobile-menu-content">
            <v-btn
              icon
              class="d-md-none mb-6 mb-md-14 dbd-container__mobile-close-icon"
              @click="closeMobileMenu()"
            >
              <v-icon size="40px">
                {{ mobileMenuCross }}
              </v-icon>
            </v-btn>
            <div class="d-flex flex-column">
              <v-list-item
                v-for="(item, i) in items"
                :key="i"
                :to="item.to"
                router
                exact
                class="my-4 my-md-8 dbd-container__nav-link"
                @click="closeMobileMenu()"
              >
                <img
                  :src="item.icon"
                  alt="navigation-icons"
                  class="mr-4 dbd-container__nav-icon"
                />
                <v-list-item-content class="text-center">
                  <v-list-item-title v-text="item.title" />
                </v-list-item-content>
              </v-list-item>
            </div>
          </div>
          </div>
        </v-list>
      </v-app-bar>

      <!-- MAIN -->
      <v-main class="black main-container">
        <v-container class="main-container__content">
          <Nuxt />
        </v-container>
      </v-main>

      <!-- FOOTER -->
      <v-footer dark padless class="footer">
        <v-card
          flat
          tile
          class="footer__container greyDark lighten-1 text-center"
        >
          <v-card-text class="pt-4 pb-0" v-html="explanation"></v-card-text>

          <v-card-text>{{ contact }}</v-card-text>

          <v-card-text class="pt-0 pb-4">
            <v-btn icon>
              <a
                :href="webLink"
                target="_blank"
                class="mx-4 white--text text-decoration-none"
                color="white"
              >
                <v-icon size="24px">
                  {{ web }}
                </v-icon>
              </a>
            </v-btn>
            <v-btn icon>
              <a
                :href="linkedinLink"
                target="_blank"
                class="mx-4 white--text text-decoration-none"
              >
                <v-icon size="24px">
                  {{ linkedin }}
                </v-icon>
              </a>
            </v-btn>
          </v-card-text>

          <v-divider></v-divider>

          <v-card-text>
            © Manida Vilay - {{ new Date().getFullYear() }}
          </v-card-text>
        </v-card>
      </v-footer>
    </v-app>
  </section>
</template>

<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      isLoading: true,
      mobileMenuIsClicked: false,
      logo: require("../static/deadbydaylight-logo.png"),
      items: [
        {
          icon: require("../static/killers.webp"),
          title: "Killers",
          to: "/killers",
        },
        {
          icon: require("../static/survivors.webp"),
          title: "Survivors",
          to: "/survivors",
        },
        {
          icon: require("../static/killers.webp"),
          title: "Killers Perks",
          to: "/killers_perks",
        },
        {
          icon: require("../static/survivors.webp"),
          title: "Survivors Perks",
          to: "/survivors_perks",
        },
      ],
      mobileMenu: "mdi-segment",
      mobileMenuCross: "mdi-close",
      web: "mdi-web",
      linkedin: "mdi-linkedin",
      webLink: "https://manidavilay.com",
      linkedinLink: "https://www.linkedin.com/in/manida-vilay/",
      explanation:
        "This website was made by Manida VILAY, a french frontend developer in Vue|Nuxt in order to practise and earn experience, <br /> by combining her love for the game and her job.",
      contact: "Feel free to check her personal website or linkedin below",
    };
  },
  methods: {
    openMobileMenu() {
      this.mobileMenuIsClicked = true;
    },
    closeMobileMenu() {
      this.mobileMenuIsClicked = false;
    },
  },
  mounted() {
    setTimeout(() => {
      this.isLoading = false;
    }, 5000);
  },
};
</script>

<style lang="scss">
* {
  scroll-behavior: smooth;
}

.dbd-container {
  font-family: "Poppins", sans-serif;

  &__logo {
    width: 250px;

    @media all and (max-width: 600px) {
      width: 200px;
    }
  }

  &__nav-icon {
    width: 30px;
  }

  &__overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0,0,0,0.6);
    opacity: 0;
    transition: opacity 0.7s ease-in-out;
    pointer-events: none;
    overflow: hidden;

    &.mobileMenuTranslated {
      opacity: 1;
    }
  }

  &__mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    transform: translateX(100%);
    transition: transform 0.7s ease-in-out;

    &.mobileMenuTranslated {
      transform: translateX(0%);
    }

    @media all and (min-width: 960px) {
      transform: translateX(100%) !important;
    }
  }

  &__mobile-menu-content {
    width: 500px;

    @media all and (max-width: 600px) {
      width: 300px;
    }
  }
}

header {
  width: 85%;

  @media all and (max-width: 600px) {
    width: 100%;
  }
}

header,
.v-toolbar__content {
  height: auto !important;
}

.v-toolbar__content {
  justify-content: space-between;
}

.main-container {
  padding: 130px 0 50px !important;

  &__content {
    width: 85%;

    @media all and (max-width: 600px) {
      width: 90%;
    }
  }
}

.footer {
  &__container {
    width: 100%;
  }
}
</style>
<template>
  <v-app dark>
    <!-- HEADER -->
    <v-app-bar :clipped-left="clipped" fixed app>
      <Nuxt-link to="/">
        <v-toolbar-title v-text="title" />
      </Nuxt-link>
      <v-list class="d-flex">
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-app-bar>

    <!-- MAIN -->
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>

    <!-- FOOTER -->
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        // {
        //   icon: "mdi-apps",
        //   title: "Homepage",
        //   to: "/",
        // },
        {
          icon: "mdi-chart-bubble",
          title: "Killers",
          to: "/killers",
        },
        {
          icon: "mdi-chart-bubble",
          title: "Survivors",
          to: "/survivors",
        },
        {
          icon: "mdi-chart-bubble",
          title: "Survivors Perks",
          to: "/survivors-perks",
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Dead By Daylight",
    };
  },
};
</script>

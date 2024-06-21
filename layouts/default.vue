<template>
  <v-app>
    <v-card flat>
      <v-card-title>
        <v-bottom-navigation background-color="dark" dark shift grow>
          <v-btn
            v-for="(item, i) in ItemsMenu"
            :key="i"
            :to="item.link"
            @click="setTitle(item)"
          >
            <span>
              {{ item.text }}
            </span>
            <v-icon>
              {{ item.icon }}
            </v-icon>
          </v-btn>
        </v-bottom-navigation>
      </v-card-title>
    </v-card>

    <v-divider></v-divider>

    <v-card flat>
      <v-card-title>
        <v-alert text prominent type="warning" :icon="icon">
          <div class="title">
            {{ title }}
          </div>
        </v-alert>
      </v-card-title>
    </v-card>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      title: 'HOME',
      icon: 'mdi-home',
      ItemsMenu: [
        {
          text: 'HOME',
          icon: 'mdi-home',
          link: '/',
        },
        {
          text: 'CONTACT PERSON',
          icon: 'mdi-badge-account',
          link: '/contact-person',
        },
        {
          text: 'EDUCATION',
          icon: 'mdi-school-outline',
          link: '/education',
        },
        {
          text: 'WORK EXPERIENCE',
          icon: 'mdi-briefcase-outline',
          link: '/work-experience',
        },
        {
          text: 'SKILL',
          icon: 'mdi-basket-fill',
          link: '/skill',
        },
      ],
    }
  },

  methods: {
    setTitle(item) {
      this.title = item.text
      this.icon = item.icon
    },
  },
}
</script>

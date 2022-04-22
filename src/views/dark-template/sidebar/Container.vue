<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          Scarlat <span class="light-blue--text text--lighten-3">Marius</span>
        </h1>
        <span>
          Student <span class="light-blue--text text--lighten-3"> / </span>
          Developer
        </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{item}">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{items}">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template
                v-for="(item, i) in items"
              >
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="80"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'scarlatmariusstefan2018@gmail.com',
            },
            {
              name: 'Website',
              icon: 'mdi-web',
              text: 'https://marius004.github.io/resume/',
            },
            {
              name: 'Phone Number',
              icon: 'mdi-phone',
              text: '+40 785 596 472',
            },
            {
              name: 'Birth Date',
              icon: 'mdi-cake-variant',
              text: 'Jan 2, 2004',
            },
            {
              name: 'Residence',
              icon: 'mdi-map-marker',
              text: 'Craiova, Romania',
            },
          ],
        },
        socials: {
          title: 'SOCIAL',
          items: [
            {
              icon: 'mdi-github-circle',
              text: 'github.com/marius004',
              link: 'https://github.com/marius004',
            },
            {
              icon: 'mdi-linkedin',
              text: 'linkedin.com/in/marius-scarlat2004/',
              link: 'https://www.linkedin.com/in/marius-scarlat2004/',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [
            {
              icon: 'mdi-music',
              text: 'Music',
            },
            {
              icon: 'mdi-car',
              text: 'Formula 1',
            },
            {
              icon: 'mdi-bike',
              text: 'Cycling',
            },
            {
              icon: 'mdi-guitar-electric',
              text: 'Guitar',
            },
            {
              icon: 'mdi-laptop',
              text: 'Watching movies',
            },
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'English',
              value: 100,
            },
            {
              text : 'Romanian',
              value: 108,
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar{
    background: #2e2e2e;
}
</style>

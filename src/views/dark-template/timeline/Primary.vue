/* eslint-disable key-spacing */
<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="'Personal Projects'"
      >
        <v-timeline dense>
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    items: [
      {
        year : '2019',
        title: 'Chess Game',
        html : `
        <p>
            Current status: <span style="color: #ff9800;">Finished</span><br>Available on: <a target="_blank" href="https://github.com/marius004/Chess-Game">github.com/marius004/Chess-Game</a>
        </p>
        <p>
          At the beginning video games were the main motivation that inspired me to take up computer science.
          The project, in its core, is relatively simple. However, it proved to be a good learning experience because I learnt more about OOP, Design Patterns, SOLID and DRY principles.
        
          <h4>Features:</h4>
          <ul>
              <li>Indicate the legal moves for a specific piece on the table.</li>
              <li>Restart the game without quitting the app.</li>
          </ul>

          <br>
          
          <h4>Technologies used:</h4>
          <ul>
            <li>Java</li>
          </ul>
        </p>
        `,
        image: 'img/timeline/chess.png',
        icon : 'mdi-chess-knight',
      },
      {
        year : '2020',
        title: 'Sorting Algorithm Visualizer',
        html : `
          <p>
              Current status: <span style="color: #ff9800;">Finished</span>
              <br>
              Available on: <a target="_blank" href="https://marius004.github.io/sorting-visualizer">marius004.github.io/sorting-visualizer</a>
              <br>
              Repository: <a target="_blank" href="https://github.com/marius004/sorting-visualizer">github.com/marius004/sorting-visualizer</a>
          </p>
          <p>
            A sorting algorithm is a method for reorganizing a large number of items into a specific order, such as alphabetical, highest-to-lowest value, lowest-to-highest value.
            <br>
            In our case, the program is sorting the bars increasingly, according to their height.
            
            <h4>Features:</h4>
            <ul>
                <li>Responsive on mobile devices.</li>
                <li>Variety in sorting algorithms.</li>
            </ul>

            <br>

            <h4>Technologies used:</h4>
            <ul>
                <li>Vuejs</li>
                <li>Bootstrap</li>
            </ul>
          </p>
        `,
        image: 'img/timeline/visualizer.png',
        icon : 'mdi-chart-bar',
      },
      {
        year : '2020',
        title: 'Spotify Clone',
        html : `
          <p>
              Current status: <span style="color: #ff9800;">Finished</span><br>Available on: <a target="_blank" href="https://github.com/marius004/spotify-clone">github.com/marius004/spotify-clone</a>
          </p>
          <p>
            Being a huge music fan, I have always wanted to build a music player that would allow me to listen to my favorite songs and artists without having to skip annoying ads.
            <br>

            <h4>Features:</h4>
            <ul>
                <li>Implemented CRUD operations for users and songs.</li>
                <li>Implemented a custom web player.</li>
            </ul>

            <br>
            
            <h4>Technologies used:</h4>
            <ul>
                <li>.NET CORE</li>
                <li>Mongo</li>
                <li>Vuejs</li>
            </ul>
          </p>
        `,
        image: 'img/timeline/spotify-clone.png',
        icon : 'mdi-spotify',
      },
      {
        year : '2021',
        title: 'Started working on a competitive programming website like leetcode',
        html : `
          <p>
              Current status: <span class="light-blue--text lighten-3">Almost finished</span><br>Available on: <a target="_blank" href="https://github.com/marius004/phoenix">github.com/marius004/phoenix</a>
          </p>
          <p>
            Phoenix is a competitive programming website which allows users to run their code against custom test cases which are run on the server.
            <br>
            <h4>Features:</h4>
            <ul>
                <li>Created a remote code execution environment that is fast and secure.</li>
                <li>Created a complex CRUD panel for managing problems and tests. </li>
            </ul>

            <br>

            <h4>Technologies used:</h4>
            <ul>
                <li>Golang</li>
                <li>PostgreSQL</li>
                <li>React.js</li>
            </ul>
          </p>
        `,
        image    : 'img/timeline/phoenix.jpg',
        iconImage: 'img/timeline/phoenix-icon.jpeg',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      return items
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>

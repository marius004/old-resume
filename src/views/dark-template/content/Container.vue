<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="About me"
      >
        I'm a computer science student with a passion for software development, willing to take up new challenges and learn new things.
      </content-section>
      <content-section
        v-if="prouds"
        title="Achievements"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="experiences"
        title="Experience"
      >
        <v-layout
          v-for="(experience, i) in experiences"
          :key="i"
        >
          <v-flex md4>
            {{ experience.from }} - {{ experience.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="experience.title">{{ experience.title }}</strong>
            <div v-if="experience.location">
              <i>{{ experience.location }}</i>
            </div>
            <div v-if="experience.description">
              {{ experience.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    prouds: [
      {
        icon  : 'mdi-trophy',
        text  : 'Bronze medal at the National Olymiad of Informatics 2021',
        source: '',
      },
      {
        icon  : 'mdi-trophy',
        text  : 'Participation in International Autumn Tournament(Shumen, Bulgaria)',
        source: '',
      },
      {
        icon  : 'mdi-trophy',
        text  : 'Ranked 3rd in Cloudflight Coding Contest(Craiova)',
        source: '',
      },
    ],
    experiences: [
      {
        from       : 'Nov 2021',
        to         : 'Dec 2021',
        title      : 'Netrom Software Academy',
        location   : 'Craiova',
        description: 'NSA provided an insightful experience because I was able to see how it feels like to work for a software company and learn new things from the senior developers.',
      },
    ],
    educations: [
      {
        from       : '2018',
        to         : '2022',
        title      : 'Colegiul National Fratii Buzesti',
        location   : 'Craiova',
        description: '',
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>

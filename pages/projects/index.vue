<template>
  <v-col class="pad">
    <v-card
      class="pad logo py-4 d-flex justify-center splash flex-center cardColor"
      elevation="0"
    >
      <h1>List of Projects</h1>
    </v-card>
    <v-spacer></v-spacer>
    <div class="pad">
    <div id="gridStart" class="pad grid">
      <v-list
          v-for="(project, i) in projects"
          :key="i"
          color="transparent"
          class="item">
        <div class="imgContainer item">
          <v-img format="webp"
            :src="project.shrtImage"
            loading="lazy"
            :style="getFlippedClass(project)"
            @click="imgClick(project)"
          />
          <div
            v-if="!project.isFlipped"
            @click="imgClick(project)"
            class="compress topCharContent charContent highlight"
          >
            <h2>Click Me!</h2>
          </div>
          <div
            v-if="!project.isFlipped"
            @click="imgClick(project)"
            class="frontCharContent charContent highlight"
          >
            <h2>{{ project.name }}</h2>
          </div>
          <div
            v-if="project.isFlipped"
            class="charContent"
            @click="imgClick(project)"
          >
            <h3 class="backCharContent charContent highlight" style="">
              {{ project.name }}
            </h3>
            <h4>Description:</h4>
            <span>{{ project.shrtDesc }}</span>
            <h4>README:</h4>
            <span
              ><a :href="project.readmeFile" target="_blank" class="highlight"
                >Download Package &gt;&gt;</a
              ></span
            >
            <h4>Data:</h4>
            <span
              ><a :href="project.link" target="_blank" class="highlight"
                ><component :is="project.linkIcon"></component></a
            ></span>
          </div>
        </div>
      </v-list>
    </div>
    </div>
  </v-col>
</template>

<script>
export default {
  name: 'ProjectPages',
  data() {
    return {
      currentFlippedItem: '',
      projects: {
        'L1448 IRS3B': {
          name: 'L1448 IRS3B',
          shrtDesc:
            'We resolved the system, L1448 IRS3B, to be a compact ring with IRS3B-a/b to be inside/outside of the ring respectively. Additionally we found the disk is gravitationally unstable and could be a system with 5 sources within 2500au. Paper accepted to APJL',
          readmeFile: '',
          shrtImage: '/l1448irs3bcontinuum.jpg',
          link: 'https://github.com/nickalaskreynolds/ALMAc4-L1448IRS3B-2016.1.01520.S',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
        'Perseus Multiples Continuum': {
          name: 'Perseus YSOs 8au',
          shrtDesc:
            'Statistical study of 32 Perseus protostars at high resolution (8au). Paper submitted to APJL',
          readmeFile: '',
          shrtImage: '/perseusmultiplescontinuum.jpg',
          link: 'https://github.com/nickalaskreynolds/ALMAc7-PerseusMultiples-Statistics',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
        'Perseus Multiples Kinematics': {
          name: 'Perseus YSOs C18O Kinematics',
          shrtDesc:
            'Statistical study of 33 Perseus protostars at high sensitivity kinematic observations to determine the central potential masses for each of the sources. Paper in prep.',
          readmeFile: '',
          shrtImage: '/perseusmultiplesspectra.jpg',
          link: 'https://github.com/nickalaskreynolds/ALMAc5-PerseusMultiples-2017.1.0053.S',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
        'Orion and Perseus Protostellar Spectra': {
          name: 'Orion and Perseus Protostellar Spectra',
          shrtDesc:
            'Statistical study of ~100 protostars in Orion and Perseus molecular clouds using the medium spectrograph Triplespec found on the Apache Pointe Observatory. Paper in prep.',
          readmeFile: '',
          shrtImage: '/apo.jpg',
          link: 'https://github.com/nickalaskreynolds/APO-Triplespec-Protostar-Spectra',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
        'SMT Mapping of gas in Perseus': {
          name: 'SMT Mapping of the dense gas in Perseus',
          shrtDesc:
            'Mapping the D/H ratio and CO for several Perseus protostars using the Sub Millimeter Telescope of the ARO consortium. Paper in prep.',
          readmeFile: '',
          shrtImage: '/smt.jpg',
          link: 'https://github.com/nickalaskreynolds/SMT-Protostar-Mapping',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
        'IRAM 30m High Resolution Spectra': {
          name: 'High resolution Spectra of Perseus',
          shrtDesc:
            'Statistical study of ~40 Perseus Protostars using the IRAM 30m telescope targeting the N2H+ line to study the core characteristics. This is done in collaboration with Kyler Rogers and Dr. John Tobin. Paper in prep.',
          readmeFile: '',
          shrtImage: '/iram-2.jpg',
          link: 'https://github.com/nickalaskreynolds/ALMAc5-PerseusMultiples-2017.1.0053.S',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
        'BHR7': {
          name: 'BHR7 disk-to-envelope',
          shrtDesc:
            'We conduct high resolution continuum and kinematic observations towards BHR7 to link the large scale envelope structures down to the compact disk. Paper in prep.',
          readmeFile: '',
          shrtImage: '/bhr7-12co.jpg',
          link: 'https://github.com/nickalaskreynolds/ALMAc6-BHR7-2019.1.00463.S',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
        'OU PhD 2023': {
          name: 'PhD Dissertation',
          shrtDesc:
            'I completed my PhD at the University of Oklahoma in 2023 in Physics and Astronomy.',
          readmeFile: '',
          shrtImage: '/iram30m_1.jpg',
          link: 'https://github.com/nickalaskreynolds/PhD-Dissertation-2023',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
        'OU Masters 2021': {
          name: 'Masters Thesis',
          shrtDesc:
            'I completed my Masters at the University of Oklahoma in spring 2021 in Physics and Astronomy.',
          readmeFile: '',
          shrtImage: '/iram30m_1.jpg',
          link: 'https://github.com/nickalaskreynolds/Masters-Thesis-2021',
          linkIcon: 'IconsGithub',
          isFlipped: false,
        },
      },
    }
  },
  methods: {
    getFlippedClass(project) {
      if (project.isFlipped) {
        return 'open'
      } else {
        return 'close'
      }
    },
    imgClick(item) {
      item.isFlipped = !item.isFlipped
    },
    close() {
      this.$emit('close')
    },
  },
}
</script>

<style scoped lang="scss">
@import '@/assets/mixins.scss';
@import '@/assets/variables.scss';

.cardColor {
  @include cardColor;
}
.splash {
  @include splash;
}
.highlight {
  @include highlight;
}
.bolden {
  @include bolden;
}
a {
  text-decoration: underline;
}
.grid {
  display: grid;
  grid-gap: 10px;
  justify-content: center;
  align-content: center;
  gap: 10px;
  grid-auto-flow: row dense;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  position: relative;
  min-width: 160px;
  width: 100%;
  grid-area: auto;
  grid-row-start: auto;
  grid-column-start: auto;
  cursor: pointer;
}

.grid::before {
  content: '';
  width: 300px;
  padding-bottom: 0%;
  grid-row: 1;
  grid-column: 1;
}
.grid > *:first-child {
  grid-row: 1;
  grid-column: 1;
}
.item {
  display: flex;
  position: relative;
  min-width: 150px;
  min-height: 150px;
  width: 300px;
  height: 300px;
}

.imgContainer {
  display: flex;
  position: relative;
  text-align: bottom;
  width: 100%;
  min-width: 150px;
}

.frontCharContent {
  text-align: center;
  bottom: 0;
}
.topCharContent {
  text-align: right !important;
  top: 0 !important;
}
.backCharContent {
  text-align: none;
  overflow: scroll;
}
.charContent {
  @include cardColor;
  position: absolute;
  left: 0;
  right: 0;
  margin: auto;
}
.backCharContent h3 {
  @include cardColor;
  display: inline-block;
  line-height: auto;
  padding: 3px 8px 3px 8px;
  font-size: 130%;
}
.charContent .highlight {
  text-decoration: underline;
}

.open {
  animation-duration: 0.5s;
  animation-iteration-count: 1;
  animation-name: turn;
  animation-timing-function: ease-in-out;
  animation: turn 3.5s ease-out forwards 1s;
}
.close {
  animation-duration: 0.5s;
  animation-iteration-count: 1;
  animation-name: turn;
  animation-timing-function: ease-in-out;
  animation: turn 3.5s ease-out forwards 1s;
}

@keyframes turn {
  100% {
    transform: rotateY(180deg);
  }
}

.details {
  display: none;
  line-height: 80%;
}
.details .bio {
  font-size: 80%;
  padding: 10px;
  text-align: left;
}
.details span {
  font-size: 100%;
}
.portrait {
  max-height: 100%;
  margin: 0 -200%;
}
.bioLink {
  margin-top: 20px;
}
.open .details {
  display: flex;
  height: 100%;
}
.open .charContent {
  @include cardColor;
  position: relative;
  width: 100%;
  height: 100%;
}
.open .charContent h2 {
  display: none;
}
</style>

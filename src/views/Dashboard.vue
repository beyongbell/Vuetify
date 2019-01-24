<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard </h1>
    <v-container class="my-5">
      <v-layout row class="mb-3">
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>folder</v-icon>
            <span class="caption text-lowercase">By project name</span>
          </v-btn>
          <span>Sort Project by project name</span>
        </v-tooltip>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
            <v-icon left small>person</v-icon>
            <span class="caption text-lowercase">By person</span>
          </v-btn>
          <span>Sort Project by person</span>
        </v-tooltip>
      </v-layout>
      <v-card flat v-for="project in projects" :key="project.title">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <div class="caption grey--text"> Project Title </div>
            <div> {{ project.title }} </div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text"> Person </div>
            <div> {{ project.person }} </div>
          </v-flex>
           <v-flex xs6 sm4 md2>
            <div class="caption grey--text"> Due by </div>
            <div> {{ project.due }}  </div>
          </v-flex>
           <v-flex xs2 sm4 md2>
             <div>
                 <v-chip small :class="`${project.status} white--text caption my-2`">{{ project.status }}</v-chip>
             </div>
          </v-flex>
          <v-divider></v-divider>
        </v-layout>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects : [
        {title: 'B', person : 'c', due: 1, status: 'doing'},
        {title: 'A', person : 'a', due: 2, status: 'complete'},
        {title: 'C', person : 'b', due: 3, status: 'doing'}
      ]
    }
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1)
    }
  },
}
</script>

<style>
  .project.doing {
    border-left : 4px solid orange
  }
  .project.complete {
    border-left : 4px solid green
  }
  .v-chip.doing {
    background: orange
  }
  .v-chip.complete {
    background: green
  }
</style>

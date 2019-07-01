<template>
  <v-app id="inspire">
    <v-content>
      <v-container fluid>
        <v-layout align-start justify-center>
          <!-- <v-flex xs4 class="elevation-1 pa-3 ma-2">
            <v-card>
              <v-toolbar color="black" dark>
                <v-toolbar-title>Roster</v-toolbar-title>
              </v-toolbar>

              <v-list>
                <draggable
                  v-model="items"
                  group="people"
                  style="min-height: 10px"
                >
                  <template v-for="item in items">
                    <v-list-tile :key="item.id" avatar>
                      <v-avatar color="light-green darken-3" class="mr-2">
                        <span class="white--text headline">{{
                          item.avatar
                        }}</span>
                      </v-avatar>
                      <v-list-tile-content>
                        <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                  </template>
                </draggable>
              </v-list>
            </v-card>
          </v-flex> -->
          <v-layout row wrap xs12 class="elevation-1 pa-3 ma-2">
            <v-flex v-for="(team, index) in teams" :key="index" xs4 class="">
              <v-card>
                <v-toolbar :color="team.color">
                  <v-toolbar-title>{{ team.name }}</v-toolbar-title>
                </v-toolbar>
                <v-list two-line>
                  <draggable
                    v-model="team.list"
                    group="people"
                    style="min-height: 10px"
                    @change="setStorageData"
                  >
                    <template v-for="item in team.list">
                      <v-list-tile :key="item.id" avatar>
                        <v-avatar :color="team.color" class="mr-2">
                          <span class="headline">{{ item.avatar }}</span>
                        </v-avatar>
                        <v-list-tile-content>
                          <v-list-tile-title>{{
                            item.title
                          }}</v-list-tile-title>
                        </v-list-tile-content>
                      </v-list-tile>
                    </template>
                  </draggable>
                </v-list>
              </v-card>
            </v-flex>
          </v-layout>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'Home',
  components: {
    draggable
  },
  data() {
    return {
      dItems: [
        {
          id: 1,
          avatar: 'AA',
          title: 'Adam'
        },
        {
          id: 2,
          avatar: 'PM',
          title: 'Pavlínka'
        },
        {
          id: 3,
          avatar: 'VD',
          title: 'Vašík'
        },
        {
          id: 4,
          avatar: 'ZB',
          title: 'Zdenda'
        },
        {
          id: 5,
          avatar: 'MP',
          title: 'Martin'
        },
        {
          id: 6,
          avatar: 'LN',
          title: 'Novas'
        },
        {
          id: 7,
          avatar: 'MV',
          title: 'Marcel'
        },
        {
          id: 8,
          avatar: 'VT',
          title: 'Vadim'
        },
        {
          id: 9,
          avatar: 'VS',
          title: 'Vojta'
        },
        {
          id: 10,
          avatar: 'JH',
          title: 'Jan H.'
        },
        {
          id: 11,
          avatar: 'OB',
          title: 'Ondra B.'
        },
        {
          id: 12,
          avatar: 'JJ',
          title: 'Kuba'
        },
        {
          id: 13,
          avatar: 'JK',
          title: 'Jirka K.'
        },
        {
          id: 14,
          avatar: 'TK',
          title: 'Tomáš'
        },
        {
          id: 15,
          avatar: 'VV',
          title: 'Viky'
        }
      ],
      dTeams: [
        { name: 'Mercedes', list: [], color: 'blue-grey lighten-3' },
        { name: 'Ferrari', list: [], color: 'red lighten-1' },
        { name: 'McLaren', list: [], color: 'deep-orange lighten-1' },
        { name: 'Williams', list: [], color: 'light-blue lighten-4' },
        { name: 'Renault', list: [], color: 'yellow lighten-2' }
      ],
      items: [],
      teams: []
    }
  },
  mounted() {
    const data = this.getStorageData()
    this.items = JSON.parse(data.items) || this.dItems
    this.teams = JSON.parse(data.teams) || this.dTeams
  },
  methods: {
    setStorageData() {
      sessionStorage.setItem('items', JSON.stringify(this.items))
      sessionStorage.setItem('teams', JSON.stringify(this.teams))
    },
    getStorageData() {
      return {
        items: sessionStorage.getItem('items'),
        teams: sessionStorage.getItem('teams')
      }
    }
  }
}
</script>

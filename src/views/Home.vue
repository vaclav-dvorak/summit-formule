<template>
  <v-app id="inspire">
    <v-content>
      <v-container fluid>
        <v-layout align-start justify-center>
          <v-flex xs4 class="elevation-1 pa-3 ma-2">
            <v-card>
              <v-toolbar color="black" dark>
                <v-toolbar-title>Roster</v-toolbar-title>
              </v-toolbar>

              <v-list>
                <draggable
                  v-model="items"
                  :options="{ group: 'people' }"
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
          </v-flex>
          <v-layout row wrap xs8 class="elevation-1 pa-3 ma-2">
            <v-flex v-for="(team, index) in teams" :key="index" xs6 class="">
              <v-card>
                <v-toolbar :color="team.color">
                  <v-toolbar-title>{{ team.name }}</v-toolbar-title>
                </v-toolbar>
                <v-list two-line>
                  <draggable
                    v-model="team.list"
                    :options="{ group: 'people' }"
                    style="min-height: 10px"
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
      items: [
        {
          id: 1,
          avatar: 'AA',
          title: 'Adam'
        },
        {
          id: 2,
          avatar: 'PM',
          title: 'Paja'
        },
        {
          id: 3,
          avatar: 'VD',
          title: 'Vasik'
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
        }
      ],
      teams: [
        { name: 'Mercedes', list: [], color: 'blue-grey lighten-3' },
        { name: 'Ferrari', list: [], color: 'red lighten-1' },
        { name: 'McLaren', list: [], color: 'deep-orange lighten-1' },
        { name: 'Williams', list: [], color: 'light-blue lighten-4' },
        { name: 'Renault', list: [], color: 'yellow lighten-2' },
        { name: 'Red Bull Racing', list: [], color: 'grey darken-1' }
      ]
    }
  }
}
</script>

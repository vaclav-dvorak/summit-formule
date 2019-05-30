<template>
  <v-app id="inspire">
    <v-content>
      <v-container fluid>
        <v-layout align-start justify-center>
          <v-flex xs4 class="elevation-1 pa-3 ma-2">
            <v-card>
              <v-toolbar color="red lighten-2">
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
                <v-toolbar color="blue lighten-1">
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
                        <v-avatar color="red darken-2" class="mr-2">
                          <span class="white--text headline">{{
                            item.avatar
                          }}</span>
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
      teams: {
        mercedes: { name: 'Mercedes', list: [] },
        ferrari: { name: 'Ferrari', list: [] },
        mclaren: { name: 'McLaren', list: [] },
        williams: { name: 'Williams', list: [] },
        renault: { name: 'Renault', list: [] }
      }
    }
  }
}
</script>

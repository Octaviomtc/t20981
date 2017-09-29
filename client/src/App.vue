<template>
  <v-app id="example-2" toolbar>
    <v-navigation-drawer permanent light :mini-variant.sync="mini" v-model="drawer" overflow>
      <v-toolbar flat class="transparent">
        <v-list class="pa-0">
          <v-list-tile avatar>
            <v-list-tile-avatar>
              <img src="https://scontent.fmex8-2.fna.fbcdn.net/v/t31.0-8/13340288_10209223798933130_2484225004412554404_o.jpg?oh=edd70c58f8edd6fe231b0bccf035537e&oe=5A51E95B" />
            </v-list-tile-avatar>
            <v-list-tile-content>
              <v-list-tile-title>Octavio Martinez</v-list-tile-title>
            </v-list-tile-content>
            <v-list-tile-action>
              <v-btn icon @click.native.stop="mini = !mini">
                <v-icon>chevron_left</v-icon>
              </v-btn>
            </v-list-tile-action>
          </v-list-tile>
        </v-list>
      </v-toolbar>
      <v-list class="pt-0" dense>
        <v-divider></v-divider>
        <v-list-tile v-for="item in items" :key="item.title" @click="" :title="item.title" :v-show="item.if">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>

      </v-list>
    </v-navigation-drawer>
    <main>
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </main>
  </v-app>
</template>

      </main>
    </v-app>
  </div>
</template>

<script>
import PageHeader from '@/components/Header.vue'

export default {
  name: 'app',
  components: {
    PageHeader
  }
}
</script>
<script>
export default {
  data () {
    return {
      drawer: null,
      items: [
        { title: 'Home', icon: 'dashboard', if: false },
        { title: 'About', icon: 'question_answer', if: true },
        { title: 'Logout', icon: 'highlight_off', if: '$store.state.isUserLoggedIn', action: 'logout' }
      ],
      mini: false,
      right: null
    }
  },
  methods: {
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({
        name: 'songs'
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.danger-alert {
  color: red;
}
</style>

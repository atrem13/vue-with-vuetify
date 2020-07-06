<template>
    <nav>
      <v-navigation-drawer 
        v-model="drawer" 
        app 
        class="primary">
        <v-layout column class="text-center">
          <v-flex class="mt-5">
            <v-avatar size="120">
              <img src="avatar/avatar-1.png" alt=""/>
            </v-avatar>
            <p class="text-subtitle-1 mt-3 white--text">The Net Ninja</p>
            <Dialog/>
          </v-flex>
        </v-layout>
        <v-list>  
          <v-list-item-group >
            <v-list-item
              v-for="link in links"
              :key = "link.text"
              router 
              :to="link.route"
            >
              <v-list-item-icon>
                <v-icon class="white--text">{{link.icon}}</v-icon>
              </v-list-item-icon>

              <v-list-item-content>
                <v-list-item-title class="white--text">{{link.text}}</v-list-item-title>
              </v-list-item-content>
            
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-navigation-drawer>
       
      <v-app-bar
        app
        flat
      >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title class="text-uppercase grey--text">
          <span>Todo</span> 
          <span class="font-weight-light">Ninja</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-menu offset-y>
          <template v-slot:activator="{on, attrs}">
            <v-btn
              text
              color="grey"
              v-bind="attrs"
              v-on="on"
            >
              <v-icon left>expand_more</v-icon>
              Menu
            </v-btn>
          </template>
          <v-list>
            <v-list-item
              v-for="link in links"
              :key="link.text"
              router
              :to="link.route"
            >
              <v-list-item-title>
                <v-icon left>{{link.icon}}</v-icon> 
                {{link.text}}
              </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-btn text color="grey">
          Sign Out
          <v-icon right>exit_to_app</v-icon>
        </v-btn>
      </v-app-bar>

        
    </nav>
</template>
<script>
import Dialog from './Dialog'
export default {
    components:{ Dialog },
    data(){
      return{
        drawer:false,
        links:[
          {
            text:'dashboard',
            icon:'dashboard',
            route:'/'
          },
          {
            text:'project',
            icon:'folder',
            route:'/project'
          },
          {
            text:'team',
            icon:'person',
            route:'/team'
          }
        ]
      }
    }
}
</script>
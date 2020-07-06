<template>
    <div class="team">
        <h1 class="subheading grey--text">Team</h1>
        <v-container class="my-5">
            <v-layout row wrap>
                <v-flex xs12 sm6 md4 lg3 v-for="team in teams" :key="team.name">
                    <v-card outlined class="ma-5">
                        <v-card-text class="text-center">
                            <v-responsive class="pa-5">
                                <v-avatar size="120" class="grey lighten-4">
                                    <img :src="`avatar${team.avatar}`" alt="">
                                </v-avatar>
                            </v-responsive>
                            <div class="text-subtitle-2">{{team.name}}</div>
                            <div class="text-caption grey--text">{{team.role}}</div>
                        </v-card-text>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn
                                text
                                color="grey mr-3"
                            >
                                Message
                                <v-icon right flat>message</v-icon>
                            </v-btn>
                        </v-card-actions>
                    </v-card>
                </v-flex>
            </v-layout>
        </v-container>
    </div>
</template>
<script>
export default {
    data(){
        return{
            teams: [
                { name: 'The Net Ninja', role: 'Web developer', avatar: '/avatar-1.png' },
                { name: 'Ryu', role: 'Graphic designer', avatar: '/avatar-2.png' },
                { name: 'Chun Li', role: 'Web developer', avatar: '/avatar-3.png' },
                { name: 'Gouken', role: 'Social media maverick', avatar: '/avatar-4.png' },
                { name: 'Yoshi', role: 'Sales guru', avatar: '/avatar-5.png'}

            ]
        }
    }
}
</script>
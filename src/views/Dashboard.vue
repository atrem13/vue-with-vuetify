<template>
    <div class="dashboard">
        <h1 class="subheading grey--text">Dashboard</h1>
        <v-container class="my-5">
            <v-layout row class="mb-3">
                <v-tooltip top>
                    <template v-slot:activator="{on, attrs}">
                        <v-btn 
                            v-bind="attrs"
                            v-on="on"
                            small 
                            text 
                            color="grey" 
                            @click="sortBy('title')"
                        >
                            <v-icon left>folder</v-icon>
                            <span class="text-subtitle-1 text-lowercase">by project name</span>
                        </v-btn>
                    </template>
                    <span class="text-caption">sort data by project name</span>
                </v-tooltip>
                <v-tooltip top>
                    <template v-slot:activator="{on, attrs}">
                        <v-btn 
                            v-bind="attrs"
                            v-on="on"
                            small 
                            text 
                            color="grey" 
                            @click="sortBy('person')"
                        >
                            <v-icon left>person</v-icon>
                            <span class="text-subtitle-1 text-lowercase">by person</span>
                        </v-btn>
                    </template> 
                    <span class="text-caption">sort data by person name</span>   
                </v-tooltip>
            </v-layout>
            <v-card flat v-for="project in projects" :key="project.title">
                <v-layout row wrap :class="`pa-3 project ${project.status}`" >
                    <v-flex xs12 sm12 md6>
                        <div class="caption grey--text">Project</div>
                        <div>{{project.title}}</div>
                    </v-flex>
                    <v-flex xs6 sm4 md2 >
                        <div class="caption grey--text">Person</div>
                        <div>{{project.person}}</div>
                    </v-flex>
                    <v-flex xs6 sm4 md2 >
                        <div class="caption grey--text">Due by</div>
                        <div>{{project.due}}</div>
                    </v-flex>
                    <v-flex xs12 sm4 md2 >
                        <div class="mt-2">
                            <v-chip :color="project.color" class="white--text caption">{{project.status}}</v-chip>
                        </div>
                    </v-flex>
                </v-layout>
                <v-divider></v-divider>
            </v-card>
        </v-container>
    </div>
</template>
<style scoped>
    .project.complete{
        border-left : 4px solid #8df1f1 ;
    }
    .project.ongoing{
        border-left: 4px solid #ffc640;
    }
    .project.overdue{
        border-left: 4px solid #f03c0f;
    }
</style>
<script>
export default {
    data(){
        return{
            projects: [
                { title: 'Design a new website',color:'#ffc640', person: 'The Net Ninja', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci non sequi animi!'},
                { title: 'Code up the homepage',color:'green', person: 'Chun Li', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci  sequi animi!'},
                { title: 'Design video thumbnails',color:'#8df1f1', person: 'Ryu', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci  sequi animi!'},
                { title: 'Create a community forum',color:'#f03c0f', person: 'Gouken', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci  sequi animi!'},
            ]
        }
    },
    methods:{
        sortBy(prop){
            this.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1);
        }
    }
}
</script>
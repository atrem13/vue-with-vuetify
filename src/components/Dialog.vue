<template>
    <v-dialog v-model="dialog" persistent max-width="600px">
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="success"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Add New Project
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="headline">New Project</span>
        </v-card-title>
        <v-card-text>
          <v-container>
              <v-form>
                <v-row>
                    <v-col cols="12" sm="6" md="6">
                        <v-text-field 
                            label="Project Title" 
                            prepend-icon="work"
                        ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="6">
                        <v-menu
                            v-model="datePicker"
                            :close-on-content-click="false"
                            :nudge-right="40"
                            transition="scale-transition"
                            offset-y
                            min-width="290px"
                        >
                            <template v-slot:activator="{ on, attrs }">
                            <v-text-field
                                v-model="dueDate"
                                label="Due Date"
                                prepend-icon="event"
                                readonly
                                v-bind="attrs"
                                v-on="on"
                            ></v-text-field>
                            </template>
                            <v-date-picker v-model="dueDate" @input="datePicker = false"></v-date-picker>
                        </v-menu>
                    </v-col>
                    <v-col cols="12" xs="12">
                        <v-textarea
                            label="Content"
                            prepend-icon="description"
                        ></v-textarea>
                    </v-col>
                </v-row>

              </v-form>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="dialog = false">Close</v-btn>
          <v-btn color="blue darken-1" text @click="dialog = false">Save</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>
<script>
import format from 'date-fns/format'
export default {
    data(){
        return{
            dialog:false,
            dueDate:'',
            datePicker:false,
        }
    },
    computed:{
        deadline(){
            return this.dueDate ? format(this.dueDate, 'Do MMMM YYYY') : '' 
        }
    }
}
</script>
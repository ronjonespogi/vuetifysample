<div>
    <p>
        {{ fname }}
    </p>
    <v-data-table
            v-bind:headers="headers"
            :items="items"
            class="elevation-1"
            v-model="selected"
    >
        <!--<template slot="headerCell" scope="props">
      <span v-tooltip:bottom="{ 'html': props.header.text }">
        {{ props.header.text }}
      </span>
        </template>-->

        <template slot="items" scope="props">
            <tr @click="showAlert(props.item)">
            <td>{{ props.item.name }}</td>
            <td class="text-xs-right">{{ props.item.calories }}</td>
            <td class="text-xs-right">{{ props.item.fat }}</td>
            <td class="text-xs-right">{{ props.item.carbs }}</td>
            <td class="text-xs-right">{{ props.item.protein }}</td>
            <td class="text-xs-right">{{ props.item.sodium }}</td>
            <td class="text-xs-right">{{ props.item.calcium }}</td>
            <td class="text-xs-right">

                <v-layout row justify-center>
                <v-dialog v-model="dialog" persistent max-width="600px"
                          lazy absolute>

                    <!--<v-btn primary dark slot="activator">Delete</v-btn>-->

                    <v-btn
                            slot="activator"
                            small
                            fab
                            color="success"
                    >
                        <v-icon>edit</v-icon>
                    </v-btn>


                    <v-card>
                        <v-card-title>
                            <span class="headline">{{ fname }} - Registration</span> 
                            <br>
                        </v-card-title>
                        <v-card-text>
                            <v-container grid-list-md>
                                <v-layout wrap>
                                    <v-flex xs12 sm6 md4>
                                        <v-text-field label="Legal first name*" required></v-text-field>
                                    </v-flex>
                                    <v-flex xs12 sm6 md4>
                                        <v-text-field label="Legal middle name" hint="example of helper text only on focus"></v-text-field>
                                    </v-flex>
                                    <v-flex xs12 sm6 md4>
                                        <v-text-field
                                                label="Legal last name*"
                                                hint="example of persistent helper text"
                                                persistent-hint
                                                required
                                        ></v-text-field>
                                    </v-flex>
                                    <v-flex xs12>
                                        <v-text-field label="Email*" required></v-text-field>
                                    </v-flex>
                                    <v-flex xs12>
                                        <v-text-field label="Password*" type="password" required></v-text-field>
                                    </v-flex>
                                    <v-flex xs12 sm6>
                                        <v-select
                                                :items="['0-17', '18-29', '30-54', '54+']"
                                                label="Age*"
                                                required
                                        ></v-select>
                                    </v-flex>
                                    <v-flex xs12 sm6>
                                        <v-autocomplete
                                                :items="['Skiing', 'Ice hockey', 'Soccer', 'Basketball', 'Hockey', 'Reading', 'Writing', 'Coding', 'Basejump']"
                                                label="Interests"
                                                multiple
                                        ></v-autocomplete>
                                    </v-flex>
                                </v-layout>
                            </v-container>
                            <small>*indicates required field</small>
                        </v-card-text>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn color="blue darken-1" flat @click="dialog = false">Close</v-btn>
                            <v-btn color="blue darken-1" flat @click="dialog = false">Save</v-btn>
                        </v-card-actions>
                    </v-card>

                </v-dialog>
                </v-layout>

            </td>
            </tr>
        </template>


    </v-data-table>

</div>

</template>
<script>
    export default {

        methods: {
            showAlert(a){
                //if (event.target.classList.contains('btn__content')) return;
                /*alert('Alert! \n' + a.name);*/

                this.selected.name = a.name;
                this.selected.cal = a.calories;
                this.selected.fat =  a.fat;
                this.fname = a.name

                console.log(this.selected.fat);
                console.log(this.fname);

            }
        },
        data () {
            return {
                fname: 'Test',
                selected:[],
                dialog: false,
                test: true,
                headers: [
                    {
                        text: 'Training Title',
                        align: 'left',
                        sortable: false,
                        value: 'name'
                    },
                    { text: 'Mentor', value: 'calories',sortable: false},
                    { text: 'Schedule', value: 'fat',sortable: false},
                    { text: '# of Registered Participants', value: 'carbs',sortable: false },
                    { text: 'Register', value: 'protein',sortable: false }
                    /*{ text: 'Iron (%)', value: 'iron',sortable: false }*/
                ],
                items: [
                    {
                        name: 'Frozen Yogurt',
                        calories: 'Johnvel Mike Amarisca',
                        fat: 'July 8',
                        carbs: 3,
                        protein: 4.0,
                        iron: '1%'
                    },
                    {
                        name: 'Ice cream sandwich',
                        calories: 237,
                        fat: 9.0,
                        carbs: 37,
                        protein: 4.3,
                        iron: '1%'
                    },
                    {
                        name: 'Eclair',
                        calories: 262,
                        fat: 16.0,
                        carbs: 23,
                        protein: 6.0,
                        iron: '7%'
                    },
                    {
                        name: 'Cupcake',
                        calories: 305,
                        fat: 3.7,
                        carbs: 67,
                        protein: 4.3,
                        iron: '8%'
                    },
                    {
                        name: 'Gingerbread',
                        calories: 356,
                        fat: 16.0,
                        carbs: 49,
                        protein: 3.9,
                        iron: '16%'
                    },
                    {
                        name: 'Jelly bean',
                        calories: 375,
                        fat: 0.0,
                        carbs: 94,
                        protein: 0.0,
                        iron: '0%'
                    },
                    {
                        name: 'Lollipop',
                        calories: 392,
                        fat: 0.2,
                        carbs: 98,
                        protein: 0,
                        iron: '2%'
                    },
                    {
                        name: 'Honeycomb',
                        calories: 408,
                        fat: 3.2,
                        carbs: 87,
                        protein: 6.5,
                        iron: '45%'
                    },
                    {
                        name: 'Donut',
                        calories: 452,
                        fat: 25.0,
                        carbs: 51,
                        protein: 4.9,
                        iron: '22%'
                    },
                    {
                        name: 'KitKat',
                        calories: 518,
                        fat: 26.0,
                        carbs: 65,
                        protein: 7,
                        iron: '6%'
                    }
                ]
            }
        }
    }
</script>
<template>
    <div id="app">
        <vue-bootstrap4-table :rows="rows" :columns="columns" :config="config">
        </vue-bootstrap4-table>
    </div>
</template>

<script>
    import VueBootstrap4Table from './components/VueBootstrap4Table.vue'

    export default {
        name: 'App',
        data: function() {
            return {
                rows: [],
                columns: [
                    {
                        label: "id",
                        name: "id",
                        filter: {
                            type: "simple",
                            placeholder: "id"
                        },
                        sort: true,
                        uniqueId: true
                    },
                    {
                        label: "First Name",
                        name: "name.first_name",
                        filter: {
                            type: "simple",
                            placeholder: "Enter first name"
                        },
                        sort: true,
                        // slot_name: "my_duplicate_id_column"
                    },
                    {
                        label: "Last Name",
                        name: "name.last_name",
                        filter: {
                            type: "simple",
                            placeholder: "Enter last name"
                        },
                        sort: true,
                    },
                    {
                        label: "Email",
                        name: "email",
                        filter: {
                            type: "simple",
                            placeholder: "Enter email"
                        },
                        sort: true,
                    },
                    {
                        label: "City",
                        name: "address.city",
                        sort: true,
                    },
                    {
                        label: "Country",
                        name: "address.country",
                        filter: {
                            type: "simple",
                            placeholder: "Enter country"
                        },
                    },
                ],
                config: {
                    pagination: true,
                    pagination_info: true,
                    num_of_visibile_pagination_buttons: 7,
                    per_page: 10,
                    checkbox_rows: true,
                    highlight_row_hover: true,
                    rows_selectable: true,
                    multi_column_sort: true,
                    // highlight_row_hover_color:"grey",
                    card_title: "Vue Bootsrap 4 advanced table"
                }
            }
        },
        components: {
            VueBootstrap4Table
        },
        mounted() {
            let self = this;
            axios.get('https://raw.githubusercontent.com/rubanraj54/vue-bootstrap4-table/develop/src/assets/toy_data/users_500.json')
                .then(function(response) {
                    // console.log(typeof response.data);

                    self.rows = response.data;
                })
                .catch(function(error) {
                    // handle error
                    console.log(error);
                });
        },
    }
</script>

<style>

</style>

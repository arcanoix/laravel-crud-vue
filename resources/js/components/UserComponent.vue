<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-12">
                <div class="card">
                    <div class="card-header">Usuarios</div>
                        <table>
                            <thead>
                                <th>Nombre</th>
                                <th>Email</th>
                            </thead>
                            <tbody>
                                <tr v-for="user in users" :key="user.id">
                                    <td>{{user.name}}</td>
                                    <td>{{user.email}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
    </div>
</template>

<script>
    export default {

        data() {
            return {
                users:[]
            }
    },

        created() {
                this.index();
        },

        methods: {
           async index() {
                   
                 await axios.get("/users")
                    .then((res) => {
                        console.log(res.data);
                        this.users = res.data;
                        
                    });
            }
        },

        mounted() {
            console.log('Component mounted.');
        }
    }
</script>
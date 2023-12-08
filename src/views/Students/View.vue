<template>
    <div>
        <div class="card">
            <div class="card-header">
                <h4>
                    Students
                </h4>

            </div>
            <div class="card-body">
                <table class="table table-bordered">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Name</th>
                            <th>Username</th>
                            <th>Email</th>
                            <th>Address</th>
                            <th>Phone Number</th>
                        </tr>
                    </thead>
                    <tbody v-if="this.students.length > 0">
                        <tr v-for="(student, index) in this.students" :key="index">
                            <td>{{ student.id }}</td>
                            <td>{{ student.name }}</td>
                            <td>{{ student.username }}</td>
                            <td>{{ student.email }}</td>
                            <td>{{ student.address.city }}</td>
                            <td>{{ student.phone }}</td>

                        </tr>
                    </tbody>
                    <tbody v-else>
                        <tr>
                            <td colspan="6">Loading Data ....</td>
                        </tr>
                    </tbody>


                </table>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'students',
    data(){
return {
    students:[]
}
    },
    mounted(){
        this.getStudents();
console.log('i am here')
    },
    methods:{
        getStudents(){
            axios.get('https://jsonplaceholder.typicode.com/users').then(res => {
                this.students = res.data
                console.log(res)

            })
        }

    },
}
</script>
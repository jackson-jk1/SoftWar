<template>
    <div  class="table-responsive">
        <table class="table table-dark dataTable dtr-inline" cellspacing="0" width="100%" role="grid" aria-describedby="example_info" style="width: 100%;table-layout:fixed">
            <thead>
            <tr>
                <th scope="col">#</th>
                <th scope="col">Nome</th>
                <th scope="col">Email</th>
                <th scope="col">Maior de 18</th>
                <th scope="col">Tipo Sanguineo</th>
                <th scope="col">Comentarios</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="(user,i) in users">
                <th scope="row">{{i}}</th>
                <td>{{user.name}}</td>
                <td>{{user.email}}</td>
                <td v-if="user.older == true">Sim</td>
                <td v-if="user.older == false">Nao</td>
                <td><p>{{user.blood}}</p></td>
                <td><p>{{user.comments}}</p></td>
            </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    data: () => ({
     users:{}
    }),
   mounted() {
       axios.get('api/users').then((res) =>{
           this.users = res.data.users;
           }
       );
   }
}
</script>
<style>
#table{
    overflow-x: hidden;
}
td{
    word-wrap:break-word;
}
</style>

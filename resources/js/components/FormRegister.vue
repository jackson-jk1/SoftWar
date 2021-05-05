<template>
<div>
<div class="row justify-content-center">
    <div class="col-md-8">
        <div class="card">
            <div class="card-header">Register</div>

            <div class="card-body">
                <form>

                    <div class="form-group row">
                        <label for="name" class="col-md-4 col-form-label text-md-right">Name</label>

                        <div class="col-md-6">
                            <input id="name" type="text" class="form-control" v-model="user.name" autofocus>

                        </div>
                    </div>

                    <div class="form-group row">
                        <label for="email" class="col-md-4 col-form-label text-md-right">E-Mail Address</label>

                        <div class="col-md-6">
                            <input id="email" type="email" class="form-control" v-model="user.email" >

                        </div>
                    </div>

                    <div class="form-group row">
                        <label for="password" class="col-md-4 col-form-label text-md-right">Password</label>

                        <div class="col-md-6">
                            <input id="password" type="password" class="form-control" v-model="user.password">
                        </div>
                    </div>
                    <div class="form-group row">
                        <label for="password-confirm" class="col-md-4 col-form-label text-md-right">Password Confirm</label>
                        <div class="col-md-6">
                            <input id="password-confirm" type="password"  class="form-control"  v-model="user.password_confirmation">
                        </div>
                    </div>


                    <div class="form-group">
                        <div class="col-md-6 offset-md-4">
                            <label for="bloodtype">Blood Type</label>
                            <select class="form-control" id="bloodtype" v-model="user.blood">
                                <option selected >Tipo Sanguineo</option>
                                <option v-for="blod in blodType" :value="blod.type">{{blod.type}}</option>
                            </select>
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-6 offset-md-4">
                            <p>Maior de idade?</p>
                            <div class="form-check form-check-inline">
                                <input class="form-check-input"  type="radio" id="Yes" :value="true" v-model="user.older">
                                <label class="form-check-label" for="Yes" >Sim</label>
                            </div>
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" id="No" :value="false" v-model="user.older">
                                <label class="form-check-label" for="No" >Não</label>
                            </div>
                        </div>
                    </div>

                    <div class="form-group">
                        <div class="col-md-6 offset-md-4">
                            <label for="comments">Comments</label>
                            <textarea class="form-control" id="comments" rows="3" v-model="user.comments"></textarea>
                        </div>
                    </div>
                    <div class="form-group row mb-0">
                        <div class="col-md-6 offset-md-4">
                            <button @click="insert(user)" class="btn btn-primary">
                                Register
                            </button>
                        </div>
                    </div>
                    {{user}}
                </form>
            </div>
        </div>
    </div>
 </div>
</div>
</template>

<script>
export default {
    data: () => ({
        user:{
            name:'',
            email:'',
            password:'',
            password_confirmation:'',
            blood:'',
            older:'',
            comments:''

        },
        blodType: [
            { type: 'A+'},
            { type:'A-'},
            { type:'B+'},
            { type:'B-'},
            { type:'AB+'},
            { type:'AB-'},
            { type:'O+'},
            { type:'O-'}
        ],

    }),
   methods: {
        insert(user){
            if (!user.name||!user.email||!user.password||!user.blood||!user.older||!user.comments||!user.password_confirmation){
                return
            }
            axios.post('register',user);
       },
   }

}
</script>

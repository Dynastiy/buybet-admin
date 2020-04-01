<template>
    <div id="login" class="text-center">
        <h1 style="color:#ffb20f">Login</h1>
        <div class="mt-5">
            <input type="text" name="username" v-model="input.username" placeholder="Username" />
        </div>
        <div class="mt-4">
        <input type="password" name="password" v-model="input.password" placeholder="Password" />
        </div>
        <div class="mt-4">
        <button type="button" class="button" v-on:click="login()">Login</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Login',
        data() {
            return {
                input: {
                    username: "",
                    password: ""
                }
            }
        },
        methods: {
            login() {
                if(this.input.username != "" && this.input.password != "") {
                    if(this.input.username == this.$parent.mockAccount.username && this.input.password == this.$parent.mockAccount.password) {
                        this.$emit("authenticated", true);
                        this.$router.replace({ name: "secure" });
                    } else {
                        alert("The username and / or password is incorrect");
                    }
                } else {
                    alert("A username and password must be present");
                }
            }
        }
    }
</script>

<style scoped>
    #login {
        width: 500px;
        margin-left:15% ;
        margin-top: 100px;
        padding: 1.2rem;
    }
    input {
    width: 80% !important;
    padding: 0.5rem !important ;
  }
  .button {
    background-color: #ffb20f !important;
    color: #000;
    border-radius: 1rem !important;
    border: none;
    padding: 0.2rem 2rem;
    font-size: 1rem;
    font-weight: bold;
  }
</style>
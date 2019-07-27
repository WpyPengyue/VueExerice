<template>
    <div>
        <form v-if="!isReg">
            <div>Login</div>
            name:<input type="text" name="name" v-model="name"><br>
            password:<input type="password" name="password" v-model="password"><br>
            <button type="button" @click="login()">登录</button>
            <button type="button" @click="reg()">注册</button>
        </form>
        <form v-else>
            <div>Register</div>
            name:<input type="text" name="name" v-model="name"><br>
            password:<input type="password" name="password" v-model="password"><br>
            repeat:<input type="password" name="repeat" v-model="repeat"><br>
            <button type="button" @click="confirmReg()">确认</button>
            <button type="button" @click="cancel()">取消</button>
        </form>
    </div>

</template>
<script>
export default {
    name: 'Login',
    data: function(){
        return {
            isReg: false,
            name: '',
            password: '',
            repeat: ''
        }
    },
    methods: {
        login() {
            if(localStorage.getItem('name') === this.name && localStorage.getItem('password') === this.password){
                this.name = '';
                this.password = '';
                this.$router.push('/home/list');
            }else{
                alert('账号或密码错误');
            }
        },
        reg() {
            this.name = '';
            this.password = '';
            this.isReg = true;
        },
        confirmReg() {
            if(this.password === this.repeat){
                localStorage.setItem('name', this.name);
                localStorage.setItem('password', this.password);
                this.name = '';
                this.password = '';
                this.repeat = '';
                this.isReg = false;
            }else{
                alert('两次密码不一致');
            }
        },
        cancel() {
            this.name = '';
            this.password = '';
            this.repeat = '';
            this.isReg = false;
        }
    }
}  
</script>

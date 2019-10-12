<template>
    <div class="login">
        <!--<b-jumbotron  header="VueJS + ChatKit App"-->
                      <!--lead="By: Hamza Arshad"-->
                      <!--bg-variant="info"-->
                      <!--text-variant="white">-->
            <!--<p>More projects found at my </p>-->
            <!--<b-btn target="_blank" href="https://www.hamzaarshad.com">website.</b-btn>-->
        <!--</b-jumbotron>-->
        <div class="login-container">
            <div class="login-box">
                <div class="login-title" href="#">VUECHAT</div>
                <div class="login-subtext">A Chat Application Made with Vue.js and Chatkit.</div>
                <LoginForm />
            </div>
        </div>
        <vue-particles
                class="particles-js"
                color="#dedede"
                :particleOpacity="0.7"
                :particlesNumber="80"
                shapeType="circle"
                :particleSize="4"
                linesColor="#dedede"
                :linesWidth="1"
                :lineLinked="true"
                :lineOpacity="0.4"
                :linesDistance="150"
                :moveSpeed="3"
                :hoverEffect="true"
                hoverMode="grab"
                :clickEffect="true"
                clickMode="push"
        >
        </vue-particles>

        <!--<b-container>-->
            <!--<b-row>-->
                <!--<b-col lg="4" md="3"></b-col>-->
                <!--<b-col lg="4" md="6">-->
                    <!--<LoginForm />-->
                <!--</b-col>-->
                <!--<b-col lg="4" md="3"></b-col>-->
            <!--</b-row>-->
        <!--</b-container>-->
    </div>
</template>

<script>
    import LoginForm from '../components/LoginForm.vue'

    export default {
        name: 'login',
        components: {
            LoginForm
        }
    }
</script>
<style>
    .particles-js {
        background: url("../assets/grey-background-06.jpg");
        background-size: cover;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }
    .login-container{
        position: absolute;
        z-index: 999;
        width: 100%;
        height: 100%;
    }
    .login-box{
        width: 500px;
        height: 300px;
        background: #333;
        margin: auto;
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        box-shadow: 0 0 8px #000;
    }
    .login-title{
        font-family: 'Fjalla One', sans-serif;
        color: #d0d0d0;
        font-size: 40px;
        margin: 0 auto;
        text-align: center;
        margin-top: 30px;
    }
    .login-subtext{
        font-family: Montserrat, sans-serif;
        color: #d0d0d0;
        text-align: center;
    }
</style>
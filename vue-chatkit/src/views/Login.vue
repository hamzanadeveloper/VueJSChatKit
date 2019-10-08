<template>
    <div class="login">
        <b-jumbotron  header="VueJS + ChatKit App"
                      lead="By: Hamza Arshad"
                      bg-variant="info"
                      text-variant="white">
            <p>More projects found at my </p>
            <b-btn target="_blank" href="https://www.hamzaarshad.com">website.</b-btn>
        </b-jumbotron>
        <b-container>
            <b-row>
                <b-col lg="4" md="3"></b-col>
                <b-col lg="4" md="6">
                    <LoginForm />
                </b-col>
                <b-col lg="4" md="3"></b-col>
            </b-row>
        </b-container>
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
<template>
    <div class="user-list">
        <span class="channel-header">MEMBERS</span>
        <hr>
        <b-list-group>
            <b-list-group-item style="background: rgb(53,56,58);color: #d0d0d0;border:none;" class="user-container" v-for="user in users" :key="user.username">
                <b-badge v-if="user.presence"
                         :variant="statusColor(user.presence)"
                         style="height: 13px;width: 12px;margin-right:5px;"
                         pill>
                    &nbsp;</b-badge>
                {{ user.name }}

            </b-list-group-item>
        </b-list-group>
    </div>
</template>

<script>
    import { mapState } from 'vuex'

    export default {
        name: 'user-list',
        computed: {
            ...mapState([
                'loading',
                'users'
            ])
        },
        methods: {
            statusColor(status) {
                return status === 'online' ? 'success' : 'warning'
            }
        }
    }
</script>
<style>
    @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Montserrat&display=swap');

    .channel-header{
        font-family: 'Fjalla One', sans-serif;
        color: #d0d0d0;
        font-size: 17px;
    }
    .user-container{
        font-family: Montserrat, sans-serif;
        font-size: 11px;
        padding: 8px;
        cursor: pointer;
        margin-left: -10px;
        white-space: nowrap;
        margin-right: -9px;
        border-radius: 5px;
    }
    .channel-container:active{
        background-color: #565656;
    }
</style>
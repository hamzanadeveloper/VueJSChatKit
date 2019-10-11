<template>
    <div class="room-list">
        <span class="channel-header">CHANNELS</span>
        <hr>
        <b-list-group v-if="activeRoom">
            <b-list-group-item style="background: rgb(53,56,58);color: #d0d0d0;border:none;" class="channel-container" v-for="room in rooms"
                               :key="room.name"
                               :active="activeRoom.id === room.id"
                               href="#"
                               @click="onChange(room)">
                # {{ room.name }}
                </b-list-group-item>
        </b-list-group>
    </div>
</template>

<script>
    import { mapState, mapActions } from 'vuex'

    export default {
        name: 'RoomList',
        computed: {
            ...mapState([
                'rooms',
                'activeRoom'
            ]),
        },
        methods: {
            ...mapActions([
                'changeRoom'
            ]),
            onChange(room) {
                this.changeRoom(room.id)
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
    .channel-container{
        font-family: Montserrat, sans-serif;
        font-size: 15px;
        padding: 8px;
        cursor: pointer;
        margin-left: -10px;
        margin-right: -9px;
        border-radius: 5px;
    }
    .channel-container:active{
        background-color: #565656;
    }
</style>
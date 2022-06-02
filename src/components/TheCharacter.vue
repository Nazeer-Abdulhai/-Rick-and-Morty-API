<template>
    <div class="main">
        <!-- All 3 forms -->
        <div class="forms">
            <!-- name and mood form  -->
            <form @submit.prevent="nameMoodRender">
                <h2 class="title">Find the character</h2>
                    <label for="">By Name</label>
                    <input type="text"  v-model="name">

                    <!-- Search for Name or by a selected mood -->
                    <label>choose alive or dead Characters</label>
                    <select v-model="role">
                        <option value="Alive">Alive</option>
                        <option value="Dead">Dead</option>
                    </select>
                    <button class="btn">Show</button>
            </form>
            <!-- Episode form -->
            <form @submit.prevent="callEpisode">
                <h2 class="title">Find the character</h2>
                    <label for="">By episode</label>
                    <input type="text"  v-model="episode">
                    <button class="btn show-margin-top">Show</button>
            </form>
            <!-- location form -->
            <form action="" @submit.prevent="callLocation">
                <h2 class="title">Find the character</h2>
                <label for="">By Location</label>
                <input type="text"  v-model="location">
                <button class="btn show-margin-top">Show</button>
            </form>
        </div>


        <!-- Displaying the characters -->

        <div class="container">


                <!-- NameMood Display -->
            <div class="card list" style="width: 18rem;" v-for="item in TheNameMoodList" :key="item.id" >
                <h2 class="card-title">{{ item.name}}</h2>
                <img :src="item.image" class="card-img-top" alt="...">
                <div class="card-body">
                    <p class="card-text">Gender: {{item.gender}}</p>
                    <p class="card-text">Specie: {{item.species}}</p>
                </div>
            </div>

            <!-- Episode display -->
            <div class="card list" style="width: 18rem;" v-for="item in episodeList" :key="item.id" >
                <h2 class="card-title">{{ item.name}}</h2>
                <img :src="item.image" class="card-img-top" alt="...">

                <div class="card-body" v-html="characterEpisode(item.characters)">
                </div>
            </div>

            <!-- Search By location -->
                <div class="card list" style="width: 18rem;" v-for="item in LocationList" :key="item.id" >
                    <h2 class="card-title">{{ item.name}}</h2>
                    <img :src="item.image" class="card-img-top" alt="...">

                <div class="card-body" v-html="characterLocation(item.location)">
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    
    name: 'TheUser',

    data(){
        return {
            TheNameMoodList: null,
            episodeList: null,
            LocationList: null,
             name: '',
             location: '',
             type: '',
             role: '',
             episode: ''

        };
    },

    methods: {
        nameMoodRender(){
        this.apiCall();
        },

        apiCall(){
        axios({
            method: 'get',
            url: 'https://rickandmortyapi.com/api/character',
            params: {
             name: this.name,
             location: this.location,
             episode: this.episode,
             status: this.role
            },
        }).then(res => 
        {
            this.TheNameMoodList = res.data.results
        }).catch('No result')
        },

        callEpisode(){
            axios({
            method: 'get',
            url: 'https://rickandmortyapi.com/api/episode',
            params: {
            name: this.episode,
            },
        }).then(res => 
        {
            this.episodeList = res.data.results
        }).catch('No Episode has been found')
        },

        characterEpisode(list){
            let result = '';
            list.forEach(char => {
                 axios({
            method: 'get',
            url: char,
            }).then(res =>
            
            
            {
                result= "<div>"+res.data.name+"</div>";
            }).catch('No result')
            })
            return result;
        },

        callLocation(){
            axios({
            method: 'get',
            url: 'https://rickandmortyapi.com/api/location',
            params: {
            name: this.location,
            },
        }).then(res => 
        {
            this.LocationList = res.data.results
        }).catch('No Location has been found')
        },


        characterLocation(x){
            let result = '';
            x.forEach(loc => {
            axios({
            method: 'get',
            url: loc,
            }).then(res =>
            {
                result = "<div>"+res.data.name+"</div>";
            }).catch('No result')
            })
            return result;
        },



        
    }
}
</script>


<style scoped>
.main{
    margin-top: 15rem;
}

.forms{
    display: flex;
}
.container{
    justify-content: space-between;
    
}
.list{
    display: inline-flex;
    margin: 10px;
    box-shadow: rgba(251, 251, 251, 0.2) 0px 7px 29px 0px;
}

.list:hover{
    transform: translateY(-1.5rem) scale(1.03);
}

form {
    max-width: 400px;
    margin: 30px auto;
    background: white;
    text-align: center;
    padding: 23px;
    border-radius: 10px;
    box-shadow: rgba(255, 255, 255, 0.2) 0px 7px 29px 0px;
    
}

label{
    color: #aaa;
    display: inline-block;
    margin: 15px 0 0;
    font-size: 1em;
    letter-spacing: 1px;
    font-weight: bold;
}

input,select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}

button{
    background: white;
    margin-top: 2rem;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;

}

button:hover{
    transform: translateY(-3px);
}

.show-margin-top{
    margin-top: 110px;
}
</style>
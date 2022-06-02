<template>
    <div class="main">
        <form @submit.prevent="submitting">
        <h2 class="title">Search for an character</h2>
            <label for="">Give dimension</label>
            <input type="text"  v-model="dimension">

            <label for="">Or location</label>
            <input type="text"  v-model="location">

            <label for="">Or episode</label>
            <input type="text"  v-model="episode">

            <label>choose alive or dead Characters</label>
            <select v-model="role">
                <option value="Alive">Alive</option>
                <option value="Dead">Dead</option>
            </select>
            <button class="btn">Show me the Characters</button>
        </form>
            <div class="container">
                <div class="card list" style="width: 18rem;" v-for="item in Thelist" :key="item.id" >
                    <h2 class="card-title">{{ item.name}}</h2>
                    <img :src="item.image" class="card-img-top" alt="...">
                    <div class="card-body">
                            <p class="card-text">Gender: {{item.gender}}</p>
                        <p class="card-text">Specie: {{item.species}}</p>
                        <!-- <p class="card-text">{{ item.episode[0]}}</p> -->
                        <!-- <p class="card-text">{{ item.type}}</p> -->
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
            Thelist: null,
            dimension: '',
             location: '',
             episode: '',
             role: '',
        };
    },

    // created: function() {
    //     this.apiCall();
    // },

    methods: {
        submitting(){
        this.apiCall();
        },

        apiCall(){
        // axios.get("https://rickandmortyapi.com/api/character?status="+ this.dimension)
        // .then(res => {this.Thelist = res.data.results;
        // console.log(res);
        // }).catch ('no result has been found')
        axios({
            method: 'get',
            url: 'https://rickandmortyapi.com/api/character',
            params: {
            //  status: this.dimension,
            //  status: this.location,
            //  status: this.episode,
             status: this.role
            },
        }).then(res => 
        {
            this.Thelist = res.data.results
        }).catch('No result')
        },
    }
}
</script>


<style scoped>
.main{
    margin-top: 15rem;
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
    max-width: 700px;
    margin: 30px auto;
    background: white;
    text-align: center;
    padding: 40px;
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
</style>
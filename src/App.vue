<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>
<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
const API_KEY = 'AIzaSyCQRU_UlnwybAt9SNj2X2oyabi903WsOog';


export default {
    name: 'App',
    components:{
        SearchBar
    },
    methods:{
        onTermChange(searchTerm){
            axios.get('https://www.googleapis.com/youtube/v3/search',{
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => console.log(response));
        }
    }
}
</script>

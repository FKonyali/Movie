<template>
    <div class="home">
        <PageHeader/>
        <div class="text-center mt-20" v-if="movies == ''">
            Yükleniyor...
        </div>
        <div class="movie-boxes container">
            <ListMovieBox :movies="movies"/>
            <ListMovieBox :movies="moreMovieItems"/>
            <div class="text-center">
                <button class="box__btn" v-on:click="dataMore">
                    {{moreNewsLoading}}
                </button>
            </div>
        </div>
        <PageFooter/>
    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader'
import ListMovieBox from'@/components/ListMovieBox'
import PageFooter from'@/components/PageFooter'

export default {
    name: 'Home',
    components: {
        PageHeader,
        ListMovieBox,
        PageFooter
    },
    data() {
        return {
            movies: '',
            pagination: 1,
            moreMovieItems: [],
            moreNewsLoading: 'Daha fazla görüntüle (+10)',
            test: this.getCookie('test') || 0
        }
    },
    computed: {
        userInfo: function() {
            this.setCookie('test', this.test);
            return this.test
        }
    },
    watch: {
        userInfo: function (newVal) {
            console.log(newVal)
        }
    },
    created() {
        this.test++;
        fetch('http://www.omdbapi.com/?apikey=ceb2ae86&s=movie')
            .then(data => data.json())
            .then(json => {
                this.movies = json.Search;
            });
    },
    methods: {
        dataMore: function() {
            this.moreNewsLoading = 'Yükleniyor...';
            this.pagination++;
            fetch('http://www.omdbapi.com/?apikey=ceb2ae86&s=movie&page=' + this.pagination)
                .then(data => data.json())
                .then(json => {
                    this.moreMovieItems = [...this.moreMovieItems, ...json.Search];
                    this.moreNewsLoading = 'Daha fazla görüntüle (+10)'
                });
        },
        setCookie: function(cname, cvalue, exdays) {
            var d = new Date();
            d.setTime(d.getTime() + (exdays*24*60*60*1000));
            var expires = "expires="+ d.toUTCString();
            document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
        },
        getCookie: function(cname) {
            var name = cname + "=";
            var decodedCookie = decodeURIComponent(document.cookie);
            var ca = decodedCookie.split(';');
            for(var i = 0; i <ca.length; i++) {
                var c = ca[i];
                while (c.charAt(0) == ' ') {
                c = c.substring(1);
                }
                if (c.indexOf(name) == 0) {
                return c.substring(name.length, c.length);
                }
            }
            return "";
        }
    }
}
</script>

<style lang="sass">
    .movie-boxes
        .box
            &:nth-child(even)
                background: #e3e3e3
    
    .mt-20
        margin-bottom: 20px
    
</style>
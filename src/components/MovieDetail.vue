<template>
    <div class="container">
        <div class="text-center" v-if="loading">
            Yükleniyor...
        </div>
        <article class="content" v-if="loading == false">
            <div class="content__info">
                <ul>
                    <li>
                        <span>Imdb Puanı:</span> {{movie.imdbRating}}
                    </li>
                    <li>
                        <span>Vizyon Yılı:</span> {{movie.Year}}
                    </li>
                    <li>
                        <span>Film Süresi:</span> {{movie.Runtime}}
                    </li>
                    <li>
                        <span>Kategori:</span> {{movie.Genre}}
                    </li>
                    <li>
                        <span>Yönetmen:</span> {{movie.Director}}
                    </li>
                    <li>
                        <span>Yazar:</span> {{movie.Writer}}
                    </li>
                    <li>
                        <span>Aktörler:</span> {{movie.Actors}}
                    </li>
                    <li>
                        <span>Dil:</span> {{movie.Language}}
                    </li>
                    <li>
                        <span>Yapım:</span> {{movie.Country}}
                    </li>
                </ul>
            </div>
            <div class="content__poster">
                <img :src="movie.Poster" :alt="movie.Title">
            </div>
        </article>
    </div>
</template>

<script>
export default {
    name: 'MovieDetail',
    props: ['imdbID'],
    data () {
        return {
            movie: '',
            loading: true
        }
    },
    created() {
        fetch('http://www.omdbapi.com/?apikey=ceb2ae86&i=' + this.imdbID)
            .then(data => data.json())
            .then(json => {
                this.loading = false;
                this.movie = json;
            });
    }
}
</script>

<style lang="sass">
    $font2: 'Myriad Pro'

    .content
        display: flex
        justify-content: space-between
        padding: 0 21px 0 44px
        font-family: $font2

        &__info
            padding-right: 30px
            color: #636363
            font-size: 18px
            flex: 1

            span
                font-weight: 700

            li
                font-weight: 400
                margin-bottom: 5px

    ul
        list-style: none

    @media (max-width: 600px)
        .content
            flex-wrap: wrap

            &__info
                order: 1
                margin-top: 15px
                flex: none
                width: 100%
</style>
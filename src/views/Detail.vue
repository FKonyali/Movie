<template>
    <div class="detail">
        <PageHeader/>
            <div class="container">
                <MovieDetail :imdbID="imdbID"/>
            </div>
        <PageFooter/>
    </div>
</template>

<script>
import PageHeader from '@/components/PageHeader'
import MovieDetail from '@/components/MovieDetail'
import PageFooter from'@/components/PageFooter'

export default {
    name: 'Home',
    components: {
        PageHeader,
        MovieDetail,
        PageFooter
    },
    data() {
        return {
            imdbID: this.$route.params.id
        }
    }
}
</script>
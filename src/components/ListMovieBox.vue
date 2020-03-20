<template>
    <div>
        <router-link :to="item.imdbID" class="box" v-for="item in movies" :key="item.id">
            <div class="box__top">
                <div class="box__mtitle">
                    {{item.Title}} ({{item.Year}})
                </div>
                <div class="box__mpoint">
                    <span class="box__ptext">Puan</span> <span class="box__pnumber">{{parseInt(Math.random() * 5 + 5)}}</span>
                </div>
            </div>
            <div class="box__bot">
                <div class="box__poster">
                    <img :src="item.Poster" :alt="item.Title">
                </div>
                <div class="box__detail">
                    <div class="box__p">
                        <p>
                            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce dictum varius ultricies. Ut malesuada lobortis hendrerit. Aenean tincidunt cursus orci in auctor. 
                        </p>
                    </div>
                    <div class="box__btn">
                        DETAY
                    </div>
                </div>
            </div>
        </router-link>
    </div>
</template>

<script>
export default {
    name: 'ListMovieBox',
    props: ['movies']
}
</script>

<style lang="sass">
    $font: 'Open Sans'
    $font2: 'Myriad Pro'

    .text-center
        text-align: center
    
    .box
        background: #FFF
        display: block
        padding: 15px 14px 10px 32px
        max-width: 100%
        width: 913px
        margin: 0 auto 16px auto

        &__top
            display: flex
            justify-content: space-between
            margin-bottom: 27px

        &__mtitle
            font: 700 20px $font
            color: #636363

        &__mpoint
            font: 700 20px $font
            color: #ec561b

        &__bot
            display: flex
            justify-content: space-between
            flex-wrap: wrap

        &__poster
            width: 92px
            height: 92px
            background: #a1a1a1
            margin-right: 91px
            margin-bottom: 37px

            img
                width: 100%
                height: 100%
                object-fit: cover

        &__detail
            display: flex
            justify-content: space-between
            flex: 1
            flex-wrap: wrap

        &__p
            font: 400 18px $font2
            color: #636363
            max-width: 100%
            width: 345px

        &__ptext
            &:after
                content: ':'

        &__btn
            background: #376fe1
            padding: 13px 88px 12px 70px
            border-radius: 10px
            text-transform: uppercase
            color: #FFF
            font: 700 16px/18px $font
            display: inline-block
            align-self: flex-end
            border: 0
            cursor: pointer
    
    @media (max-width: 600px)
        .box
            &__bot
                justify-content: space-between

            &__poster
                margin-right: 47px

            &__p
                width: 100%
                font-size: 14px
                margin-bottom: 10px

            &__mpoint
                font-family: $font2
                font-size: 12px
                display: flex
                flex-direction: column-reverse
                align-items: center

            &__pnumber
                font-size: 16px

            &__ptext
                &:after
                    display: none

            &__btn
                padding: 13px 30px

</style>
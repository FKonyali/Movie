<template>
    <header class="header">
        <div class="header__container">
            <h1 class="header__title header--maxwidth">
                Lorem Ipsum <br>
                Dolor sit amet consectetur..
            </h1>
            <div class="header__desc header--maxwidth">
                <p>
                    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor. 
                </p>
            </div>
            <div class="header__img">
                <img alt="Movie" src="../assets/img/header-img.png">
            </div>
            <a href="#" class="header__btn">
                CTA BUTTON
            </a>
        </div>
    </header>
</template>

<script>
export default {
    
}
</script>

<style lang="sass">
    $font: 'Open Sans'
    $font2: 'Myriad Pro'

    .header
        background: #9d5c5c url('../assets/img/header-bg.png') center
        position: relative
        margin-bottom: 30px
        background-size: 100%

        &:before
            content: ''
            position: absolute
            top: 0
            left: 0
            right: 0
            bottom: 0
            background: rgba(0,0,0,.13)

        &__container
            position: relative
            width: 1250px
            max-width: 100%
            padding: 50px 21px
            margin: 0 auto

        &__title
            font: 700 36px $font
            color: #121212
            margin-bottom: 38px

        &__desc
            font: 600 24px $font
            margin-bottom: 24px
            color: #070707

        &__img
            position: absolute
            right: 21px
            bottom: 0

            img
                width: 100%

        &__btn
            background: #376fe1
            font: 700 18px $font
            color: #FFF
            text-transform: uppercase
            display: inline-block
            padding: 17px 120px
            border-radius: 5px
            text-align: center
            cursor: pointer

        &--maxwidth
            max-width: 100%
            width: 510px

    @media (max-width: 850px)
        .header
            background: #ebebeb

            &__title
                font-size: 24px
                margin-bottom: 20px

            &__desc
                font-size: 16px

            &__btn
                padding: 13px 80px

            &--maxwidth
                width: 400px

            &__img
                width: 200px

    @media (max-width: 660px)
        .header
            &--maxwidth
                width: 300px

    @media (max-width: 600px)
        .header
            &__container
                align-items: center
                display: flex
                flex-direction: column
                padding: 28px 10px

            &__img
                position: relative
                width: 171px
                max-width: 100%

            &--maxwidth
                width: 100%
                text-align: center

            &__title
                margin-bottom: 5px

            &__desc
                margin-bottom: 5px

            &__btn
                width: 100%

</style>
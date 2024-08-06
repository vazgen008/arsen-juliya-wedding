<template>

  <div class="dresscode">
    <div>
        <!-- <img src="./img/dresscodeAM.png" alt="" v-if="this.$i18n.locale === 'am'"> -->
        <img src="./img/dresscodeEN.png" >
    </div>
    <div class="dresscode__text">
        <p>{{$t('dresscodeText')}}</p>
    </div>
    <div class="dresscode__colors">
        <div class="dresscode__colors--green">

        </div>
        <div class="dresscode__colors--lightgreen">

        </div>
        <div class="dresscode__colors--brown">

        </div>
        <div class="dresscode__colors--pink">

        </div>
        <div class="dresscode__colors--lightpink">

        </div>
        <div class="dresscode__colors--darkblue">

        </div>
        <div class="dresscode__colors--lightblue">

        </div>
        <div class="dresscode__colors--gray">

        </div>
    </div>
    <div class="dresscode__examples">
        <div>
            <img src="./img/dresscode5.jpg" alt="">
        </div>
        <div>
            <img src="./img/dresscode4.jpg" alt="">
        </div>
        <div>
            <img src="./img/dresscode3.jpg"  alt="">
        </div>
        <div>
            <img src="./img/dresscode2.jpg"  alt="">
        </div>
        <div>
            <img src="./img/dresscode12.jpg" alt="">
        </div>
        <div>
            <img src="./img/dresscode7.jpg" alt="">
        </div>
        <div>
            <img src="./img/dresscode8.jpg" alt="">
        </div>
        <div>
            <img src="./img/dresscode10.jpg" alt="">
        </div>
        <div>
            <img src="./img/dresscode13.jpg" alt="">

        </div>
        <div>
            <img src="./img/dresscode11.jpg" alt="">
        </div>
    </div>
  </div>
</template>

<script setup>

</script>

<style scoped lang="scss">
.dresscode{
    &>div:first-child img{
        width: 290px;
        height: 40px;
        font-family: serif;
    }
        display: flex;
    margin-top: 100px;
    flex-direction: column;
    align-items: center;
        row-gap: 50px;
    &__text{
        width: 568px;
        height: 180px;
        background: rgba($color: white, $alpha: 0.3);
        padding: 30px;
        font-size: 20px;
        box-sizing: border-box;
        border-radius: 8px;
    }
    
    &__colors{
        & img{
            width: 305px;
            height: 55px;
        }
        display: flex;
        column-gap: 20px;
        & div{
            width: 50px;
            height: 50px;
            border-radius: 50%;
        }
        &--green{
            background: #636653;
        }
        &--lightgreen{
            background: #8D8E7E;
        }
        &--brown{
            background: #B08A81;
        }
        &--pink{
            background: #EFBFBB;
        }
        &--lightpink{
            background: #FEE4E3;
        }
        &--darkblue{
            background: #173182;
        }
        &--lightblue{
            background: #c9e1fb;
        }
        &--gray{
            background: #9096a4;
        }
    }
    &__examples{
        display: grid;
    /* grid-auto-rows: auto auto; */
    /* grid-auto-columns: auto auto auto auto auto auto; */
    grid-template-rows: auto auto;
    grid-template-columns: auto auto auto auto auto;
    row-gap: 20px;
    column-gap: 30px;
    align-items: flex-end;

        & img{
            height: 218px;
            width: 150px;
        }
    }
}
@media only screen and (min-width: 375px) and (max-width: 600px) {
    .dresscode__text {
        width: 300px;
        height: 180px;
        background: rgba(255, 255, 255, 0.3);
        font-size: 18px;
        box-sizing: border-box;
        display: flex;
        align-items: center;
        border-radius: 8px;
        padding: 20px;
        line-height: 1.5;
    }
    .dresscode__examples {
        display: grid;
        row-gap: 30px;
        grid-template-columns: auto auto;
        align-items: flex-end;
        flex-direction: column;
        
        &>div>img{
            width: 150px;
            height: 240px;
        }
    }
    .dresscode__colors{
        display: grid;
        grid-template-rows: auto auto;
        grid-template-columns: auto auto auto auto auto;
    }
}
</style>
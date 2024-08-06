<template>
<div id="wedding__main" class="wedding__main">
    <div class="wedding__main--entry">
        <p>{{$t('invitationText')}}</p>
    </div>
    <div class="wedding__main--date">
        <img src="./img/date.png" alt="">
    </div>
    <div class="wedding__main--party party">
        <img src="https://optim.tildacdn.one/tild3038-3065-4637-b133-336233373764/-/cover/600x600/center/center/-/format/webp/handisutyun2.png" alt="axnax">
        <div class="party__info">
            <div class="party__info--title">
                {{$t('weddingParty.title')}}
            </div>
            <div class="party__info--time">
                {{$t('weddingParty.time')}}
            </div>
            <div class="party__info--place">
                {{$t('weddingParty.place')}}
            </div>
            <div class="party__info--city">
                {{$t('weddingParty.city')}}
            </div>
            <div class="party__info--action">
               <a href="https://yandex.ru/maps/-/CDcAYSYm" ><button v-if="showPartyButton" :class="{ visible: showPartyButton }" class="ceremony--action">{{$t('weddingParty.buttonText')}}</button></a> 
            </div>
        </div>
    </div>
</div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from "vue";


const showCeremonyButton = ref(false);
const ceremonyButtonAlreadyVisible = ref(false);

const ceremonyButtonScroll = () => {
  const mainInfo = document.getElementsByClassName('wedding__main--party')[0];
  const rect = mainInfo.getBoundingClientRect();
  const windowHeight = window.innerHeight || document.documentElement.clientHeight;

  // Check if the bottom of the element is in view
  if (rect.bottom <= windowHeight) {
    showCeremonyButton.value = true;
    ceremonyButtonAlreadyVisible.value = true;
  } else if (ceremonyButtonAlreadyVisible.value) {
    showCeremonyButton.value = true;
  } else {
    showCeremonyButton.value = false;
  }
};

const showPartyButton = ref(false);
const partyButtonAlreadyVisible = ref(false);

const partyButtonScroll = () => {
  const mainInfo = document.getElementsByClassName('party__info')[0];
  const rect = mainInfo.getBoundingClientRect();
  const windowHeight = window.innerHeight || document.documentElement.clientHeight;

  // Check if the bottom of the element is in view
  if (rect.bottom <= windowHeight) {
    showPartyButton.value = true;
    partyButtonAlreadyVisible.value = true;
  } else if (ceremonyButtonAlreadyVisible.value) {
    showPartyButton.value = true;
  } else {
    showPartyButton.value = false;
  }
};

onMounted(() => {
  window.addEventListener('scroll', ceremonyButtonScroll);
  window.addEventListener('scroll', partyButtonScroll);
  ceremonyButtonScroll(); // Check initial scroll position
  partyButtonScroll()
});

onUnmounted(() => {
  window.removeEventListener('scroll', ceremonyButtonScroll);
  window.removeEventListener('scroll', partyButtonScroll);
});
</script>

<style scoped lang="scss">
@font-face {
  font-family: 'myfont';
  src: url('../fonts/myfont.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}
.wedding__main{
    color: white;
&--entry{
    text-align: center;
    display: flex;
    width: 100%;
    align-items: center;
    justify-content: center;
    & p{
        font-size: 27px;
        width: 700px;
    font-family: 'myfont';

    }
}
&--date{
    display: flex;
    justify-content: center;
    padding-top: 60px;
    & img{
        width: 760px;
        height: 120px;
        // height: 90px;
    }
}
&--ceremony{
    & img{
        width: 400px;
    }
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-content: center;
    align-items: center;
    text-align: center;
    & .ceremony__info{
            display: flex;
    flex-direction: column;
    align-content: center;
    align-items: center;
    row-gap: 14px;
        &--title{
            width: 320px;
                font-size: 25px;
    color: #a9957d;
    font-weight: 300;
    font-family: 'MontserratARM';
    text-transform: uppercase;
        }
        &--time{
            font-size: 35px;
    color: #a9957d;
    font-weight: 700;
    font-family: 'MontserratARM';
        }
         &--church{
            font-size: 35px;
    color: #a9957d;
    font-weight: 700;
    font-family: 'MontserratARM';
        }
        &--city{
            font-size: 20px;
    color: rgb(243, 237, 230);
    font-family: 'MontserratARM';
        }
    }
}
&--party{
    margin-top: 40px;
    & img{
        width: 400px;
    }
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-content: center;
    align-items: center;
    text-align: center;
    & .party__info{
            display: flex;
    flex-direction: column;
    align-content: center;
    align-items: center;
    row-gap: 14px;
        &--title{
            width: 320px;
                font-size: 25px;
    color: #a9957d;
    font-weight: 300;
    font-family: 'MontserratARM';
    text-transform: uppercase;
        }
        &--time{
            font-size: 35px;
    color: #a9957d;
    font-weight: 700;
    font-family: 'MontserratARM';
        }
         &--place{
            font-size: 35px;
    color: #a9957d;
    font-weight: 700;
    font-family: 'MontserratARM';
        }
        &--city{
            font-size: 20px;
    color: rgb(243, 237, 230);
    font-family: 'MontserratARM';
        }
    }
}
}
.ceremony--action {
  opacity: 0;
  animation: fadeIn 2s forwards, fadeOut 0.5s forwards;
  animation-play-state: paused;
  color: white;
  border: 3px solid #f3ede6;
  background: none;
  border-radius: 50px;
  padding: 0 30px;
  font-size: 20px;
  height: 45px;
  margin-top: 20px;
}

.visible {
  animation-play-state: running;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
 
  100% {
    opacity: 1;
  }
}

@media screen and (min-width: 300px) and (max-width: 600px) {
    
    .wedding__main--date img {
        width: 250px;
        height: 90px;
    }
    .wedding__main{
    color: white;
&--entry{
    text-align: center;
    display: flex;
    width: 100%;
    align-items: center;
    justify-content: center;
    & p{
        font-size: 27px;
        width: auto;
    }
}
}
    
}
</style>
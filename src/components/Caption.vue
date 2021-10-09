<template>
    <div class="wrapper">
        <span class="champions-league" name="champions-league"></span>
        <label for="champions-league">Champions League</label>
        <span class="europe-league" name="europe-league"></span>
        <label for="europe-league"> Europe League</label>
        <span class="relegation" name="relegation"></span>
        <label for="relegation">Relegation</label>
    </div>
</template>

<script>
export default {
  name: 'Caption',
};
</script>

<style lang="scss" scoped>
    .wrapper{
        width: 100%;
        margin: 0;
        text-align: center;
        margin: 20px;
    }
    span, label{
        display: inline-block;
        vertical-align: top;
        text-align: start;
        margin: 20px;
        line-height: 17px;
        height: 15px;
    }
    .champions-league, .europe-league, .relegation{
        width: 15px;
    }
    .champions-league{
        background-color: #77D970;
    }
    .europe-league{
        background-color: #38A3A5;
    }
    .relegation{
        background-color: #D57E7E;
    }
    @media (max-width: 480px) {
       .wrapper{
            margin: 5px;
       }
       span, label{
           margin: 5px;
           height: 7px;
           line-height: 8px;
           font-size: 7px;
       }
        .champions-league, .europe-league, .relegation{
        width: 7px;
    }
    }
</style>

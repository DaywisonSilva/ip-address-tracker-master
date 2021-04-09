<template>
  <div class="card-background__app">
    <div class="card-info__app">
      <div>Ip Address</div>
      <div>{{ ip }}</div>
    </div>
    <div class="card-info__app">
      <div>Location</div>
      <div>{{ location }}</div>
    </div>
    <div class="card-info__app">
      <div>Timezone</div>
      <div>{{ timezone }}</div>
    </div>
    <div class="card-info__app">
      <div>Isp</div>
      <div>{{ isp }}</div>
    </div>
  </div>
</template>

<script>
export default {
    props: ['ip', 'location', 'timezone', 'isp']
};
</script>

<style>
    .card-background__app {
        position: absolute;
        min-height: 130px;
        border-radius: 15px;
        background-color: white;
        padding: 15px 30px;
        box-sizing: border-box;
        top: 70%;
        left: calc(50% - 400px);
        width: 90%;
        max-width: 800px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        box-shadow: 0px 4px 10px #3d3d3d3b;
        z-index: 2;
    }

    .card-info__app {
        width: 25%;
        min-width: 180px;
        margin: 10px 0;
        display: grid;
        place-content: center;
        font-weight: bold;
        text-align: center;
    }

    .card-info__app div:first-child {
        color: #7c7c7c;
        text-transform: uppercase;
        letter-spacing: 2px;
        margin-bottom: 20px;
    }

    .card-info__app div:last-child{
        font-size: 1.2rem;
        color: #464646;
    }

    .card-info__app:nth-child(2) {
        width: calc(25% - 4px);
        border-left: 2px solid rgb(206, 206, 206);
        border-right: 2px solid rgb(206, 206, 206);
    }

    .card-info__app:nth-child(3) {
        width: calc(25% - 2px);
        border-right: 2px solid rgb(206, 206, 206);
    }

    @media screen and (max-width: 860px){
        .card-background__app {
            left: 5%;
        }
    }

    
    @media screen and (max-width: 650px) {
        .card-background__app {
            justify-content: center;
            transform: scale(.6);
            top: 120px;
        }

        .card-info__app {
            border: none !important;
        }
    }

    @media screen and (max-width: 466px) {
        .card-background__app {
            justify-content: center;
            transform: scale(.6);
            top: 80px;
        }
    }

</style>

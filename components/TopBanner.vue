<template>
    <section class="topBanner">
        <div class="container">
            <div class="row">
                <div class="inner">
                    <h1>
                        COVID UK
                    </h1>
                    <p>
                        Use this tool to find out the latest stats for Coronavirus in the UK
                    </p>
                </div>
            </div>
            <div class="row">
                <img :src="require('../assets/images/arrow.svg')" alt="arrow">
            </div>
        </div>
    </section>
</template>
<style lang="scss" scoped>
.topBanner {
    background: url('../assets/images/banner-top.jpg');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    display: flex;
    align-items: center;
    @media only screen and (max-width: 420px) {
        background-position: 70%;
    }
    .inner {
        padding: 210px 0;
        color: white;
        @media only screen and (max-width: 420px) {
            padding: 38vh 0;
        }
    }
    .row:nth-child(2) {
        justify-content: center;
        margin-bottom: 20px;
    }
}
</style>
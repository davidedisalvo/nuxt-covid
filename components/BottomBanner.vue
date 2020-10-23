<template>
    <section class="bottomBanner">
        <div class="container">
            <div class="row">
                <div class="col-4">
                    <h2>
                        WASH HANDS
                    </h2>
                    <p>Keep washing your hands regularly</p>
                </div>
                <div class="col-4">
                    <h2>
                        COVER FACE
                    </h2>
                    <p>Wear a face covering in enclosed spaces</p>
                </div>
                <div class="col-4">
                    <h2>
                        MAKE SPACE
                    </h2>
                    <p>Stay at least 2 metres apart, wear face covering</p>
                </div>
            </div>
        </div>
    </section>
</template>
<style lang="scss" scoped>
    .col-4 {
        width: 30%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        @media only screen and (max-width: 790px) {
            width: 100%;
            margin-bottom: 80px;
        }
        h2 {
            font-size: 36px;
            margin-bottom: 16px;
            font-weight: bold;
        }
        p {
            font-size: 20px;
            text-align: center;
            color: #505050;
            line-height: 23px;
        }
    }
</style>
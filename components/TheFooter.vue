<template>
    <footer>
        <div class="container">
            <div class="row">
                <div class="nameChallenge">
                    <p>An RCCO development challenge by Davide Di Salvo</p>
                    <p>Data source: Gov.uk</p>
                </div>
                <div>
                    <h3>COVID UK</h3>
                </div>
            </div>
        </div>
    </footer>
</template>
<style lang="scss" scoped>
    footer {
        background: #1C4155;
        border-radius: 8px 8px 0px 0px;
        padding: 40px 0;
        color: white;
        h3 {
            font-size: 3rem;
        }
        .row {
            > div {
                display: flex;
                flex-direction: column;
                justify-content: center;
                &:first-of-type {
                    margin-bottom: 20px;
                }
            }
        }
    }
</style>
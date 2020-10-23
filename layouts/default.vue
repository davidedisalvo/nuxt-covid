<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 62.5%;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}
@media (max-width: 1160px) {
  html { font-size: 50%; }
}
@media(max-width: 960px) {
  html { font-size: 45%; }
}
@media (max-width: 790px) {
  html { font-size: 30%; }
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
h1,h2,h3,h4,h5 {
  font-family: 'Roboto Condensed', sans-serif;
}

h1 {
  font-size: 10rem;
  margin-bottom: 10px;
}
h2 {
  font-size: 8rem;

}
h3 {
    font-size: 7rem;
}
h4 {
  font-size: 3rem;
}
p {
  font-size: 2rem;
}
.container {
  margin: 0 auto;
  width: 100%;
}

.row {
  padding: 0 8vw;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  
}
section:not(:first-child) {
  margin-bottom: 150px;
}
section:first-child {
  margin-bottom: 80px;
}


</style>

<template>
  <div>
    <div class="grid-gallery">
      <div class="grid-item">
        <a href="">
            <img src="https://backend.inmobiliaria-delsur.com.ar/archivos/33_0.jpg" alt="">
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    async mounted () {
        await fetch("https://api.github.com/repos/LucasFN1314/ProyectoGaleria/contents/public/images", {
            headers: {
                "Authorization": "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",
            }
        }).then(response => response.json()).then((data) => {
            console.log(data);
            this.images = data;
        });
    },
    data () {
        return {
            images: []
        }
    }
};
</script>

<style lang="scss" scoped>
.grid-gallery {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 50px 20px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  grid-auto-rows: 250px;
  grid-auto-flow: dense;
  grid-gap: 20px;
}

.grid-gallery .grid-item:nth-child(3n-2) {
    grid-column: span 2;
    grid-row: span 2;
}

.grid-gallery .grid-item {
    position: relative;
    background-color: #efefef;
    overflow: hidden;
}

.grid-gallery .grid-item a {
    cursor: zoom-in;
}

.grid-gallery .grid-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform .5s cubic-bezier(.165,.84,.44,1);
}
</style>
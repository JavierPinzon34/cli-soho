<template>
  <div class="item-proyecto" :style="{ backgroundColor: color }">
    <div class="bg-proyecto" :class="`${ imagePosition ==1 ? 'fondo-d' : 'fondo-i' }`" :style="{ backgroundImage: 'url(' + require(`@/assets/img/proyecto/${code}-image.jpg`) + ')' }">
      <b-row>
        <b-col :offset="`${imagePosition == 1 ? 'lg-6' : ''}`" lg="6" class="contenido-proyecto" :class="`${ theme == 1 ? 'theme-1' : 'theme-2' }`">
          <img :src="require(`@/assets/img/proyecto/${code}-logo.png`)" alt="">
          <div class="underline"></div>
          <h1> {{ name }}</h1>
          <p> {{ description }} </p>
          <div class="tag-links" />
          <a v-for="(tag, index) in tags" :key="index" href="">{{ tag }}</a>
          <button type="button" class="btn btn-success d-flex mt-4" :style="{ color: color }">
              VER DETALLES
            </button>
        </b-col>
      </b-row>
      </div>
  </div>
</template>
<script>
export default {
  props: {
    color: {
      type: String,
      default: 'White'
    },
    code: {
      type: String,
      default: ''
    },
    imagePosition: {
      type: Number,
      default: true
    },
    name: {
      type: String,
      default: ''
    },
    description: {
      type: String,
      default: ''
    },
    tags: {
      type: Array,
      default: []
    },
    theme: {
      type: Number,
      default: 0
    }
  }
}
</script>
<style lang="scss">
  .item-proyecto {
    font-family: 'Graphik', sans-serif;
    .bg-proyecto {
      width: 100%;
      height: 100%;
      background-size: contain;
      background-repeat: no-repeat;
      transition: .5s;
      padding: 0;
      img {
        width: auto;
        height: 60px;
        margin-bottom: 10px;
      }
      .contenido-proyecto {
        padding: 100px;
        .underline {
          width: 80px;
          height: 3px;
          margin-bottom: 30px;
          bottom: 0;
          left: calc(50% - 40px);
        }
        .tag-links {
          display: inline-flex;
          position: relative;
          width: 20px;
          height: 21px;
          top: 5px;
          background-repeat: no-repeat;
          background-position: bottom;
        }
        button {
          width: 120px;
          text-align: center;
          padding-left: 20px;
          padding-top: 10px;
          height: 40px;
          border: unset;
          font-weight: 600;
          font-size: 13px;
        }
        @media (max-width: 1199.98px) {
          padding: 20px 20px 300px 20px;
        }
      }
      a {
        margin-left: 10px;
        margin-right: 10px;
        text-decoration: underline;
      }
      .theme-1 {
        .tag-links {
          background-image: url('../../assets/img/tag-dark.svg');
        }
        .underline {
          background-color: #ee2e24;
        }
        h1, p, a {
          color: black;
        }
        button {
          background-color: #ee2e24;
          &:active {
            background-color: #b3453f;
          }
          &:focus {
            box-shadow: unset;
          }
        }
      }
      .theme-2 {
        .tag-links {
          background-image: url('../../assets/img//tag-light.svg');
        }
        .underline {
          background-color: white;
        }
        h1, p, a {
          color: white;
        }
        button {
          background-color: white;
          &:active {
            background-color: #e2dfdf;
          }
          &:focus {
            box-shadow: unset;
          }
        }
      }
    }
    .fondo-i {
      background-position: 100%;
    }
    .fondo-d {
      background-position: 0;
    }
    @media (max-width:  991.98px) {
      .fondo-i {
      background-position: bottom;
      }
      .fondo-d {
        background-position: bottom;
      }
    }
  }
</style>

<template>
<div class="page-container">
  <div class="panel-container">
    <header class="panel-header">
      <div class="search-input" :style="{width: textWidth + 'px'}">
        <span class="input-text" ref="inputspan">{{ text }}</span>
        <span class="ellipsis" v-if="isShowEllipsis">......</span>
      </div>
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 52.966 52.966" width="14" height="14" fill="#fff">
        <path d="M51.704 51.273L36.844 35.82c3.79-3.8 6.14-9.04 6.14-14.82 0-11.58-9.42-21-21-21s-21 9.42-21 21 9.42 21 21 21c5.082 0 9.747-1.817 13.383-4.832l14.895 15.49c.196.206.458.308.72.308.25 0 .5-.093.694-.28.398-.382.41-1.015.028-1.413zM21.984 40c-10.478 0-19-8.523-19-19s8.522-19 19-19 19 8.523 19 19-8.525 19-19 19z"/>
      </svg>
      <div class="placeholder"></div>
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 612 612" width="16" height="16" opacity="0.85">
        <path fill="#6BBC57" d="M577.557 184.258C560.417 140.85 519.54 59.214 519.54 59.214l.003-.01s-82.64 38.422-123.102 61.674c-30.27 17.396-41.46 48.877-44.22 56.743-3.22 9.23-12.33 51.19 6.12 90.86 23.93 51.44 50.86 106.04 50.86 106.04v.01s55.31-25.83 106.09-51.13c39.16-19.51 58.3-57.96 61.53-67.18 2.75-7.865 13.577-39.475.753-71.95z"/>
        <path fill="#BDE9B7" d="M501.052 102.162l6.466 2.263L426.69 335.38l-6.466-2.263z"/>
        <circle cx="299.756" cy="198.246" r="178.613" fill="#FFB30D"/>
        <circle cx="299.756" cy="198.246" r="155.24" fill="#FCE29C"/>
        <path fill="#FCC329" d="M299.756 189.873l41.513-76.398c7.9-30.932-16.92-54.887-41.52-55.584-24.6-.69-51.52 24.89-43.26 55.59l43.26 76.4zm7.27 4.884h86.948c30.954-7.674 40.15-41.076 29.02-63.02-11.13-21.942-46.46-33.38-69.494-11.467l-46.475 74.487zm1.764 8.687l46.095 73.724c23.04 22.1 56.11 12.27 68.816-8.8 12.71-21.07 3.68-57.092-27.11-65.006l-87.79.08zm-8.582 3.174l-40.58 76.898c-7.53 31.027 17.586 54.677 42.187 55.075 24.6.4 51.207-25.51 42.577-56.1l-44.184-75.86zm-8.15-3.318l-86.95.115c-30.945 7.862-40.094 41.125-28.936 63.053 11.158 21.928 49.88 34.073 72.884 12.13l43-75.297zm.407-8.47l-45.968-73.806c-23.003-22.14-56.088-12.366-68.83 8.682-12.742 21.047-3.774 57.085 27.002 65.05l87.79.073z"/>
        <path fill="#A63131" d="M71.014 337.344c76.277 85.25 207.22 92.522 292.468 16.245L87.258 44.87C2.01 121.15-5.262 252.092 71.014 337.342z"/>
        <path fill="#BC5757" d="M101.447 310.115c61.238 68.44 166.364 74.278 234.804 13.04L114.49 75.31c-68.443 61.24-74.28 166.364-13.043 234.805z"/>
        <path fill="#F1D4AF" d="M186.412 237.54l-34.753 7.904c-11.67 5.94-12.32 20.066-5.88 27.826 6.44 7.758 21.6 9.12 28.82-1.732l11.8-33.998zm55.65 32.292l-18.696 30.343c-3.927 12.483 5.7 22.843 15.75 23.675 10.052.835 21.64-9.035 18.945-21.785l-16-32.233zm-81.86-91.515l-29.845-19.48c-12.377-4.252-22.982 5.102-24.08 15.128-1.094 10.025 8.47 21.868 21.286 19.506l32.64-15.15z"/>
        <path fill="#2D97B7" d="M30.857 311.46c0 118.41 74.514 219.34 179.01 258.06v19.68h191.12v-20.3c102.608-38.786 175.9-137.698 177.323-253.993l10.886-18.937H22.804l8.063 14.028c-.002.49-.01.973-.01 1.46z"/>
        <path fill="#FFF" d="M540.565 321.42c.02 1.167.03 2.335.03 3.507 0 81.014-43.082 151.957-107.58 191.195l4.163 7.195c66.974-40.677 111.717-114.308 111.717-198.39 0-1.172-.01-2.34-.03-3.508zm-140.68 211.26c-11.587 4.63-23.648 8.322-36.092 10.974v.796l1.178 7.443c13.51-2.844 26.58-6.875 39.11-11.958z"/>
      </svg>
      <div class="brand">
        <div class="brand-saladict">Saladict</div>
      </div>
    </header>
    <div class="dicts">
      <section class="dict-item" v-for="id in selected">
        <header class="dict-item-header">
          <img class="dict-item-logo" :src="dicts[id].favicon">
          <h1 class="dict-item-name">{{ dicts[id].name }}</h1>
        </header>
        <div ref="dict" class="dict-item-body">
          <component :is="id" :result="dicts[id].result"></component>
        </div>
      </section>
    </div>
  </div>
  <transition name="fade">
    <img v-if="imgsrc" class="panel-img" :src="imgsrc" @click="downloadImg" alt="panel image">
    <div v-else class="panel-mask">
      <loader :width="150" :height="150" fill="#fff"></loader>
    </div>
  </transition>
</div>
</template>

<script>
import html2canvas from 'html2canvas'
import Loader from 'src/components/Loader'
import defaultConfig from 'src/app-config'
import {storage} from 'src/helpers/chrome-api'

export default {
  name: 'share-img',
  data () {
    let dicts = Object.keys(defaultConfig.dicts.all).reduce((dicts, id) => {
      dicts[id] = {
        result: null,
        favicon: chrome.runtime.getURL(`assets/dicts/${id}.png`),
        name: chrome.i18n.getMessage('dict_' + id) || id
      }
      return dicts
    }, {})

    return {
      imgsrc: '',
      text: '',
      textWidth: 84,
      isShowEllipsis: false, // html2canvas doesn't support text overflow: ellipsis
      selected: [],
      dicts
    }
  },
  methods: {
    downloadImg () {
      var a = document.createElement('a')
      a.href = this.imgsrc
      a.download = `${this.text}-Saladict`
      a.click()
    }
  },
  mounted () {
    storage.local.get('paneldata')
      .then(({paneldata}) => {
        return new Promise((resolve, reject) => {
          this.text = paneldata.text
          paneldata.dicts.forEach(dict => {
            this.selected.push(dict.id)
            this.dicts[dict.id].result = dict.result
            if (dict.id === 'dictcn') {
              dict.result.animate = false
            }
          })

          this.$nextTick(() => {
            // get text width
            let textWidth = this.$refs.inputspan.getBoundingClientRect().width
            console.log(textWidth)
            if (textWidth > this.textWidth) {
              if (textWidth <= 270) {
                this.textWidth = textWidth
              } else {
                this.textWidth = 270
                this.isShowEllipsis = true
              }
            }
          })
          setTimeout(resolve, 1500)
        })
      })
      .then(() => {
        html2canvas(document.querySelector('.panel-container')).then(canvas => {
          if (canvas) {
            this.imgsrc = canvas.toDataURL('image/png')
          } else {
            console.error('dom to canvas faild')
          }
        })
      })
  },
  components: (() => {
    // Dynamically & asynchronously loads components
    const components = {Loader}
    Object.keys(defaultConfig.dicts.all).forEach(id => {
      components[id] = () => Promise.resolve(require('src/dictionaries/' + id + '/view.vue'))
    })
    return components
  })()
}
</script>

<style src="normalize.css/normalize.css"></style>

<style lang="scss">
*, *:before, *:after {
  box-sizing: inherit;
}

html {
  box-sizing: border-box;
}

body {
  font-size: 14px;
  // font-family: "Helvetica Neue", Helvetica, Arial, "Hiragino Sans GB", "Hiragino Sans GB W3", "Microsoft YaHei UI", "Microsoft YaHei", "WenQuanYi Micro Hei", sans-serif;
  background: #f7f7f7;
}

.page-container {
  position: relative;
  width: 400px;
  margin: auto;
}

.panel-mask {
  display: flex;
  justify-content: center;
  position: absolute;
  z-index: 9999;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  padding-top: 10%;
  background: rgba(0, 0, 0, 0.7);
}

.panel-img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  cursor: pointer;
}

.panel-container {
  display: flex;
  position: relative;
  flex-direction: column;
  background: #fff;
}

.panel-header {
  display: flex;
  align-items: center;
  height: 30px;
  padding-left: 6px;
  background-color: rgb(92, 175, 158);
}

.hidden-input {
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
  padding: 0 5px;
}

.search-input {
  position: relative;
  width: 6em;
  height: 18px;
  margin-right: 8px;
  padding: 0 5px;
  color: #fff;
  overflow: hidden;
  background-color: rgba(225, 225, 225, 0.1);
  transition: all 0.4s;
}

.input-text {
  position: absolute;
  z-index: 1;
  top: 0;
  left: 0;
  padding: 0 5px;
  white-space: nowrap;
}

.ellipsis {
  position: absolute;
  z-index: 2;
  top: 0;
  right: 0;
  padding-right: 5px;
  background-color: #6ab4a5;
}

.placeholder {
  flex: 1;
}

.brand {
  color: rgba(255, 255, 255, 0.6);
  margin: 0 6px 0 2px;
}

.brand-saladict {
  text-align: center;
}

.dicts {
  flex: 1;
  padding: 0 10px;
  border: 1px solid #eee;
  border-top: none;
}

.dict-item {
  position: relative;
}

.dict-item-header {
  display: flex;
  align-items: center;
  border-top: 1px #ddd solid;
}

.dict-item:first-child .dict-item-header {
  border: none;
}

.dict-item-logo {
  align-self: flex-start;
  width: 19px;
  height: 19px;
  margin-top: -1px;
}

.dict-item-name {
  margin: 0;
  padding: 3px;
  font-size: 12px;
  font-weight: normal;
  color: #444;
  cursor: pointer;
}

.dict-item-body {
  overflow: hidden;
  margin-bottom: 10px;
  font-size: 12px;
  line-height: 1.6;
  color: #333;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s
}
.fade-enter, .fade-leave-active {
  opacity: 0
}
</style>
